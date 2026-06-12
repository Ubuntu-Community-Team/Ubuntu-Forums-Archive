---
title: "Max display res 800x600 on ATI Rage Mobility"
date: 2009-03-11
forum: Hardware
---

### Post by Neon Kitten on 2009-03-11
Hi all,

I installed Xubuntu 8.10 last night on an old Dell Latitude C600 laptop (Pentium III 750MHz, 256MB RAM) since its light system requirements made it a more sensible choice than the other major Linuxes out there. Graphics are ATI Rage Mobility 128.

All went fine with the install, but there's one problem I can't seem to fix - the screen resolution. I am only offered 640x480@60Hz or 800x600@56Hz, with the latter being the post-install default.

However the LCD panel on the Dell has a native res of 1024x768@60Hz. As a result, xubuntu is blurry :) 

Windows XP happily runs on this laptop at 1024x768, and I need to get Xubuntu to do it. I've tried editing xorg.conf to add the right mode specifically (just adding a "Modes" line and nothing else); that resulted in a parse error at boot. I tried installing the ATI Radeon drivers - that resulted in a "cannot detect..." error at boot. In both of those cases, going into low-graphics mode saw the screen running at 1024x768, with Xubuntu sitting at 800x600 in the middle (but sharper :) )

A search here threw up this thread from last year:

[http://ubuntuforums.org/showthread.php?t=882581](http://ubuntuforums.org/showthread.php?t=882581)

...but the solution that seems to have done the job - installing displayconfig-gtk from Synaptic Manager - doesn't seem available to me - there is no displayconfig-gtk listed.

So basically... help! :)

---

### Post by Neon Kitten on 2009-03-12
Solved - simply copying the xorg.conf file from here:

[http://ubuntuforums.org/showpost.php?p=6406456&postcount=6](http://ubuntuforums.org/showpost.php?p=6406456&postcount=6)

...fixed the problem and allowed me to boot at 1024x768.

---

