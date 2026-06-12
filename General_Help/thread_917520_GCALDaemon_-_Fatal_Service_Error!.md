---
title: "GCALDaemon - Fatal Service Error!"
date: 2008-09-12
forum: General Help
---

### Post by Kevanx on 2008-09-12
I've looked high and low with no solution to this problem.

I've installed GCALDaemon (way easier than the syncml/funambol setup!), and it works fine writing FROM evolution TO google calendar, but not the other way. Furthermore, when I run standalone-start.sh or sync-now.sh, this is what the output is:
```

INFO  | GCALDaemon V1.0 beta 16 starting...
INFO  | RSS/ATOM feed converter enabled.
INFO  | Local time zone is Eastern Standard Time.
INFO  | Start listening file /home/kevan/.evolution/calendar/local/system/calendar.ics...
INFO  | File listener started successfully.
INFO  | Offline file synchronization enabled.
FATAL | Fatal service error!
java.lang.ArrayIndexOutOfBoundsException
	at java.lang.String.getChars(String.java:862)
	at org.gcaldaemon.logger.QuickWriter.write(QuickWriter.java:150)
	at org.gcaldaemon.core.file.OnlineFileListener.removeTimestamps(OnlineFileListener.java:371)
	at org.gcaldaemon.core.file.OnlineFileListener.isEquals(OnlineFileListener.java:340)
	at org.gcaldaemon.core.file.OfflineFileListener.run(OfflineFileListener.java:78)
INFO  | Synchronization finished.

```

I've double-checked that the GCALDaemon folder is set to 777, and that all of the scripts are set to 755, Java is 1.6.
I'm fairly certain that I set everything up correctly in the gcal-daemon.cfg file.

I'm 64-bit, if that helps, but other 64-bit users have had no problems.

Any help would be appreciated.

-------------------
EDIT: Inexplicably, it works fine now. I rebooted, and I also changed ```
progress.enabled=false
``` to true. Neither of those should have made a difference, but whatever. No complaints!

---

