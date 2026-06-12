---
title: "Ubuntu Edgy - Mythtv &amp; ivtv issue??"
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by tiger.woods on 2007-01-20
Ubuntu rocks!!! easiest install I've experienced yet with Myth.... where has ubuntu been... or should I say where have I been.

Compiling and install went perfectly but I'm seeing an odd message maybe someone could shed some light on??  Channel(/dev/video0): SetInputAndFormat() failed

I'm pretty sure it's ivtv related and am thinking it has to do with not setting the capture card settings through 'v4l2-ctl' anyone have any experience with this or the process needed to get a PVR250 working with ubuntu and Myth?


mythtv@myth2:~/mythtv$ mythbackend
2007-01-19 22:15:23.201 Using runtime prefix = /usr/local
2007-01-19 22:15:23.275 New DB connection, total: 1
2007-01-19 22:15:23.320 Connected to database 'mythconverg' at host:
192.168.1.111
2007-01-19 22:15:23.328 Current Schema Version: 1175
Running as a slave backend.
2007-01-19 22:15:23.340 New DB connection, total: 2
2007-01-19 22:15:23.380 Connected to database 'mythconverg' at host:
192.168.1.111
2007-01-19 22:15:23.382 mythbackend: MythBackend started as a slave backend
2007-01-19 22:15:23.387 EITHelper: localtime offset -5:00:00
2007-01-19 22:15:23.396 New DB connection, total: 3
2007-01-19 22:15:23.439 Connected to database 'mythconverg' at host:
192.168.1.111
2007-01-19 22:15:23.516 Channel(/dev/video1): SetInputAndFormat() failed
2007-01-19 22:15:23.517 Channel(/dev/video1): SetInputAndFormat() failed
2007-01-19 22:15:23.517 TVRec(5) Error: Setting start channel '6' failed,
                       and backup '2' failed as well.
2007-01-19 22:15:23.530 EITHelper: localtime offset -5:00:00
2007-01-19 22:15:23.600 Channel(/dev/video0): SetInputAndFormat() failed
2007-01-19 22:15:23.601 Channel(/dev/video0): SetInputAndFormat() failed
2007-01-19 22:15:23.601 TVRec(6) Error: Setting start channel '44' failed,
                       and backup '2' failed as well.
2007-01-19 22:15:23.603 Main::Starting HttpServer
2007-01-19 22:15:23.611 Main::Registering HttpStatus Extension
2007-01-19 22:15:23.613 mythbackend version: 0.20.20070111-1 [www.mythtv.org](www.mythtv.org)
2007-01-19 22:15:23.613 Enabled verbose msgs:  important general
2007-01-19 22:15:24.627 Connecting to master server: 192.168.1.111:6543
2007-01-19 22:15:24.629 Connected successfully
2007-01-19 22:15:30.664 MythSocket(823cfb0:10): writeStringList:
Error, invalid string list.
2007-01-19 22:15:33.400 mythbackend: Running housekeeping thread

---

### Post by tiger.woods on 2007-01-21
Answering my own post...

It appears to have been related to the recording directory since it didn't exist. After creating the directory the error disappeared.

---

