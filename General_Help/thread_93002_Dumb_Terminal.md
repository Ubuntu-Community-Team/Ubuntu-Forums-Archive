---
title: "Dumb Terminal"
date: 2005-11-21
forum: General Help
---

### Post by Iandefor on 2005-11-21
Hey all. I've got an old notebook that I'd like to set up to use as a graphical dumb terminal, but I've not got the foggiest idea of how to even start setting that up. If someone could point me in the right direction, I'd appreciate it. In case it might be relevant, it's a Sony Vaio PCG-R505TE.

EDIT: Silly me. The feature I was looking for is called "Remote Desktop Access"

Now, I have a new problem. I did the following: ```
apt-get install tightvncserver tightvnc-java
``` and then when I tried to run tightvncserver, it returned```
root@brownie:/home/ian # tightvncserver 
Found /usr/share/tightvnc-java for http connections.
 suggested, but also was pointed out that it spawns
a new desktop and doesn't link to your currently running session. I
thought it would be most convenient if there was perhaps an "advanced"
button on the remote desktop program that would let you select a
different port to bind to to get around that acces  Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the tightvncserver script.
Couldn't start Xtightvnc process.

21/11/05 04:50:58 Xvnc version 3.3.tight1.2.9
21/11/05 04:50:58 Copyright (C) 1999 AT&T Laboratories Cambridge.
21/11/05 04:50:58 Copyright (C) 2000-2002 Constantin Kaplinsky.
21/11/05 04:50:58 All Rights Reserved.
21/11/05 04:50:58 See http://www.uk.research.att.com/vnc for information on VNC
21/11/05 04:50:58 See http://www.tightvnc.com for TightVNC-specific information
21/11/05 04:50:58 Desktop name 'X' (brownie:1)
21/11/05 04:50:58 Protocol version supported 3.3
21/11/05 04:50:58 Listening for VNC connections on TCP port 5901
21/11/05 04:50:58 Listening for HTTP connections on TCP port 5801
21/11/05 04:50:58   URL http://brownie:5801
Font directory '/usr/X11R6/lib/X11/fonts/Speedo/' not found - ignoring

Fatal server error:
could not open default font 'fixed'
21/11/05 04:50:59 Xvnc version 3.3.tight1.2.9
21/11/05 04:50:59 Copyright (C) 1999 AT&T Laboratories Cambridge.
21/11/05 04:50:59 Copyright (C) 2000-2002 Constantin Kaplinsky.
21/11/05 04:50:59 All Rights Reserved.
21/11/05 04:50:59 See http://www.uk.research.att.com/vnc for information on VNC
21/11/05 04:50:59 See http://www.tightvnc.com for TightVNC-specific information
21/11/05 04:50:59 Desktop name 'X' (brownie:1)
21/11/05 04:50:59 Protocol version supported 3.3
21/11/05 04:50:59 Listening for VNC connections on TCP port 5901
21/11/05 04:50:59 Listening for HTTP connections on TCP port 5801
21/11/05 04:50:59   URL http://brownie:5801
Font directory '/usr/X11R6/lib/X11/fonts/Speedo/' not found - ignoring

Fatal server error:
could not open default font 'fixed'
``` If someone has any suggestions, I would appreciate it.

---

### Post by aysiu on 2005-11-21
You can do a "server install" and maybe follow the Mini-RAM HowTo:
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

---

### Post by Iandefor on 2005-11-21
[quote=aysiu]You can do a "server install" and maybe follow the Mini-RAM HowTo:
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html]("http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html")[/quote] 
Thank you for your speedy answer, but I was actually thinking along the lines of the software I would need to get a dumb terminal set up- I'm not familiar at all with the solutions available. Thanks for your patience with my inexperience in this area!

---

### Post by MarcDM on 2005-11-21
go to [http://www.2x.com/pxes/]("http://www.2x.com/pxes/") and download the 1.0 ISO cd image. 

You're gonna boot the laptop with that. 

Then on your Ubuntu box, go to System -> Administration -> Login Screen Setup

Under security enable "XDMCP" and under XDMCP, check the box that says "Honor Indirect Requests"

Now boot the laptop with the CD you just downloaded from the PXES website. When it boots, and fish comes up on screen, Just press 2 (to boot xdmcp) and hit enter.

if it comes up with a less than optimum screen resolution... at boot time enter : xvm="1024x768" to force it to use that resolution. 

The mouse wheel is disabled by default in pxes so to enable it add :
mwe=1 to the boot line. 

```
2 xvm="1024x768" mwe=1
``` is what I type to boot mine. 

The PXES people also have ways of booting from a floppy or network.

XDMCP will get u everything except sound runnin on the laptop. With all the power comin from the XDMCP server.

Hope this helps.

Marc DM

---

### Post by Iandefor on 2005-11-21
Thank you very much! Now I've got a few solutions lined up that I can try out. I'll be trying PXES as soon as I replace the bum disk on the laptop.

---

