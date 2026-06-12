---
title: "Best Way to Try New Versions"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by artsci2 on 2009-04-15
It seems the best way to dabble in new systems and features is to have three hard drives. One as the primary and dependable base system. an experimental system drive, and a data drive. This is not so hard to set up since the cost of hard drives is so low.

One issue that comes up for us less skilled dabblers is related to the GRUB configuration after making some catastrophic change in the experimental system that results in a "GRUB error" and non booting of the base system. This can be avoided by installing the base system while the experimental drive is disconnected. Then disconnecting the base drive and connect/install the experimental system drive. After reconnecting both drives and rebooting you can use the BIOS to choose the boot device.

This physical swapping of drives is not difficult on a desktop cpu. Laptops are a different story though. I would like to install on an external hard drive without touching the internal drive or installing a dual boot GRUB on the external. How do I find out what selections to make so the install CD does not touch the internal drive and does not put Grub on the external drive?

---

### Post by Sef on 2009-04-15
The best way to try new versions is with the live cd.   If there is a problem with the live cd, then almost certainly it will happen upon install.

---

### Post by techlive on 2009-04-15
according to me , we can try new versions in any free virtual hypervisor, like Sun Virtualbox which I use..

---

### Post by stringkarma on 2009-04-15
I'd have to agree, for testing (and actually for serving, if you want to be sure that your desktop can act as a server, without breaking the desktop) is to use virtualbox.

---

### Post by artsci2 on 2009-04-15
> **Sef said:**
> The best way to try new versions is with the live cd.   If there is a problem with the live cd, then almost certainly it will happen upon install.

Yes I definitely try live CD first. But If I want to add some programs and try them it's time to install on HD.

So all I'm hoping for is an easy to understand method to install a system to a second hard drive without installing a boot manager that will cause problems after one of the drives is changed.

---

### Post by oldos2er on 2009-04-15
I have my own method of doing this; when I'm installing a new distro into a "sandbox" partition, I don't allow it to install its boot loader. After it's installed, I manually add an entry for it in grub's menu.lst. There's only one distro this hasn't worked for--Sidux--because it doesn't seem to have the option not to install a bootloader. Every other distro I've tried does.

---

### Post by Therion on 2009-04-15
> **artsci2 said:**
> So all I'm hoping for is an easy to understand method to install a system to a second hard drive without installing a boot manager that will cause problems after one of the drives is changed.
Maybe I'm not understanding something here, but the scenario you describe is my exact setup.  I have two drives I use primarily: one is labeled "Stable" and the other "Experimental".  Stable holds a fully updated and ready-to-use install of my current DOC (Distro Of Choice (currently that's Jaunty)).  Experimental is my test-drive drive. 

When I feel like trying out a new distro here's the drill:

Shutdown the system and unplug it (I'm just anal that way about electricity dontcha know...)
Swap "Stable" for "Experimental"
Reboot with LiveCD of Distro X in the optical drive
Pop into the BIOS (just to make sure boot chain is as it should be and that the drive swap is being recognized...)
Continue with boot of LiveCD
Install Distro X from LiveCD
Reboot into new install of Distro X
Go nuts with updates, installs, whatever the heck I want with reckless abandon because my stable install is safely tucked away and sitting pretty on a drive all its own!  Very nice.

This entire process takes about five minutes on my system since I have a removable drive cage and tool-less drive connectors (snap in/snap out).  

Furthermore, since the boot-loader for Distro X installs on Experimental along with the distro itself, there *are no* boot-loader issues to contend with.  

Lastly, I have an external, 500GB, Data drive that holds my backups and only gets connected when I'm running off the "Stable" drive/install and only when it's needed.

---

### Post by daboroe on 2009-04-15
I saw what you can do is to use wubi, virtual box or the live cd

---

### Post by Herman on 2009-04-15
I do it the same way as oldos2er, (above), but I install GRUB to the first sector of the Ubuntu partition by selecting 'advanced' in step7 of 7 of the installation, and then selecting which partition I want GRUB installed to. A good installation how-to should explain the details of how to do that. You can install GRUB to MBR in an external USB drive in the same manner.]

If someone is installing in a desktop computer, a 'Dedicated GRUB Partition is the multiple-booter's best freind, [How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_").
Or try GAG Boot Manager, [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm").

Regards, Herman :)

---

