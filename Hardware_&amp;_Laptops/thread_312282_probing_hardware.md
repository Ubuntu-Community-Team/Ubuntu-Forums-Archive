---
title: "probing hardware"
date: 2006-12-04
forum: Hardware &amp; Laptops
---

### Post by daveoily on 2006-12-04
I'm making my first faultering steps in the world of linux, congrats to whoever it is (and I know there are probably MANY of you) who made this distro what it is, to me, it's been the easiest, most functional version of linux I've put on any machine of mine.

However... as seems to be the case with most linux distributions, there's always something that doesn't work, (usually the modem) I'm using breezy, so perhaps some things have been fixed in more up to date versions, nevertheless, I still wish to get closer to developing the o.s. by understanding how things work. [hence I'm not too sure why the root account is obscured by default (some security issue I guess:rolleyes: ), but I've sorted that out now by searching for appropriate threads on this very forum :) ]

There appear to be many useful commands that are available on the comand line to diagnose what hardware you have (and presumably this info is useful if intending to write a driver for said hardware). I'll list the ones i've found out thus far...

cat /proc/cpuinfo   .... probes the cpu
hdparm -i /dev/hda  ..... info on hard drive 
fdisk -l  .... also hard drive, but more like info on partitions
cat /dev/sndstat ...... probes the sound card
lspci -vv .... probes the pci slot??? (on mine I guess that probes pcmcia, as it's on a laptop:confused: )
lsusb ... probes the usb

Superprobe seems not to be used on this version of linux, it's been a while since I did a fresh install of any linux versions (which seemed to require it) I guess it's been replaced by something better... what would that be? My graphics work fine anyway, it'd just be nice to know.

I'm guessing there's a similar command for finding out about the modem, does anyone know what it is?

How many more hardware diagnostic type commands are there? And what are they? Please post any that you've found useful.

---

### Post by halfvolle melk on 2006-12-04
There's also lshw which you should run as root, ie. **sudo lshw**.

---

### Post by daveoily on 2006-12-04
Thanks that seems to list ummm... everything! 

I actually enabled the root account as it's just a kacky laptop for mucking about on ;) but I guess I could have used sudo.

:) Are there any more? (if, indeed I really need them) perhaps I should ask, is there anything that lshw doesn't list?

---

### Post by halfvolle melk on 2006-12-04
Check this link
[http://www.ahinc.com/linux101/](http://www.ahinc.com/linux101/)
It talks about system info amongst others.

---

