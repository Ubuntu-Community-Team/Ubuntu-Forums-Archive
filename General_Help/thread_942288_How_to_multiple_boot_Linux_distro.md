---
title: "How to multiple boot Linux distro"
date: 2008-10-09
forum: General Help
---

### Post by davidw89 on 2008-10-09
i currently have windows and ubuntu in a dual boot configuration thanks to grub.

I would like to try fedora, SUSE and gOS (making a bootable USB, like how you would boot a CD normally). How do i go about installing these for GRUB? Like how i normally install with Ubuntu?

---

### Post by Herman on 2008-10-09
Most other Linux distros use GRUB, but some use LiLo instead.
When you install each new operating system, they should set themselves up automatically to include all the operating systems currently on the hard disk in the new boot loader menu.
They normally will all install GRUB to MBR in your first hard disk for you.

It's okay to leave it like that for a while, so if you're only trying out the other operating systems briefly, you don't need to do anything.

If you will be keeping these operating systems for some time, it is likely that sooner or later each operating system will have kernel updates. When that happens you should really update the GRUB menu you use to boot with the latest kernel for each operating system.
That can get to be a lot of work. 
To avoid doing all that work, you can change from direct kernel boot entries to either configfile boot stanzas or chainloader boot stanzas and install GRUB to the boot sector of each operating system's partition.
[Operating System Entries for Multiple Booting More Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems").
You can't use the configfile command if the ther distro boots with LiLo, but you can use the chainloader command.
You can use the chainloader command for any other operating system, but you need to install a boot loader to the boot sector for it to work.

Regards, Herman :)

---

### Post by jespdj on 2008-10-09
A great way to try out different Linux distros or other operating systems is by installing them in a virtual machine, for example using [VirtualBox](http://virtualbox.org/).

That way, you don't have to mess with the partitions on your harddisk, it's easy to make snapshots etc.

---

