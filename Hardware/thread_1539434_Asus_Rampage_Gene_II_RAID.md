---
title: "Asus Rampage Gene II RAID"
date: 2010-07-26
forum: Hardware
---

### Post by dawrobel on 2010-07-26
I'm switching from windows and trying to install Ubuntu 10.04 on my current setup (4 1TB drives, Raid 0+1). When I try to install though I am unable to see the array properly (ie. During the partition definition part of the setup I can create a new partition table but I don't get any options as when i would install to a single drive not in a raid -  letting me use the entire disk). Im thinking that perhaps Ubuntu isn't seeing my raid? Anyone else experience this issue? 

I would like to keep the same setup I had when i was using windows (it would see approx. 2 TB of space).

---

### Post by dabl on 2010-07-26
RAID in Linux is not the same as RAID in Windows.

Software RAID: [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

and

[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)


FakeRAID: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by ronparent on 2010-07-26
Since you are currently trying to use a fakeraid structure created in windows in 10.04, there is a problem that gparted will not recognize the raid drive and thus is not installable to a raid without a work around. The problem originates from 10.04 being distributed without the program kpartx, which is an adjunct to gparted and needed for gparted to address a raid drive. The solution is to boot to the 10.04 live cd, install kpartx with synaptics, and, to continue to run the install from the same live cd session. 

Attempting to install to a nested raid (the raid 0+1) may present additional problems. See [http://ubuntuforums.org/showthread.php?t=1533793](http://ubuntuforums.org/showthread.php?t=1533793) 

Basically the party in the above link was unable to partition a nested raid like yours. Unfortunately I was unaware of the kpartx issue when I originally corresponded with him, and yhey are currently unavailable to test the status of possible fixes. 

I'll note that unless your raid based data is well backed up, I wouldn't try to change your raid to a software raid based system at this point. Tampering with the data structure may result in complete loss of the data on the current raid. 

I will be happy to help, if I can.

---

### Post by dawrobel on 2010-07-27
Thanks for your help, I should clarify I have backed up all my data off at this time and wanted to setup my system with Ubuntu as the one and only OS I have on the machine. After reading the fakeraid thing and seeing its not officially endorsed by Ubuntu it might not be a good idea (I'm actually using this computer for computational purposes and my supervisor at the university wanted me to make several backups of my data as its pretty important material).

Would you say it might be a better idea to simply setup one drive as the main one and then find software to clone that drive onto the others as a backup solution?

---

### Post by ronparent on 2010-07-27
I think that a raid setup is no replacement for a sensible backup system. There is probably no compelling need for a raid in a typical home or private setup with one primary user. In any case I personally would never lump my OS, programs, and data onto one partition. I personally use raid 0 primarily for speed and am under no illusion that even a raid 1 offer any real safety. That said, the choices are yours.

---

