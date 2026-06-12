---
title: "Trouble with Rosegarden and Jack"
date: 2008-10-21
forum: General Help
---

### Post by Firedragon15309 on 2008-10-21
Hey all, I recently became a full Ubuntu user and completely erased windows and I downloaded rosegarden to make some beautiful music. However, it refuses to even open. I've checked forum after forum and none of them seem to have an answer to my problem. They have suggested that I download Jack and I have, however, whenever I start up Jack it comes up with this message in the message area. 
> 22:13:42.819 Patchbay deactivated.
22:13:43.040 Statistics reset.
22:13:43.184 Startup script...
22:13:43.184 artsshell -q terminate
22:13:43.327 ALSA connection graph change.
Error: Can not create link from "/home/josh/.kde/socket-josh-laptop" to "/tmp/ksocket-josh"
Error: Can not create link from "/home/josh/.kde/socket-josh-laptop" to "/tmp/ksocket-joshoDZDv2"
can't create mcop directory
Creating link /home/josh/.kde/socket-josh-laptop.
22:13:43.745 Startup script terminated with exit status=256.
22:13:43.745 JACK is starting...
22:13:43.746 /usr/bin/jackd -R -P10 -dalsa -r44100 -p1024 -n15 -D -Chw:0 -Phw:0 -s -S -Xraw -H
22:13:43.748 JACK was started with PID=9095.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210935632, from thread -1210935632] (1: Operation not permitted)
cannot create engine
22:13:43.795 JACK was stopped successfully.
22:13:43.795 Post-shutdown script...
22:13:43.796 killall jackd
22:13:43.948 ALSA connection change.
jackd: no process killed
22:13:44.203 Post-shutdown script terminated with exit status=256.
22:13:45.972 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.


Then when I try pushing start to start it up, it will start for about 30 seconds and then time out. If anyone can please help me I will be extremely grateful.

---

### Post by spiderbatdad on 2008-10-22
seems like a problem with the jackd installation...it is trying to run in user space, but access root files. How did you install the programs jackd and rosegarden? They are in synaptic package manager. Maybe the user account you are using doesn't have sufficient privileges. Is this the administrative account?

---

### Post by Firedragon15309 on 2008-10-22
Ya it's the admin account. I downloaded both through synaptic as well. if it helps, this is the error message that pops up.
> Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info.

---

### Post by Vadi on 2008-10-22
I had jack issues with rosegarden also. I used Jokosher in the end, I'm interested in a solution to this issue just to know.

---

### Post by Firedragon15309 on 2008-10-22
This is actually on of the websites that I used that one forum said would help as well. [https://help.ubuntu.com/community/UbuntuStudioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation")

---

### Post by Firedragon15309 on 2008-10-22
and that's how i tried to do it most recently. When I tried running it through root and this was the message that came up on there. > Warning: no locale found: /usr/share/locale/qjackctl_en_US.qm

---

### Post by Firedragon15309 on 2008-10-22
Ok, so I have been able to successfully start up Jack by changing the drive to dummy and I am now able to open Rosegarden but only through the terminal can I do any of this and only by using sudo commands. Also, Rosegarden still has no sound so now I am trying to figure out how to fix that issue which is pretty big considering it is a sound editing program.

---

### Post by Vadi on 2008-10-22
Tried posting on their forums, if they have any? Probably would get more help in there.

Also, getdeb has a newer version of rosegarden available, give it a try: [http://www.getdeb.net/search.php?keywords=rosegarden](http://www.getdeb.net/search.php?keywords=rosegarden)

---

### Post by Firedragon15309 on 2008-10-26
It wouldn't even work with that one. :( it doesn't have enough support from my system and it told me to go through synaptic to get the best one. :(

---

