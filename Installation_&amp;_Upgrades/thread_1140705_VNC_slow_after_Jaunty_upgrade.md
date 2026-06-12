---
title: "VNC slow after Jaunty upgrade"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by mebigfatguy on 2009-04-27
Greetings,

   I had vnc server running reasonably well (as well as vnc runs) in 8.10. After I upgraded to 9.04, connecting from windows using UltraVNC (the client that was used before) is now eternally slow. I see the desktop immediately, can enter my desktop sleep lock password, and have it accepted, but then anything after that, either mouse clicks or keyboard typing takes around 10 minutes per action. Literally!.

Any ideas how i can fix this?

---

### Post by chross on 2009-04-29
This is exactly my problem! In Intrepid everything was perfectly fine and fast, but now on Jaunty I experience heavy lacks as you described. When I log in, it takes ages for the screensaver to vanish as well as opening menus or other tasks. I also recognized problems with moving windows. The windows are actually moved on the server, but there is no visual response at the local machine, i.e. the windows stick in place.

Any suggestions?

Cheers, chross

BTW: my first post :)

---

### Post by mebigfatguy on 2009-04-30
Seems like a common problem... see similar thread

[http://ubuntuforums.org/showthread.php?t=1144104&highlight=vnc](http://ubuntuforums.org/showthread.php?t=1144104&highlight=vnc)

and bug report: [https://bugs.launchpad.net/ubuntu/+s...no/+bug/353126](https://bugs.launchpad.net/ubuntu/+s...no/+bug/353126)

---

### Post by la5lia on 2009-05-03
Same problem here!

When are they going to fix it ?

---

### Post by Imoen on 2009-05-24
I'm glad to know this isn't only me with the problem. Also I have noticed that mouse cursor seems to become distorted at times and there's a strange pixilation in certain areas of my screen but it's not changed on certain colors or anything like that, only on random locations.

---

### Post by steeff on 2009-06-01
+1
I use jaunty on a computer without screen, for media and download purposes.
so without vnc is it impossible to use !
please do something quickly...](*,)

---

### Post by xyeo on 2009-06-10
Had the same issue. Disabled the visual effects and it works fine now.

---

### Post by ricojonah on 2009-10-29
I just posted a fairly easy solution/workaround for resolving this problem in the Tutorials section of the Ubuntu forums. It's pending approval right now, so here's the actual post for anyone who wants to read:



**BACKGROUND: **
Every Ubuntu 9.04 Jaunty and 9.10 Karmic system comes with a VNC server and Client (vino for the server, and both vinagre and tsclient for the client). The problem I've noticed is that every VNC session I've used with Ubuntu's default VNC server/client tools has had a noticeable amount of sluggishness. The slowness is extremely noticeable when a VNC server is connected to over low-bandwith connections (weak wireless LANs, ISP plans with less than 512kbps for upload bandwidth). This has been an ongoing issue for several months, and I've seen many, many users reporting the same problem.

**DISCLAIMER: **
This is a *possible* workaround/solution for the problem. (I say [I]possible[I] because I'm no expert with the guts & entrails that make vnc function on Ubuntu, but this solution worked for me).

**POSSIBLE CAUSE: **
By default, Ubuntu uses **vino** for the VNC server, and two different clients for connecting to it: **vinagre**and **tsclient (Terminal Server Client)**.

Unfortunately, the default VNC clients appear to use a lot of bandwidth during VNC sessions. The primary reason for this is that neither**tsclient** nor **vinagre**, provide a means to configure the compression levels of the VNC session (at least not on the GUI). By default, both clients appear to assume a very low (or no) compression, causing the VNC sessions to eat up a lot of bandwidth.

Vino, as the vnc server, is capable of serving a low-bandwidth/high compession vnc session, so replacing vino with something like tightvncserver is NOT necessary.
[B]
POSSIBLE SOLUTION:[/B]
I just tested this on two of my home computers: Try using a different vnc client instead of tsclient or vinagre. 

1) I installed xtightvncviewer, which is installable using apt-get or synaptic. It is command-line based, but it supports the ability to set the compression level of the VNC connection. (If anyone knows of a GUI-based VNC client for Ubuntu that allows you to set compression levels, please post! :D ).

2) I connected to my VNC server (from my client, using xtightvncviewer) using this command in a terminal window:

```
xtightvncviewer -compresslevel 9 192.168.1.20
```

Note: the *-compresslevel 9* option specifies the maximum level of compression (it's a noticeably lower quality, but uses MUCH less bandwidth and is still decent & very useable). Of course, you'll want to replace *192.168.1.20* with the actual IP address or hostname of the VNC server you're wanting to connect to.

You may be prompted for your VNC password within the terminal, if configured for one on your VNC server.

3) That's it!

Please post if this resolves anyone's issue with the slow VNC connection. It worked for me, and I'd love to know if it helped someone else too.

As an afterthought, this problem seems like a pretty silly one to me. Why does neither tsclient nor vinagre provide a GUI option to set the compression levels? Almost every other VNC client I've seen allows this, and this is absolutely essential for anyone wanting to remote over a low-bandwidth or WAN connection). 

Also, I've noticed some threads and tutorials suggesting that the vino VNC server needs to be replaced with a different VNC server to get better low-bandwidth performance. I'm not sure why anyone would think that's necessary--Vino's very well-integrated and supports low-bandwidth/high-compression sessions; it's the clients that appear to be the problem.

Please post your thoughts, results, and suggestions. Thanks!

---

