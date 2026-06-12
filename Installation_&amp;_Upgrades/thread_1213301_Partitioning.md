---
title: "Partitioning"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by jmac25 on 2009-07-14
I am trying to install Ubuntu on a laptop with Vista. I would like to be able to do a dual boot. I thought that on install it would partition my hd and install ubuntu alongside vista but that is not an option to install alongside. I would like to not have to delete vista if at all possible. Maybe I need to do a little more work than just run the install from the iso cdrom i made? Please help.

---

### Post by merlinus on 2009-07-14
Use vista's disk management tool to shrink its partition, but defrag several times first.  Then you can select side-by-side from the ubuntu partitioning menu.

Also, make sure you have backed up important data before doing anything.

---

### Post by konnorrigby on 2009-07-14
Hello, dual booting is verry simple. when you are in are in the partioning menu select run ubuntu alongside other operating systems, and chose the size you want your ubuntu space to be, and then vista, do [COLOR=#ff0000]*NOT* [/COLOR][COLOR=black]shrink the vista partion to smaller than the space taken up by documents, program files, ect.[/COLOR]
 
hope i helped.

---

### Post by Mark Phelps on 2009-07-15
It's not really "verry simple" -- unless, that is, you want to be left with an unbootable version of Vista.

Follow the advice offered by merlinus and use the Vista Disk Management tool to shrink Vista.  Don't use the Ubuntu installer or a GParted LiveCd, or any other Linux disk utility tool.

---

### Post by Ra-Hoor-Khuit on 2009-07-15
Step-by-step Tutorial for this particular dual boot here:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by raymondh on 2009-07-15
Merlin's given good advice.

More tips:

1.  back up your files.  No gurantees.
2.  Boot the liveCD and check for defects and hash/[md5sum]("https://help.ubuntu.com/community/HowToMD5SUM")
3.  Try out ubuntu without any changes ... to see how it plays with your system.

More dual-boot/install/GRUB resources:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://orgs.man.ac.uk/documentation/grub/grub_toc.html#SEC_Contents](http://orgs.man.ac.uk/documentation/grub/grub_toc.html#SEC_Contents)

Good luck.

---

