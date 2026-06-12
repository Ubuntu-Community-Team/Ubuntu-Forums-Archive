---
title: "Ubuntu Server 8.04 LTS and Software RAID1 installation"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by Dralt on 2009-08-15
Hi,

So, I am setting up a new LAMP server and I got a machine with 2 identical drives for a RAID1 set-up.

Alas, it's not true hardware RAID and I must do a software RAID installation. (don't want to go the FakeRAID route)

The documentation for this is sketchy.

In fact, there is no such official documentation for 8.04 LTS.

There is documentation for 8.10 and 9.04. There are other sources on the Web as well.

Procedures slightly differ in ways I do not understand.

Assuming this official documentation is correct:

[Ubuntu Documentation > Ubuntu 9.04 > Ubuntu Server Guide > Installation > Advanced Installation]("https://help.ubuntu.com/9.04/serverguide/C/advanced-installation.html")

I do not need to mark any partition bootable.

But, according to these instructions:

[Ubuntu Documentation > Community Documentation > InstallationSoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID?action=fullsearch&context=180&value=Convert+to+software+raid&titlesearch=Titles")

[How To Install Ubuntu 8.04 With Software RAID1]("http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1")

I do need to make the first partition on each disc as bootable.

Similar differences exist when it comes to dealing with GRUB.

I also find little information on how to deal with kernel upgrades.

Does the entire set-up need to be repeated when you install a new kernel?

So, my question: Is there a definitive guide on how to perform a software RAID1 installation?

---

### Post by Dralt on 2009-08-15
I guess I will revert to a non-RAID configuration, since software RAID doesn't inspire much confidence at this time.

---

