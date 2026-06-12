---
title: "UEFI on my Asus X52F"
date: 2012-08-14
forum: Hardware
---

### Post by venky96 on 2012-08-14
I was reviewing my settings in BIOS and UEFI was disabled. I wanted  to check what UEFI was so I googled it. I found out its like an upgrade  to BIOS and improved boot speed. Currently I'm dual booting Ubuntu  12.04(32 bit) and Windows 7(64 bit). I'm currently confused as to how to  make the switch since I don't want to make my System unbootable. How do  I make the switch from BIOS to UEFI. 
  System Chipset : Intel HM55

---

### Post by dandnsmith on 2012-08-15
I'm not entirely sure, but, according to the reading I've done so far (Linux Format magazine and their forums), you don't really want to as you'd need the Ubuntu release to be in the UEFI table of OS allowed to make installations and alterations.

Perhaps someone else can tell you more.

---

### Post by venky96 on 2012-08-15
I honestly don't mind reinstalling my OS's if UEFI is worth the trouble.

---

### Post by drmrgd on 2012-08-15
As UEFI requires a completely different boot manager and a different partitioning scheme, in order to make the switch, you'll have to reformat your drive(s) and re-partition them.  To be honest (and in my opinion), if you have a working system, it's really not worth the effort as I really don't notice a drastically faster boot time on my UEFI computer.  It's probably confounded by the fact that I'm dual booting, and of course, after chainloading boot loaders, if UEFI is really faster to boot, the speed is negated. 

That being said, if you want to go through the effort and mess around with it, we can certainly help.  Forum user oldfred is a master at all things UEFI and dual booting, and will get you set up pretty quickly.  It would be helpful to know how you're currently set up (i.e. how many drives are involved, how you'd prefer to partition, etc).  Out of the box Ubuntu 64-bit (but not 32-bit...take note!) is already set up to appropariately set up the efibootmgr when you install.  So, it'll be a matter of formatting the drive appropriately (you'll need at a minimum to partition in GPT mode, putting a ~200MiB FAT32 partition at the start that is labeled as efi_boot, followed by your standard NTFS partitions for Windows and ext partitions for Linux), and installing the efi version of Grub 2 to the efi_boot partition you set up in order to load Windows and / or Ubuntu.

---

### Post by venky96 on 2012-08-15
I have all the data I need in an external Hard Disk. I actually dont mind doing a full Wipe of the hard disk. I have seen Videos where people just switched from BIOS to UEFI and Installed windows. The windows 7 installer itself did all the required partitioning. What if I install Windows 7 like that and then Install Ubuntu. Would I still have to all the work that you mentioned. And Finally, Is it really worth doing all this? Since Only 64 Bit OS's support UEFI and I have only 2GB DDR3 RAM and I have heard anything less that 4 GB is practically useless.

---

### Post by venky96 on 2012-08-15
Also, In my BIOS it says UEFI is disabled. Would it be as simple as Enabling it or would I have to load a Firmware? Honestly,my PC is running smoothly but I always liked to fiddle around and try something new. But if it is really complicated and if somehow mess up the BIOS then I would just brick my PC and I don't want that happening.

---

### Post by oldfred on 2012-08-15
+1 on drmrgd comments.

With only 2GB of RAM, you will not get a lot of advantage from the 64 bit version and maybe some disadvantage. Using 64 bit is faster as it uses 64 bits for the system but then needs more RAM (not double but more). So you may slow system unless you plan on upgrading memory.

You do have to have the 64 bit version of Ubuntu to use UEFI.

---

### Post by venky96 on 2012-08-15
Alright,So I guess its really not worth using EFI on my desktop. But I'm planning to upgrade my memory sometime soon so I guess I'll do this later. But thank you again :D

---

