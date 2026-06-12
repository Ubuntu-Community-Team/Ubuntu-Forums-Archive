---
title: "Ubuntu 10.10 ProSavage8 Video fix."
date: 2010-10-22
forum: Hardware
---

### Post by jimmer321 on 2010-10-22
I could not get any higher Resolution than 800x600 so I created a new xorg.conf file in the /etc/X11 directory.Just copy and paste the info below and reboot and you are up and running with resolutions from 1280x1024 down. You may have to change the Monitor Identifier to your monitor.

---------------------

Section "Device"
Identifier "S3 ProSavage DDR-K"
Driver "vesa"
EndSection

Section "Monitor"
Identifier "Xdebc Monitor"
HorizSync 30-60
VertRefresh 50-75
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "S3 ProSavage DDR-K"
Monitor "Xdebc Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

---

### Post by vs8 on 2011-01-11
I have a friend with an old computer that Uses one of these S3 Savage GPUs, I've had the worst nightmare trying to make it display the right resolution. When I finally "fixed" it by creating my own xorg.conf, log out, suspend, hibernate, switch user, and everything in between got messed up, even restart and shut down!

I'll try this and hope for the best! Thank's in advance!

---

### Post by bossbruin on 2011-04-22
thank you this worked beautifully for me even though there was no xorg.conf file to begin with.  is there a place i can look up my monitor identifier as it is coming up unkwown

---

