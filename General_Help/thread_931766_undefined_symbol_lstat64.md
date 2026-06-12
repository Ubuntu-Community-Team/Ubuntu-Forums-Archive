---
title: "undefined symbol: lstat64"
date: 2008-09-27
forum: General Help
---

### Post by jorbuntu on 2008-09-27
I'm trying to connect to my mythtv backend server. From another ubuntu 8.04 pc, this works fine. From my own (upgraded from 7.10 to 8.04) environment it doesn't work. When I try to connect to the following error occurs: **mythfrontend: symbol lookup error: mythfrontend: undefined symbol: lstat64 **

I don't think is a mythtv problem, but some bug in lstat64. After googling for some time, I see the same issue but for different programs. 

[B]How can I determine what makes lstat64 trip? Does anyone has a solution or suggestion?
[/B]

**Details**
jorbuntu@xps:~$ mythfrontend
2008-09-27 22:43:01.777 Using runtime prefix = /usr
2008-09-27 22:43:02.505 XScreenSaver support enabled
2008-09-27 22:43:02.505 DPMS is active.
2008-09-27 22:43:02.506 Empty LocalHostName.
2008-09-27 22:43:02.506 Using localhost value of xps
2008-09-27 22:43:02.507 Testing network connectivity to 192.168.2.101
2008-09-27 22:43:02.528 New DB connection, total: 1
2008-09-27 22:43:02.535 Connected to database 'mythconverg' at host: 192.168.2.101
2008-09-27 22:43:02.537 Closing DB connection named 'DBManager0'
2008-09-27 22:43:02.554 Total desktop dim: 1680x1050, over 2 screen[s].
2008-09-27 22:43:02.554 Screen 0 dim: 1680x1050.
2008-09-27 22:43:02.554 Screen 1 dim: 1280x800.
2008-09-27 22:43:02.554 Primary screen 0.
2008-09-27 22:43:02.556 Connected to database 'mythconverg' at host: 192.168.2.101
2008-09-27 22:43:02.559 Running in a window
2008-09-27 22:43:02.559 Using screen 0, 1680x1050 at 0,0
2008-09-27 22:43:02.569 New DB connection, total: 2
2008-09-27 22:43:02.571 Connected to database 'mythconverg' at host: 192.168.2.101
2008-09-27 22:43:02.573 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-09-27 22:43:02.574 Enabled verbose msgs:  important general
mythfrontend: symbol lookup error: mythfrontend: undefined symbol: lstat64
jorbuntu@xps:~$

---

