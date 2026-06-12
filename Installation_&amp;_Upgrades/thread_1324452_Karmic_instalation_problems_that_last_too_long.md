---
title: "Karmic instalation problems that last too long"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by diggerOS on 2009-11-12
I am trying to do a clean install of Karmic Koala 64bit since it's oficially out but there are issues that are not letting me to do so.

1. using live cd:
At the begining the screen was black with white logo flashing and then after a while it would gone leaving whole screen black. I found out i have to ad vga=789 at boot options on the main menu of live cd.
So I did it...and now white logo flashes and under of it there are logs nicely moving up with OKs at the right like I supose it should be. After a moment the screen goes black and live CD continues to spin.
I googled and tried to remove 'quiet' and '--' from boot options at the main menu but with no luck, tried also inputing diferent VGAs and still no luck.. Video card is NvidiaGeForce7300GT.

2. using alternate install cd:
installation starts well but at the end it ask me for media change: 'please insert the disc labeled...' that is already in. At that moment I can't eject cd or do anything but force restart computer.

Upgrading from Jaunty works fine, but I would really like a clean install. I've installed Ubuntu so many times but something like this never happend before. I know and I can feel the solution is something very simple, like it usually is, but I don't have enough knowledge or practise to solve it.

Thanks in advance&sorry for bad english.

---

### Post by phillw on 2009-11-12
Do an md5 checksum on your cd's -->  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Is a good start. I'll go have a dig about your video card.

/edit ... It's listed as supported --> [https://launchpad.net/ubuntu/karmic/amd64/nvidia-glx-173/173.14.16-0ubuntu1](https://launchpad.net/ubuntu/karmic/amd64/nvidia-glx-173/173.14.16-0ubuntu1)
some more information is over here --->  [https://launchpad.net/ubuntu/karmic/+package/nvidia-glx-185](https://launchpad.net/ubuntu/karmic/+package/nvidia-glx-185)

Phill.

---

### Post by diggerOS on 2009-11-12
Thank you phillw for quick reply. 
Yes, checksum is not the same. What program should I use to burn again without checksum issue?

EDIT...solved tywm!

---

### Post by uwezi on 2009-11-25
We also had the same problem today - installing Ubuntu Server 9.10 on an IBM server with software RAID 1 on two PATA harddisks. 

The problem was most probably caused by an old-style 40-wire IDE cable between the on-board controller and the harddisks. This was obviously good enough for the old Linux on the machine, but not for fast access to the disks used by Ubuntu.

Replacing the IDE cable with a 80-wire UDMA cable and connecting the harddisks to individual channels (primary and secondary IDE) of the on-board controller resolved the problem.

Uwe.

---

