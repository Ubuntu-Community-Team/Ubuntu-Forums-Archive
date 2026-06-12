---
title: "No text-only Installation"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by bcourbage on 2009-08-23
I am trying to migrate an installation from Fedora to Ubuntu 9.04 on a system that has a hardware RAID1. I read that this configuration requires the Text only installation available on the Alternate install CD. So I downloaded the "PC (Intel x86) alternate install CD" for the x86 Dell, validated the md5sum against the Alternate md5sum in [http://releases.ubuntu.com/9.04/MD5SUMS](http://releases.ubuntu.com/9.04/MD5SUMS), booted from the install CD and "checked disk for defects." Everything checked out.

However, according to forums, I expect to find an option for the text-based installation in the initial menu. My installation CD does provides no such option. Can anyone point out what I'm doing wrong? I've tried on two separate machines and one VM to make sure that it wasn't hardware related.

---

### Post by staf0048 on 2009-08-23
Have you tried the first option - "Install Ubuntu?"  While I have not tried the alternate CD for 9.04 yet, I used it to install 8.04 to encrypt the HDD on my laptop.  On a graphical install it should say something like "Try Ubuntu without any changes to your hard disk" or something like that.

In either case, you are able to abort the installation before making any changes to your HDD, so proceeding with the first option will not harm your current system.

---

### Post by bcourbage on 2009-08-23
Hi Staf,

Yes, I tried it. It behaved identically to the GUI install in the Server version. When came the time to partition disks, the list of available partitions was empty. When I look at the installer main menu, the closest item I find is "Execute a shell."

Note: The RAID1 array is "virgin," freshly reformatted.

I even tried to boot with the Fedora Core 9 DVD, partition the drive and exit before the installation. Then install Ubuntu. No joy in the partition screen.

Do you recommend I try 8.04? I'm reluctant to try it because I use a wireless card on that box that uses the RTL8187b chipset and is not supported by older kernels (I think 2.6.27 is the oldest and forums indicate that people have had problems with this interface using Hardy Heron).

Alternatively, if there is an update path (via command line or gnome) to update to 9.04 I might try that. Is this possible?

---

### Post by staf0048 on 2009-08-23
Sorry, I have no experience with the new "alternate" cd's.  8.04 alt worked perfectly for me . . . was there an option anywhere to create your own partitions?  I doubt I'm going to be much help with this problem, but I'll give you a bump in hopes it catches someone's eye.

---

### Post by bcourbage on 2009-08-23
Thanks again for your help. There was an option to create partitions but the partition list (even empty space) was empty.

The issue has become academic at this point. I managed to work around it by removing the RAID array, installing the basic OS and re-establishing the RAID sync (feasible since it's a HW RAID).

---

### Post by slakkie on 2009-08-23
Grab the minimal CD install. Provides CLI sytem install

---

