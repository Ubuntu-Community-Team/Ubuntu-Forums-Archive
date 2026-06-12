---
title: "no mythtv database after upgrade"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by johnapeterson on 2009-06-05
Hello all,

After upgrading to 9.04, I am having a problem getting program schedules thru mythfilldatabase (the are all listed as unknown).  When is runs a portion of the code says this:

2009-06-05 00:41:44.569 DataDirect: Your subscription expires on 11/30/2009 08:30:55 AM
2009-06-05 00:41:53.390 Grab complete.  Actual data from Sat Jun 13 05:00:00 2009 to Sun Jun 14 05:00:00 2009 (UTC)
2009-06-05 00:41:53.391 Main temp tables populated.
2009-06-05 00:41:53.528 Clearing data for source.
2009-06-05 00:41:53.528 Clearing from Sat Jun 13 00:00:00 2009 to Sun Jun 14 00:00:00 2009 (localtime)
2009-06-05 00:41:54.214 Data for source cleared.
2009-06-05 00:41:54.214 Updating programs.
2009-06-05 00:41:54.215 DB Error (Inserting into program table):
Query was:
INSERT IGNORE INTO program (chanid, starttime, endtime, title, subtitle, description, showtype, category, category_type, airdate, stars, previouslyshown, stereo, subtitled, subtitletypes, videoprop, audioprop, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, programid) SELECT dd_v_program.chanid, DATE_ADD(starttime, INTERVAL channel.tmoffset MINUTE), DATE_ADD(endtime, INTERVAL channel.tmoffset MINUTE), title, subtitle, description, showtype, dd_genre.class, category_type, airdate, stars, previouslyshown, stereo, subtitled, (subtitled << 1 ) | closecaptioned, hdtv, stereo, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, dd_v_program.programid FROM (dd_v_program, channel) LEFT JOIN dd_genre ON (dd_v_program.programid = dd_genre.programid AND dd_genre.relevance = '0') WHERE dd_v_program.chanid = channel.chanid;
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/program' is marked as crashed and last (automatic?) repair failed

2009-06-05 00:41:56.779 Program table update complete.
2009-06-05 00:41:56.779 
2009-06-05 00:41:56.779 Checking day @ offset 9, date: Sun Jun 14 2009
2009-06-05 00:41:56.779 Data Refresh needed because of user request
2009-06-05 00:41:56.779 Refreshing data for Sun Jun 14 2009
2009-06-05 00:41:56.786 Retrieving datadirect data.
2009-06-05 00:41:56.787 Grabbing data for Fri Jun 5 2009 offset 9
2009-06-05 00:41:56.787 From Sun Jun 14 05:00:00 2009 to Mon Jun 15 05:00:00 2009 (UTC)
2009-06-05 00:41:56.787 Grabbing listing data
--2009-06-05 00:41:56--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]
Saving to: `STDOUT'


The particular part I was wondering about was the Database error was:
Table ´./mythconverg/program´ is marked as crashed and last (automatic?) repair failed

Does anyone have a suggestion on what I need to do?

Thanks alot.

---

