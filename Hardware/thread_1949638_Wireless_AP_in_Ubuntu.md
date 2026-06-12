---
title: "Wireless AP in Ubuntu"
date: 2012-03-30
forum: Hardware
---

### Post by Sysem on 2012-03-30
I just my new shiny Samsung Galaxy S2 and want to share my 3G internet with it (dongle on the PC). I've been all over the web trying to find a way to create a non ad-hoc wifi network for my S2 to connect to and I cannot get it right.

Most sites suggest using hostapd, but I cant seem to get that compiled let alone running. Installing it using "apt-get" doesnt seem to actually install anything, and building it from source is a mission as I cant seem to get the .config file working.

The second suggestion was putting the wifi card into "master" mode, but I that doesnt work either (Operation not permitted error), so I tried finding the latest drivers for my card, the Intel Centrino Wireless-N 1000, and installed that, although I'm not sure if that was successful. 

Any pointers in getting this going? To me, it should be possible as I've done it before in Windows using Connectify, so my wireless card should be able to do it...

Thanks,
Sysem

---

### Post by Sysem on 2012-04-01
Bump. No one?

---

### Post by grahammechanical on 2012-04-01
There is this:

[http://ubuntuforums.org/showthread.php?t=1681163]("http://ubuntuforums.org/showthread.php?t=1681163")

But then again you might want to wait until the end of April when 12.04 is released. It is at beta 2 right now. 12.04 gives you an option to set the PC wireless card as a Hotspot. It will be in System Settings>Network. Select your wireless connection and you will then see a button called Use as Hotspot.

How good that is I cannot tell you. Although I am using 12.04 right now I have no reason for setting it up in Access Point mode.

Regards.

---

### Post by dandnsmith on 2012-04-02
If that card doesn't allow 'master' mode, then waiting for the later release won't help.
I suggest a router, to which you can connect both PCs. This can give the added functionality if the PC with the dongle also has an ethernet interface.

---

