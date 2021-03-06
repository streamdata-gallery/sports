---
swagger: "2.0"
x-collection-name: Strava
x-complete: 0
info:
  title: Strava Get Upload
  description: Returns an upload for a given identifier.
  version: 1.0.0
host: www.strava.com
basePath: /api/v3
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /athletes/{id}/stats:
    get:
      summary: Get Athlete Stats
      description: Returns the activity stats of an athlete.
      operationId: getStats
      x-api-path-slug: athletesidstats-get
      parameters:
      - in: path
        name: id
        description: The identifier of the athlete
      - in: query
        name: No Name
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - Athlete
      - Stats
  /athlete:
    get:
      summary: Get Authenticated Athlete
      description: Returns the currently authenticated athlete.
      operationId: getLoggedInAthlete
      x-api-path-slug: athlete-get
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - Authenticated
      - Athlete
    put:
      summary: Update Athlete
      description: Update the currently authenticated athlete.
      operationId: updateLoggedInAthlete
      x-api-path-slug: athlete-put
      parameters:
      - in: body
        name: body
        description: The athlete entity to update
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - Athlete
  /athlete/zones:
    get:
      summary: Get Zones
      description: Returns the the authenticated athlete's heart rate and power zones.
      operationId: getLoggedInAthleteZones
      x-api-path-slug: athletezones-get
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - Zones
  /segments/{id}:
    get:
      summary: Get Segment
      description: Returns the specified segment.
      operationId: getSegmentById
      x-api-path-slug: segmentsid-get
      parameters:
      - in: path
        name: id
        description: The identifier of the segment
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - Segment
  /segments/starred:
    get:
      summary: List Starred Segments
      description: List of the authenticated athlete's starred segments.
      operationId: getLoggedInAthleteStarredSegments
      x-api-path-slug: segmentsstarred-get
      parameters:
      - in: query
        name: No Name
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - List
      - Starred
      - Segments
  /segments/{id}/starred:
    put:
      summary: Star Segment
      description: Stars/Unstars the given segment for the authenticated athlete.
      operationId: starSegment
      x-api-path-slug: segmentsidstarred-put
      parameters:
      - in: path
        name: id
        description: The identifier of the segment to star
      - in: formData
        name: starred
        description: If true, star the segment; if false, unstar the segment
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - Star
      - Segment
  /segments/{id}/leaderboard:
    get:
      summary: Get Segment Leaderboard
      description: Returns the specified segment leaderboard.
      operationId: getLeaderboardBySegmentId
      x-api-path-slug: segmentsidleaderboard-get
      parameters:
      - in: query
        name: age_group
        description: Premium Feature
      - in: query
        name: club_id
        description: Filter by club
      - in: query
        name: context_entries
      - in: query
        name: date_range
        description: Filter by date range
      - in: query
        name: following
        description: Filter by friends of the authenticated athlete
      - in: query
        name: gender
        description: Filter by gender
      - in: path
        name: id
        description: The identifier of the segment leaderboard
      - in: query
        name: No Name
      - in: query
        name: weight_class
        description: Premium Feature
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - Segment
      - Leaderboard
  /segments/{id}/all_efforts:
    get:
      summary: List Segment Efforts
      description: Returns a set of the authenticated athlete's segment efforts for
        a given segment.
      operationId: getEffortsBySegmentId
      x-api-path-slug: segmentsidall-efforts-get
      parameters:
      - in: path
        name: id
        description: The identifier of the segment
      - in: query
        name: No Name
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - List
      - Segment
      - Efforts
  /segments/explore:
    get:
      summary: Explore segments
      description: Returns the top 10 segments matching a specified query.
      operationId: exploreSegments
      x-api-path-slug: segmentsexplore-get
      parameters:
      - in: query
        name: activity_type
        description: Desired activity type
      - in: query
        name: bounds
        description: 'The latitude and longitude for two points describing a rectangular
          boundary for the search: [southwest corner latitutde, southwest corner longitude,
          northeast corner latitude, northeast corner longitude]'
      - in: query
        name: max_cat
        description: The maximum climbing category
      - in: query
        name: min_cat
        description: The minimum climbing category
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - Explore
      - Segments
  /segment_efforts/{id}:
    get:
      summary: Get Segment Effort
      description: Returns a segment effort from an activity that is owned by the
        authenticated athlete.
      operationId: getSegmentEffortById
      x-api-path-slug: segment-effortsid-get
      parameters:
      - in: path
        name: id
        description: The identifier of the segment effort
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - Segment
      - Effort
  /running_races/{id}:
    get:
      summary: Get Running Race
      description: Returns a running race for a given identifier.
      operationId: getRunningRaceById
      x-api-path-slug: running-racesid-get
      parameters:
      - in: path
        name: id
        description: The identifier of the running race
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - Running
      - Race
  /running_races:
    get:
      summary: List Running Races
      description: Returns a list running races based on a set of search criteria.
      operationId: getRunningRaces
      x-api-path-slug: running-races-get
      parameters:
      - in: query
        name: year
        description: Filters the list by a given year
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - List
      - Running
      - Races
  /activities:
    post:
      summary: Create an Activity
      description: Creates a manual activity for an athlete. Requires write permissions,
        as requested during the authorization process.
      operationId: createActivity
      x-api-path-slug: activities-post
      parameters:
      - in: formData
        name: commute
        description: Set to 1 to mark as commute
      - in: formData
        name: description
        description: Description of the activity
      - in: formData
        name: distance
        description: In meters
      - in: formData
        name: elapsed_time
        description: In seconds
      - in: formData
        name: name
        description: The name of the activity
      - in: formData
        name: photo_ids
        description: List of native photo ids to attach to the activity
      - in: formData
        name: private
        description: set to 1 to mark the resulting activity as private, ???view_private???
          permissions will be necessary to view the activity
      - in: formData
        name: start_date_local
        description: ISO 8601 formatted date time
      - in: formData
        name: trainer
        description: Set to 1 to mark as a trainer activity
      - in: formData
        name: type
        description: Type of activity
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - Activity
  /activities/{id}:
    get:
      summary: Get Activity
      description: Returns the given activity that is owned by the authenticated athlete.
      operationId: getActivityById
      x-api-path-slug: activitiesid-get
      parameters:
      - in: path
        name: id
        description: The identifier of the activity
      - in: query
        name: include_all_efforts
        description: To include all segments efforts
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - Activity
    put:
      summary: Update Activity
      description: Updates the given activity that is owned by the authenticated athlete.
      operationId: updateActivityById
      x-api-path-slug: activitiesid-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: id
        description: The identifier of the activity
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - Activity
  /athlete/activities:
    get:
      summary: List Athlete Activities
      description: Returns the activities of an athlete for a specific identifier.
      operationId: getLoggedInAthleteActivities
      x-api-path-slug: athleteactivities-get
      parameters:
      - in: query
        name: after
        description: An epoch timestamp to use for filtering activities that have
          taken place after a certain time
      - in: query
        name: before
        description: An epoch timestamp to use for filtering activities that have
          taken place before a certain time
      - in: query
        name: No Name
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - List
      - Athlete
      - Activities
  /activities/{id}/laps:
    get:
      summary: List Activity Laps
      description: Returns the laps of an activity identified by an identifier.
      operationId: getLapsByActivityId
      x-api-path-slug: activitiesidlaps-get
      parameters:
      - in: path
        name: id
        description: The identifier of the activity
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - List
      - Activity
      - Laps
  /activities/{id}/zones:
    get:
      summary: Get Activity Zones
      description: Premium Feature. Returns the zones of a given activity.
      operationId: getZonesByActivityId
      x-api-path-slug: activitiesidzones-get
      parameters:
      - in: path
        name: id
        description: The identifier of the activity
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - Activity
      - Zones
  /activities/{id}/comments:
    get:
      summary: List Activity Comments
      description: Returns the comments on the given activity.
      operationId: getCommentsByActivityId
      x-api-path-slug: activitiesidcomments-get
      parameters:
      - in: path
        name: id
        description: The identifier of the activity
      - in: query
        name: No Name
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - List
      - Activity
      - Comments
  /activities/{id}/kudos:
    get:
      summary: List Activity Kudoers
      description: Returns the athletes who kudoed an activity identified by an identifier.
      operationId: getKudoersByActivityId
      x-api-path-slug: activitiesidkudos-get
      parameters:
      - in: path
        name: id
        description: The identifier of the activity
      - in: query
        name: No Name
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - List
      - Activity
      - Kudoers
  /clubs/{id}:
    get:
      summary: Get Club
      description: Returns a given club using its identifier.
      operationId: getClubById
      x-api-path-slug: clubsid-get
      parameters:
      - in: path
        name: id
        description: The identifier of the club
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - Club
  /clubs/{id}/members:
    get:
      summary: List Club Members
      description: Returns a list of the athletes who are members of a given club.
      operationId: getClubMembersById
      x-api-path-slug: clubsidmembers-get
      parameters:
      - in: path
        name: id
        description: The identifier of the club
      - in: query
        name: No Name
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - List
      - Club
      - Members
  /clubs/{id}/admins:
    get:
      summary: List Club Administrators.
      description: Returns a list of the administrators of a given club.
      operationId: getClubAdminsById
      x-api-path-slug: clubsidadmins-get
      parameters:
      - in: path
        name: id
        description: The identifier of the club
      - in: query
        name: No Name
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - List
      - Club
      - Administrators
  /clubs/{id}/activities:
    get:
      summary: List Club Activities
      description: Retrieve recent activities from members of a specific club. The
        authenticated athlete must belong to the requested club in order to hit this
        endpoint. Pagination is supported. Enhanced Privacy Mode is respected for
        all activities.
      operationId: getClubActivitiesById
      x-api-path-slug: clubsidactivities-get
      parameters:
      - in: path
        name: id
        description: The identifier of the club
      - in: query
        name: No Name
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - List
      - Club
      - Activities
  /clubs/{id}/join:
    post:
      summary: Join Club
      description: Adds the authenticated athlete to the club's membership.
      operationId: joinClubById
      x-api-path-slug: clubsidjoin-post
      parameters:
      - in: path
        name: id
        description: The identifier of the club
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - Join
      - Club
  /clubs/{id}/leave:
    post:
      summary: Leave Club
      description: Removes the authenticated athlete from the club's membership.
      operationId: leaveClubById
      x-api-path-slug: clubsidleave-post
      parameters:
      - in: path
        name: id
        description: The identifier of the club
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - Leave
      - Club
  /athlete/clubs:
    get:
      summary: List Athlete Clubs
      description: Returns a list of the clubs whose membership includes the authenticated
        athlete.
      operationId: getLoggedInAthleteClubs
      x-api-path-slug: athleteclubs-get
      parameters:
      - in: query
        name: No Name
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - List
      - Athlete
      - Clubs
  /gear/{id}:
    get:
      summary: Get Equipment
      description: Returns an equipment using its identifier.
      operationId: getGearById
      x-api-path-slug: gearid-get
      parameters:
      - in: path
        name: id
        description: The identifier of the gear
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - Equipment
  /routes/{id}:
    get:
      summary: Get Route
      description: Returns a route using its identifier.
      operationId: getRouteById
      x-api-path-slug: routesid-get
      parameters:
      - in: path
        name: id
        description: The identifier of the route
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - Route
  /athletes/{id}/routes:
    get:
      summary: List Athlete Routes
      description: Returns a list of the routes created by the authenticated athlete
        using their athlete ID.
      operationId: getRoutesByAthleteId
      x-api-path-slug: athletesidroutes-get
      parameters:
      - in: path
        name: id
        description: The identifier of the athlete
      - in: query
        name: No Name
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - List
      - Athlete
      - Routes
  /uploads:
    post:
      summary: Upload Activity
      description: Uploads a new data file to create an activity from.
      operationId: createUpload
      x-api-path-slug: uploads-post
      parameters:
      - in: formData
        name: commute
        description: Whether the resulting activity should be tagged as a commute
      - in: formData
        name: data_type
        description: The format of the uploaded file
      - in: formData
        name: description
        description: The desired description of the resulting activity
      - in: formData
        name: external_id
        description: The desired external identifier of the resulting activity
      - in: formData
        name: file
        description: The uploaded file
      - in: formData
        name: name
        description: The desired name of the resulting activity
      - in: formData
        name: private
        description: Whether the resulting activity should be private
      - in: formData
        name: trainer
        description: Whether the resulting activity should be marked as having been
          performed on a trainer
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - Upload
      - Activity
  /uploads/{uploadId}:
    get:
      summary: Get Upload
      description: Returns an upload for a given identifier.
      operationId: getUploadById
      x-api-path-slug: uploadsuploadid-get
      parameters:
      - in: path
        name: uploadId
        description: The identifier of the upload
      responses:
        200:
          description: Successful response
      tags:
      - Sports
      - Upload
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---