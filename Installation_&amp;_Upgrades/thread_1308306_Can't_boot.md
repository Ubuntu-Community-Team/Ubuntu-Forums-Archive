---
title: "Can't boot"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by unitedwefall on 2009-10-31
Hey

I used 9.04 basically from its release until about one month ago when it started rancdomly crashing. I did a clean install of 8.04 and it was working absolutely fine (most of that was background) anyway i decided that when 9.10 came out it go all the way up to that and see how it went. All was well untill i got to the 9.04>9.10 upgrade when i hit a snag. The intallation froze and when i went to shut it down from the options menu in the top right the whole thing crashed. Now when i try to boot to 9.04 i get this error > one or more of the mounts in etc/fstab cannot be mounted it then lists my swap and file systems and gives me an option to press escape to get to the recovery shell. i dont know how to resolve that so downloaded a live CD for 9.10 and just tried putting that in- but now i cant get passed the boot screen on it. And even my old 8.04 live CD wont work now to boot from. My windows partition seems to be fine. Any ideas?

---

### Post by macogw on 2009-10-31
"can't get past the boot screen"? Which boot screen? Your BIOS splash where it says DELL or whatever? Or...which part of the CD?

---

### Post by unitedwefall on 2009-10-31
wow okay i managed to get somewhere; i did a ```
mount -o remount,rw /
``` then ```
sudo dpkg --configure -a
``` which threw up a couple of error but now i can boot and its very odd. 9.10 seems to be half installed or something cause i have a new login screen and a bit of a new boot sequence but when i get in my touchpad wont work although keyboard shortcuts seem to be ok.

---

### Post by unitedwefall on 2009-10-31
I can get to te part where it says ubuntu and the bar runs across the bottom but no further from CD. Thanks for replying!!

---

### Post by macogw on 2009-10-31
It was mounting read-only because the filesystem got a little screwed up during the shutdown, I think.  Try running "fsck" on it from a live cd.

---

