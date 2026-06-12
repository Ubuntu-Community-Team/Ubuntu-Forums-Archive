---
title: "Home folder backup"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by ffixcollector on 2009-05-18
from what I understand, to back up ubuntu all I need to do is backup the home folder. If I had to restore my computer, I assume that I would reinstall the OS and then copy all the items from my old home folder to the new home folder on the reinstalled OS.

Will everything be restored, including; shortcuts, menu items, programs, scrips, and passwords?

---

### Post by logos34 on 2009-05-18
> **ffixcollector said:**
> 
Will everything be restored, including; shortcuts, menu items, programs, scrips, and passwords?

everything except programs and installed apps, system settings (->/usr and /etc) 

You might consider putting /home on a separate partition (link [here]("http://www.psychocats.net/ubuntu/separatehome"), or the one below in my signature), which would make it easy for you to backup your entire / partition by taking a periodic snapshot/image of it using clonezilla or partimage.  If it gets borked by an distribution upgrade gone awry or some other calamity, you can just restore the image of it (from dvd, hdd, usb, wherever you stored it). Works well for me: having my / separate (~ 6gb) means I can make a compact .gz image of it (only ~ 2 gb) and stick it on a dvd+rw.  Just restored mine yesterday after some newly-installed apps pooched by machine.  Couldn't boot, so just fired up my Parted Magic rescue cd, restored the backup image of /, and back in business 15 min later. 

at a minimum, if you want to stick with single partition, you could backup you installed .debs in addition to home files, and/or run this command to save a list of all your installed apps, so that if after reinstalling you can get all your programs back with a single command:

dpkg --get-selections > my_installed_pkgs

to reinstall all the packages, just reverse:

dpkg --set-selections < my_installed_pkgs

good luck

---

### Post by ffixcollector on 2010-12-31
> dpkg --set-selections < my_installed_pkgs

Doesn't work, I run it but nothing happens. I have quide a few PPA's installed also, How do I transfer them over?

---

### Post by azertyh on 2010-12-31
hello,
to back up the .deb, i followed [this howto](http://ubuntuforums.org/showthread.php?t=819396).
i did it this morning. apart from the problem to install dpkg-repack, it worked very well.

---

### Post by ffixcollector on 2010-12-31
My current system is set up just the way I want. I would like to migrate it as seamless as possible. I would image the HHD, but I don't believe it would work properly because the HDD UUID's and would change.

---

### Post by CharlesA on 2010-12-31
The UUID stays with the partition. You can try cloning the current drive to a larger drive and then expanding the partitions, but be sure you have a good backup before you do so. :)

EDIT: In any case, if the UUID changes, you can always fix it by booting off a livecd and fixing fstab.

---

