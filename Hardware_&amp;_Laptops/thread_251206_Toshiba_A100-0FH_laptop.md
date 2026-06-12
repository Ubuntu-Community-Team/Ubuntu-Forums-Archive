---
title: "Toshiba A100-0FH laptop"
date: 2006-09-05
forum: Hardware &amp; Laptops
---

### Post by chappejw on 2006-09-05
Hello all,

I am trying to install Ubuntu 6.06 Dapper Drake on a Toshiba A100-0FH laptop - Model #PSAA8C-0FH00E is also specified on the underside. 

Here's what happens. When I boot from the live CD I get a long list of squashFS errors like this:

[COLOR="Red"][B]SQUASHFS error: zlib_fs returned unexpected result
Unable to read page, block 26xxxx, size 63xxxx

new_ath_hal/hal.o: file not recognized[/B][/COLOR]

then 
[COLOR="Red"][B]mount: function not implemented
hw_random: RNG not detected[/B][/COLOR]

and I also notice that it could not load a driver for my sata HD drive from this.

[COLOR="Red"]**assertion failed 0,drivers/scsi/libata-core.c,ata_file_sg,line=2531**[/COLOR]

After this basically Ubuntu loads to the Desktop, 2 Gnome applets get an error and can't start, then it looks fine. I can use all the menus and everything looks good as new. Sound works, video is perfect, mouse, keyboard etc...

When I click on install and try to partition, my 100 Gig SATA hard drive is listed as the device to install on and I have 3 partitions, the first with windows xp, the other two I created previously with partition commander.

Now, when I try to partition my hard drive with ubuntu, the installer hangs and I can't continue. I can't use any options to partition/choose the drive because I believe there is a driver missing.

Can anybody tell me how I can get my SATA HD to be recognized under Ubuntu? Or if you have any other insight to this. I would like to help other SATA HD users out there.

---

### Post by chappejw on 2006-09-05
Sorry, I should have mentioned,

Hardware for Toshiba A100-0FH - Model #PSAA8C-0FH00E

core duo 1.6
1 Gig RAM
100 Gig SATA HD
Intel Graphics 950 GMA ( works under ubuntu )
Intel Wireless card ( not tested, but linux driver is on Intel site )

---

### Post by chappejw on 2007-06-20
OK, I got through the squashfs errors etc and used the alternate version of Ubuntu for install. It is the same version 6.10 or 7.04 or whatever, just that it's an alternate version for installation I guess. The only thing I have not had any luck getting to work is my wireless card. Everything else is good. a nicer touch pad driver would be nice. Perhaps that is another weekend project.

I'm finding Ubuntu getting better n better though.

---

