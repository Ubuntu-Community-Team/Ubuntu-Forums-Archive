---
title: "Bumblebee: Ubuntu 13.10 stuck on &quot;low graphics mode&quot;"
date: 2014-04-09
forum: Hardware
---

### Post by smurfzilla on 2014-04-09
Hey folks,
Could really use some help - I upgraded from 13.04 to 13.10 and could not get my secondary monitor to be recognized - I saw some posts about installing the ppa: xorg-edgers and on reboot my machine got stuck on the "low graphics mode" screen and can't get it to load now - I tried purging old packages marked with "rc" using dpkg -l, etc. and think I might have got it in worse shape. not sure how to proceed from here - any guidance or help is greatly appreciated!

---

### Post by smurfzilla on 2014-04-09
oh man is that ever nasty! Found this note over at the launchpad site - after purging bumblebee I was able to boot - I still can't get my secondary monitor to work but at least I'm back to the desktop now:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1265570](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1265570)

---

### Post by smurfzilla on 2014-04-09
Final post on this - after going back to nvidia-current-updates and doing some additional purging - I got to a point where when I plugged in my monitor to the display port (30 inch dell monitor) and tried to detect displays - both screens would just go blank and not reappear - after manually readding my display info into my xorg.conf file including having to specify the edid.bin file for my laptop screen and my monitor and rebooting I'm back in business. yuk.

---

