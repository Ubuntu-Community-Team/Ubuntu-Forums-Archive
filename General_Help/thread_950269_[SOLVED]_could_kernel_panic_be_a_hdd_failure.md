---
title: "[SOLVED] could kernel panic be a hdd failure?"
date: 2008-10-17
forum: General Help
---

### Post by gschoppe on 2008-10-17
I am getting a kernel panic on boot... it started when I was downloading a large torrent... the computer froze, and panicked on reboot.

the system says it is not a software error...

I have 2 drives... with a root and swap partition on drive one, and an LVM that spans drives one and two, containing home and my data partitions... could a failure of drive two have caused this?

---

### Post by MaxIBoy on 2008-10-17
Try booting from a liveCD, mounting all your partitions, and typing this into the terminal:
```
fsck -s /
```
The fsck command should fix any file system errors you might have. This may take a while, so you'll probably want to do it overnight.

---

### Post by gschoppe on 2008-10-17
will that work with LVM? can I even mount LVMs from a live CD?

---

### Post by WSmart on 2008-10-17
Absolutely, hard driver issues can cause kernel panic.  I solved one by using fsch as MaxIBoy suggests.

I've also played with LVM.  I set that up with a Xubuntu 8.04 alternative CD.  It makes my bile turn thinking about it.   I think the first rule in setting up LVM should have been that it behaves exactly like a regular device.  Good grief.  You have to be extremely careful with it.  You can't just open a partition manger and start punching keys.  I moved my drives around-only had the LMM extended onto a second drive and no format extended or partitions-and suddenly it's hosed.  I think if I had just moved the drives back, it might have worked, but I ran whatever, fsch, I guess, from a different machine's partion editor, thinking the partition was only one drive, that the extended...extents, wouldn't matter.  Wrong.   

Maybe things are better with the newer installs. 

Good luck.

---

### Post by gschoppe on 2008-10-17
so how would I run fsch, or an equivalent command on my secondary drive (or entire lvm) without "hose-ing" it?

---

### Post by DrMega on 2008-10-17
One of my machines, which had been running solidly for months, decided to freeze one time. On reboot it got so far and died, on subsequent reboot the BIOS screen said there were no disks. It turned out that the cable had simply come loose on my hard disk.

---

### Post by jerome1232 on 2008-10-17
I worked over how to use these volumes from a live cd a bit ago, here's my thread.
[http://ubuntuforums.org/showthread.php?t=940904](http://ubuntuforums.org/showthread.php?t=940904)

Skip the bit about encrypted partitions, basically once you have the lv's active run fsck on /dev/volumegroupname/volumename, don't mount the lv's.

---

### Post by WSmart on 2008-10-17
The partition manger will list the LV's as device options if you have LVM support on the system.  Then you just choose the LV and run fsch normally, is my understanding.  The LV has the /dev/vg/vn type name, as metioned above.  

Post and let us know how it goes.

A stupid people finds true justice in a stupid President; be real, be sober.

---

### Post by gschoppe on 2008-10-18
I managed to get fsck to run on my drives... there was an issue with my spanned partition and it appears to have fixed it... the system booted properly after, so it appears all is well...

one odd thing did happen: the first time i ran fsck off the live cd, i alt tabbed away, and started surfing the web while it ran... in a minute or two, my computer locked up hard.  after a reboot, i ran it again, after closing all other windows, and it completed ok.

thank you all... I'm gonna do some burn-in testing, and see if there's a more serious HDD issue at fault, or if it was only a glitch.

---

