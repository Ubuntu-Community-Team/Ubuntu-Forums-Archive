---
title: "Myth Transcode DaemonWont Start"
date: 2008-07-31
forum: General Help
---

### Post by kempy1000 on 2008-07-31
Hello, 
I am trying to get the myth transcoding daemon working but i have a small problem.
Evrytime i try to start with the command:
```

mtd -d

```
I get this error:
```

chris@chimera:~$ mtd -d

2008-08-01 01:00:58.406 Using runtime prefix = /usr, libdir = /usr/lib
chris@chimera:~$ 2008-08-01 01:00:58.489 Empty LocalHostName.
2008-08-01 01:00:58.489 Using localhost value of chimera
2008-08-01 01:00:58.531 New DB connection, total: 1
2008-08-01 01:00:58.559 Connected to database 'mythconverg' at host: localhost
2008-08-01 01:00:58.561 Closing DB connection named 'DBManager0'
2008-08-01 01:00:58.562 Connected to database 'mythconverg' at host: localhost
QServerSocket: failed to bind or listen to the socket
2008-08-01 01:00:58.579 MTDServerSocket Something is wrong trying to start with port=2442
You've probably got another copy of mtd already running.
You might want to try "ps ax | grep mtd".
This copy will now exit ...

```

The output from
```

ps ax | grep mtd

```
Gives:
```

chris@chimera:~$ ps ax | grep mtd
 7157 ?        SNsl   0:00 /usr/bin/mtd -d
 7424 pts/1    S+     0:00 grep mtd

```

But mythtv says cannot connect to myth Transcoding Daemon???

Thanks
Chris

---

### Post by jelofson on 2008-08-26
Can you confirm in your mythtv settings that the ports match? Under the mythfrontend setup there should be a section related to your rip settings. Make sure the port is set up properly (matches what you listed above 2442). Also, you can try looking at your transcoding log. It should be somewhere like /var/lib/mythdvd/temp/mtd.log or it might be up one level.

---

