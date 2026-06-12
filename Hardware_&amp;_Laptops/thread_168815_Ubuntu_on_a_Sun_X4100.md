---
title: "Ubuntu on a Sun X4100 ?"
date: 2006-05-01
forum: Hardware &amp; Laptops
---

### Post by dhartnet on 2006-05-01
Anyone ever try this? I started the install, all goes well until it comes to the partition step. It wont show me any disks or partitions, so there is nothing for me to edit, create, delete, etc. Sort of just dies right there.

Im just wondering if the hardware is unrecognizable for Ubuntu?




Dave

---

### Post by Sef on 2006-05-01
It's Solaris chip, so lots of tweaking would be needed to make it run.

---

### Post by mips on 2006-05-01
[QUOTE=dhartnet]Anyone ever try this? I started the install, all goes well until it comes to the partition step. It wont show me any disks or partitions, so there is nothing for me to edit, create, delete, etc. Sort of just dies right there.

Im just wondering if the hardware is unrecognizable for Ubuntu?




Dave[/QUOTE]

Ok, I see it uses AMD Opteron processors and not Sparc so it should work ok.

I believe your problem lies with the mirrored SAS disks for which you need kernel support. I don't know if ubuntu offers this. You might want to compile your own kernel.

[http://www.inserve.se/edu/debian/](http://www.inserve.se/edu/debian/)

Google for "Install Debian on SUN X4100" or replace Debian with Ubuntu.

BTW: Ubuntu does work on Sparc architecture. Have a look at Ubuntu Ports if you have a Sparc based machine.

---

### Post by dhartnet on 2006-05-01
Thanks MIPS..

I ended up grabbing a Dell 1750 to install it on, Ill save the x4100 for a future project..


Dave

---

### Post by kinsoa on 2006-07-13
Hello,

installing Ubuntu Dapper on SUN X4100 or X4200 works well.

I just have a problem with hardware RAID 0 and 1 : such discs are not recognized by the system. No other problem reported until now.


Kinsoa.

---

### Post by crouton on 2006-08-15
Sun X4x00 series uses a LSI Logic MegaRAID SAS chip (SAS1064), which other vendors like Dell also use.  There's a thread on this forum about a Dell 1950 that uses a SAS chip, and that fellow was able to get the machine to boot with the hardware RAID.  Look for it.

---

### Post by jessy on 2006-08-22
crouton: A link would be very helpful as I cannot find your mentioned post

All I know that hardware raid support for that specific SAS controller appeard in 2.6.16-rc? and as dapper is using 2.6.15 it's not yet supported.
A bugreport also exists and maybe Ben Colins will backport that driver, but currently I'm unable to build the dapper kernel(2.6.15) with that backported driver

See also: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/37452](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/37452)

---

### Post by jessy on 2006-08-22
Hi again,

I've written a short howto run Dapper on an X4100 / X4200 using HW RAID

[http://jesusch.de/index.php?page=ubuntu](http://jesusch.de/index.php?page=ubuntu)

Maybe it's helpful

---

### Post by vincus on 2006-08-29
I have the same problem, maybe the kernel doesn't identify my raid controller in the Sunfire x4100.
I googles it for a day but nothing found.... Also Tried DEbian Amd64 with a custom cd and the normal as well, the custom cd found my adapter, but there's something wrong with the installer coz it's broken when i tried to configure the base system...

Any idea?
Thx

---

### Post by jessy on 2006-09-12
vincus,

Hardware RAID is only supported since 2.6.16 kernels - you need to install on a nonmirrored disk, install a custom kernel and afterwards create the mirror.

---

