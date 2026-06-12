---
title: "Uninstalling &amp; Reinstalling Ubuntu"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by iamonlyamachine on 2009-06-14
Hi all,

I'm a relative newb here. I have a laptop dual-booted with Vista and Kubuntu 8.04. However, I wanted to swap out Kubuntu for Ubuntu, found some directions to do so online without having to uninstall but, unfortunately, it didn't quite work. The Kubuntu splash screen loads, and then it gets to the Ubuntu desktop (I can tell by the wallpaper) but it never finishes loading.

What I would *like* to do is this:
1. Un-install the current installation of Ubuntu 8.04
2. Install Ubuntu 9.04.

This way, I won't have to upgrade to 8.10 and I will also have my current Ubuntu mess worked out.

My only fear is that I might not be able to access Vista after I do this. However, my hope is that, since I will be reinstalling Ubuntu and, thus, the GRUB bootloader, Vista will be reloaded into the bootloader and I will be able to boot into either Vista or Ubuntu just fine.

Will this work? I have everything backed up, but I don't have a Vista disc, so I'd rather not have to go to the trouble of reinstalling Windows on top of all this.

Any advice? Things I should be aware of? Will I have to change the Windows MBR before doing this? I'd prefer to accomplish this with as little headache as possible.

Thanks!

---

### Post by merlinus on 2009-06-14
If you install ubuntu into the same partition as the one you are using, then it will recognize windows and add it to the boot menu.

---

### Post by lisati on 2009-06-14
Perhaps the easiest, assuming you're not using Wubi, is to tell the installer to write over the top of the existing installation. Don't forget to make backups first......

---

### Post by Amilo1718 on 2009-06-14
are your partitions only on a sofwtare basis?

---

### Post by iamonlyamachine on 2009-06-14
> **lisati said:**
> Perhaps the easiest, assuming you're not using Wubi, is to tell the installer to write over the top of the existing installation. Don't forget to make backups first......

This is exactly what I want to do. As Merlin said, I want to write the new Ubuntu install over the old (K)ubuntu install, using the same partition.

There are physical partitions and not software partitions.

Through the GUI installation menus, when I get to the step to set up the partitions, I am asked if I want to manually set up the partitions or set them up side by side.

I don't want to set them up side by side b/c I don't want the old Ubuntu partition to be using up space since it is no longer needed.

So I get the following options when I click to "Edit" the existing Ubuntu partition:

-Do Not Use Partition
-Use as Ext3: Journaling File System
-Use as Ext4: Journaling File System
-JFS
-XFS
-FAT16
-FAT32
etc.

I assume I want to use it as Ext3 since the current Ubuntu install is installed as ext3. Am I correct? Will this overwrite the current Ubuntu install and install my new Ubuntu install into that partition?

Sorry if I am a little weary on this point but I don't want to proceed without confirmation and thus screw up my Vista installation. Again, everything is backed up, but I don't have a Vista disc (didn't give me one when I bought the laptop) so it's going to be a pain if I have to restore both OS installs.

Thanks for all your help!

---

### Post by merlinus on 2009-06-15
Correct.  Use as ext3, mountpoint /, and format.  But back up any data first, as it will be destroyed.  

ext4 has lots of promise, but if you search through the threads a number of users have experienced major problems with it.

---

