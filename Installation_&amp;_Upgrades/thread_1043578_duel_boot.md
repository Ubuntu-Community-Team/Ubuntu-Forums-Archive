---
title: "duel boot"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by shrekfx on 2009-01-18
I'm going to be well more then duel booting.. Windows, ubuntu and more distros.. When i install ubuntu should i do all the partitions then or just keep partitioning when i install the other distros?

---

### Post by mlentink on 2009-01-18
How many disks do you plan to use?
Basically there is only a limit of 4 primary partitions per disk, and obviously many, many logical partitions.
But each OS demands it own minimum of space. So there are practical limits to ponder.

Perhaps you could explain more about what you want to achieve?

---

### Post by shrekfx on 2009-01-18
Mainly i want xp, ubuntu, opensuse, and posibly fedora but i hear its not really good for beginers

---

### Post by Herman on 2009-01-18
I don't really think it matters whether you decide to make all your partitions first or make them as you go. Just remember you need to make an extended partition before you run out of primary partitions, (4).
If you make a primary partition for Windows, you can make an extended partition anytime after that. Linux can be installed in a primary or a logical partition, it doesn't matter.

A 'Dedicated GRUB Partition' might be helpful if you want to multi-boot, but that's entirely optional. The alternative is to keep one operating system as the main one, and use it's boot loader as the boot manager. To do that, you will need to keep re-installing it to MBR if another one overwrites the MBR. You should be able to install each distro's boot loader to the partition boot sector of the partition each operating system is in rather than to MBR.  Then you can use chainloader commands in your main GRUB to boot the boot loader for each one. That allows each of your other operating systems to boot by their own boot loaders, which is the best way to set up a multi-boot.

Regards, Herman :)

---

### Post by shrekfx on 2009-01-18
wow, this is confusing. hehehe but willing to learn.

---

### Post by shrekfx on 2009-01-18
another question with the duel boot.. I got ubuntu and windows now on the computer ubuntu is my main, but when i first started the first time I had 2 diff boots for ubuntu, the main and the safe one i think, now i have 4, which is 2 mains and 2 safes... ???

---

### Post by Herman on 2009-01-18
> another question with the duel boot.. I got ubuntu and windows now on the computer ubuntu is my main, but when i first started the first time I had 2 diff boots for ubuntu, the main and the safe one i think, now i have 4, which is 2 mains and 2 safes... ???  Yeah, that's perfectly normal, and happens to all of us. 
It's a feature of GRUB.
The Linux kernel developers are hard workers, and they often make new kernels for us to support new kinds of hardware and software, and sometimes fix potential security issues. 
Every time we are given a newer kernel in an on-line update, automatic scrips are run to update our GRUB menus.
Just in case a new kernel might not suit our systems, the new kernel is added to the top of the list, and if it doesn't work or if something goes wrong, we can always reboot and just scroll down the list and boot with an older kernel that we know will work for us.

That's one of the main reasons why it's best to use the chainloader command to boot other operating systems boot loaders instead of booting their kernels directly, when we're multi-booting. Each other operating system can take care of updating it's own kernels list, (if it has one). :)

The other reason is, there are starting to be a few variations of GRUB. Some operating systems use GRUB with gfxboot (fancy graphics capabilties), you probably can't boot OpenSuse with Ubuntu's GRUB without disabling the gfxboot commands.
Some GRUBs are able to handle the uuid command, others not. You might not be able to boot Ubuntu with some other operating system's GRUB anymore, because it might not know what to do with  our GRUB's uuid command. 
But if you use the chainlaoder command for booting each operating system by it's partition boot sector, it's nice and simple. it doesn't matter then if the other operating system even uses GRUB. It might use LiLo instead, or Windows NTLDR, or syslinux, etc.

Here's a link about chainloader boot entries for multibooting, [chainloader boot entry]("http://users.bigpond.net.au/hermanzone/p15.htm#2._Chainloader")  

It's quite simple once you give it a try. There are lots of people here who will be able to help you with it too. :)

---

