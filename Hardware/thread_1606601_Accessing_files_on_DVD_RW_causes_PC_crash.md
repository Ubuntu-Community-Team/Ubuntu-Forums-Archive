---
title: "Accessing files on DVD RW causes PC crash"
date: 2010-10-26
forum: Hardware
---

### Post by toppcatt on 2010-10-26
Hi Folks
The problem: I have a DVD RW that gets mounted at boot ok as /dev/sr0, I can see files in the top level directory but as soon as I access one of the files it causes the machine to crash about 10-15 seconds later. By crash I mean that the monitor goes blank and the machine does not respond and needs a restart. The discs play fine in other drives/PCs

The DVD drive spins up OK. It previously worked when the machine was in a Win XP PC, but is not known to have worked in this Linux setup that I can remember.

As far as I can tell the drive is alive and well, the logs for dmesg, lshw, mount are attached as is my fstab file. The only anomaly I can see is that my fstab has the rw option as it is a dvd rw, yet the mount output shows it as ro which is rather odd. I have done some extensive searching on other forums, google etc but can't seem to find anything that is a similar problem or a fix that works, hence my own posting.

I am currently running 10.10, but the problem has existed on 10.04 and earlier releases, not sure which but certainly 9.10 and maybe each release back to 8.04, but I mostly use my dvd rom drive instead so have not been bothered by the problem.

I am running an ASUS M3A78 pro mobo with AMD dual core CPU. The drive in question is a LG ( as is the DVD ROM drive). The 2 drives are connected via an IDE ribbon on to a PCI IDE expansion card (mobo only has one IDE slot and I have 3 IDE devices)

I have provided as much info as I can think to give but just ask if you need anymore.

tom@tom-desktop:~$ uname -a
Linux tom-desktop 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux

Attachments,

Thanks

---

