---
title: "Transform Wubi Instalation into Ubuntu normal instation."
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by joaojmconstantino on 2009-07-15
Is it possible to transform a Wubi installation without DVD/CD Drive and USB to a complete and normal Ubuntu installation? Thanks. ;)

---

### Post by starcraft.man on 2009-07-15
Yes, here's link to how. Courtesy of bodhi who provided it :).

[http://www.linuxhaxor.net/2008/12/06/graduate-from-a-wubi-install-to-a-dedicated-partition/](http://www.linuxhaxor.net/2008/12/06/graduate-from-a-wubi-install-to-a-dedicated-partition/)

If you've any difficulties ask before you make any changes.

To make the partitions you'll need gparted, that doesn't appear to be covered in the small tut. Just boot into the live CD you installed WUBI with (i.e. put it in drive, reboot machine, and then select it for boot up). Once logged into a live session, you can get gparted from System > Admin > Gparted. Once there, you simply need to make two partitions, one for root containing all your files. The other is swap, same as pagine in windows.

Read [documentation]("http://gparted.sourceforge.net/documentation.php") please on how to specifically use the program, it's quite good with pics and everything.

Then, ensure that you make one partition that is EXT4 and has at least as much space as your WUBI install your transferring into it. Then make a swap file, doesn't need to be bigger than 1GB usually, only used if you've low RAM.

Once the partitions made, follow the instructions on link, quite straight forward. Make sure you use point to the right partitions (i.e. know how large they are approximately in GB).

If you plan on continuing to dualboot windows, I'd recommend an NTFS partition to store your files you want to use back and forth. This is entirely optional though and outside what you asked, it isn't any harder than making an ext4 or swap once you understand the use of gparted.

---

### Post by joaojmconstantino on 2009-07-15
Thank you very much, now I can get back to Ubuntu and erradicate Windows off my life.

---

### Post by starcraft.man on 2009-07-15
> **joaojmconstantino said:**
> Thank you very much, now I can get back to Ubuntu and erradicate Windows off my life.

Your welcome, have a great time. Linux does pretty much everything long as your neither dependent on Office 2007 features or Adobe Suite (usable in VM if necessary). See linuxappfinder for linux application alternatives.

---

### Post by joaojmconstantino on 2009-07-15
Again, thank you very much. I'm loving Ubuntu so far.

---

