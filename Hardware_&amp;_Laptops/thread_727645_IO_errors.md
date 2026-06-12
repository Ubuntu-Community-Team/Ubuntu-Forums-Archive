---
title: "I/O errors"
date: 2008-03-18
forum: Hardware &amp; Laptops
---

### Post by Salazar420 on 2008-03-18
I was recently running an 80 gb 7200 rpm western digital  to host my OS. Running low on diskspace, and in need of  more space to create a virtual harddisk for a vm guest OS, I attached a 40 gb 5400rpm harddrive. In doing so, I was forced to change ide cables, seeing as how my initial cable had only a board end and another for the harddrive, cd rom, what have you. I was planning to dedicate about half of the drive. Having heard of gparted (I think it was), I figured I'd install that to format and partition the drive. For the record, I think I used either ext2 or ext3 filesystem format ( having had it work in the past on a 1gb flash drive format attempt. Somewhere in the process something got messed. 

Flashing forward, I ended up tweaking my 80gb or something, and couldn't get it to boot correctly. I kept getting some sort of I/O error. With an ubuntu livecd it'd do the i/o errors until eventually a (busybox) opens up. I tried different disks and distros. Nothign worked. I figured it was the cable setup. Messed with em, switched em. When it was set up correctly, I'd get grub error trying to boot from harddisk, and then i/o with livecd. Eventually I got ubuntu to start up after all the i/o errors were satisfied. But installs still failed. I managed to get it to install using a geubuntu distro, but it installed incorrectly, most notably visible via failed network-manager everytime I start up. etc... anyway, I just need to know if anybody knows how to correct the I/o errors so I can isntall ubuntu again. Might try fedora for the time being.

---

