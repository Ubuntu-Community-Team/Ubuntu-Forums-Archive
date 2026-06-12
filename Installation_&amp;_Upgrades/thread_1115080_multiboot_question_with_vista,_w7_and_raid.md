---
title: "multiboot question with vista, w7 and raid"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by g3hedges on 2009-04-03
Hello.  I apologize if this question has been asked and answered a hundred times, which I'm sure it has. (I tried to look)

I am wanting to multiboot Vista, Windows 7 and Ubuntu 9.0.4.  I am already dual booting the two windows.  Here is my hdd setup.  2x500gb setup in RAID 0 with Vista installed.  Windows 7 is installed on a separate 500gb drive outside the array.  If it matters there are two other drives in the system which are used for data and backups only.  Vista was installed first and then Windows 7 which all went well.

I have now decided I want to add Ubuntu to the mix and downloaded the beta version since I don't plan on using it as a main os anyway.  I used windows 7 and "shrinked" the size of the hard drive that w7 was installed on freeing up approx 120GB of space.  So what I'm trying to do is have W7 and Ubuntu installed on the same hdd.

I booted into the setup cd and began the installation.  This may be where I screwed up.  During the installation Ubuntu setup reported that A Serial ATA RAID device had been detected and it asked if I would like to initialize this RAID device.  I said no because I was afraid of screwing up my Vista install which is my main os.  (I do have a backup image of it but would still rather not have to restore it.)  Setup then scanned and detected all of the hdd's in my system.  I selected the partition that I had created using w7 earlier and continued with the install.  Everything appeared normal, no errors and then I was prompted to remove the media and reboot.  I rebooted and was not given a choice to boot into ubuntu only vista and w7.

Should I have initialized the RAID?  I keep seeing post that reference GRUB but I never saw an option for this during setup.  Also while researching I saw Wubi mentioned, would this be the safest, easiest way of multibooting?

I appreciate any help and again sorry for the newbie ?

---

