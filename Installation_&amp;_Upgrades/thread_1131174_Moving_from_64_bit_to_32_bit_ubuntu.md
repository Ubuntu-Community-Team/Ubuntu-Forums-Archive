---
title: "Moving from 64 bit to 32 bit ubuntu"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by tlxreed on 2009-04-20
Hi all,

I've got Ubuntu 64 bit 8.04 on one partition of my HP laptop. Vista is on another partition and the third one is unused.

I've been real happy with Ubuntu as it seems like I've got everything working that I need for the moment except I am finding there aren't distributions of some software in 64 bit versions.

I'm a bit of a Linux newbie, so to me it seems like installing 32 bit Ubuntu is the way to go. Komposer is the software I want to use, an open source website editor.

I installed 64 bit Ubuntu from Vista using the 'install inside Windows' option. Grub is set up so I can boot from 64 bit or Vista. Works great.

What I'm wondering is what will happen if I run the same installer again? Could I put 32 bit Ubuntu on the third partition and have three boot options in Grub? I don't really care if the 64 bit Ubuntu goes away as long as Vista and 32 bit is booting.

If there's an option so I can run Komposer on this OS without having to do the terminal dance that would be great but so far I haven't been able to figure that one out.

TIA.

---

### Post by -gator- on 2009-04-20
hey 

you should try kubuntu, it has more applications. To modify the boot loader, you can use bootmanager, ... You can also install this applications in ubuntu.

If you don't need the ubuntu 64 bit anymore, you should delete this partition and install ubuntu 32bit via cd, because your grub (bootloader) is on the ubuntu partition (computer wount start up unless with recovery or live cd's). With the installation of ubuntu windows will automaticly put into grub loader. 
If you want the both ubuntu's, install this also with the cd and choise the 3th partition for installation. But this is a bit stupid to run a multiboot with 2 nearly the same systems.

grtz

---

### Post by tlxreed on 2009-04-21
> **-gator- said:**
> hey 

you should try kubuntu, it has more applications. To modify the boot loader, you can use bootmanager, ... You can also install this applications in ubuntu.

If you don't need the ubuntu 64 bit anymore, you should delete this partition and install ubuntu 32bit via cd, because your grub (bootloader) is on the ubuntu partition (computer wount start up unless with recovery or live cd's). With the installation of ubuntu windows will automaticly put into grub loader. 
If you want the both ubuntu's, install this also with the cd and choise the 3th partition for installation. But this is a bit stupid to run a multiboot with 2 nearly the same systems.

grtz

I guess what I don't get is the difference between installing Ubuntu in Windows versus installing while booted from the CD. The first way was pretty easy to do but the description of 'installing inside of Windows' doesn't make sense unless you think of it as just being an install started while booted in Windows instead of some sort of virtual machine.

All I know is that installing from Windows gave me a bootable machine for both OS's. I'm afraid the install while booted from the CD will be more problematic and I will end up with a system that only boots into Ubuntu. The intro screen seemed to want to partition my whole disk. If I go into manual disk setup I'm thinking I won't know how to set up the partitions correctly.

It's okay if 32 bit goes away. I don't really need three bootable partitions. So, best bet is reinstalling over the existing 64 bit OS. Does the partition need to be reformatted?

---

### Post by Dougie187 on 2009-04-21
Ok, so you should be able to install most 32 bit applications by intalling some packager with the 32 bit libraries, I think its called something like ia32libs. Anyways, you can try this out to see if you can get komposer to work in your 64 bit installation. If you can't or you just really really want to get rid of 64 bit ubuntu and move to 32 bit, you should be able to boot into windows, and uninstall ubuntu just like it was a normal windows program from inside add/remove programs.

Then you should be able to reinstall the 32 bit version of ubuntu inside windows again and it will be the same as it was with the 64 bit version.

---

### Post by tlxreed on 2009-04-21
Okay, thanks. That's what I'm doing now.

---

