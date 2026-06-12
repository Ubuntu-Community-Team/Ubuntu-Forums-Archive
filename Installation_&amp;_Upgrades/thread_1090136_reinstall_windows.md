---
title: "reinstall windows"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by heiNey on 2009-03-07
after trying to get ubuntu to play 1080p files with my system, and unable to do so, i tried to install windows on my htpc.  but im getting the microsoft error 0x0000007B (bsod?).  I tried it on a few separate drives that were all former ubuntu partitioned drives and theyre all doing the same thing.  windows xp gets to the point where it says 'setup is loading windows' then just gives me the error.  i cant get into the recovery console or anything.  

does anyone know how i can go about fixing this?  id love to stay with ubuntu, but it doesnt seem to like my onboard graphics and doesnt utilize the gpu for any video processing, so i get stuttering video.  please help...thanks

---

### Post by taurus on 2009-03-07
Maybe you want to boot your machine with Ubuntu LiveCD first.  Then use gparted (System -> Administration -> Partition Editor) to delete all the partitions.  Then, create one partition that takes up the whole hard space and format it to ntfs.  

Now see if windows can install on it.

---

### Post by heiNey on 2009-03-07
yea, ive actually already tried that and im still getting the same problem

---

### Post by conryf on 2009-03-16
Was this ever resolved? I have the exact same problem.

---

### Post by Mark Phelps on 2009-03-17
The link below has some information on the 0x7B code:

[http://www.updatexp.com/stop-messages.html]("http://www.updatexp.com/stop-messages.html")

My guess is that you need device drivers for your hard drive to be loaded at install time (using F6).

---

### Post by heiNey on 2009-03-19
well, it turns out that i did fix the issue.  as mark phelps said, it was due to windows needing sata drivers for the hard drive (windows xp).  im not sure if the motherboard plays a factor, because i have another system that did not need drivers loaded.  

the only way i got around this was to install windows 7 instead, since i dont have a floppy in my computer, and apparently you need a floppy to install the drivers for xp (for my mobo).  windows vista/7 allows you to install the drivers during installation, whereas xp required the drivers to be installed at boot up.

hope that helps.

---

### Post by dandnsmith on 2009-03-19
Yes, the 'standard' solution for systems without floppy drive is to get a copy of the installation files and slipstream in the sata drivers - seems like a lot of work to me.
A quick fix may be to get the necessary drivers on a floppy, and use a floppy drive which connects via USB (but the motherboard/BIOS needs to support this as a viable option at boot time)

---

