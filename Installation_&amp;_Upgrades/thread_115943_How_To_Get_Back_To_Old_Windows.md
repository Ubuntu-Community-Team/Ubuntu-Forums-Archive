---
title: "How To Get Back To Old Windows"
date: 2006-01-11
forum: Installation &amp; Upgrades
---

### Post by Autolycus on 2006-01-11
I have tried to install Ubuntu 5 or 6 times...always "Error 18"  So I want to go back to my old Windows....How in the heck does one reformat the drive from the Windows setup cd when there is no longer a "c" drive?

---

### Post by Kipper on 2006-01-11
If you want to reinstall Windows after a failed Ubunutu install which grabbed the entire disk, the WinXP setup should allow you just to re-partition and format as you wish. 

You will have to create partitions on your hard drive that WinXp understands. WinXP is stupid, Linux is smart it can understand a variety of filesystems. Your Ubuntu install turned all partitions into something Linux understands, namely ext3, by default.

This "error 18" is cropping up a few times here. Looks like Ubunutu installs OK, but the bootloader GRUB does not or has a problem, hence you end up with an unsuable system.

If you use the "linux-expert" install you get a choice to use an alternative bootloalder called "lilo" or to put GRUB on a floppy disk, which might get you past this block. It would be a pity to give up on Linux without ever using it.

---

### Post by Autolycus on 2006-01-11
OK ...I'll give it another try...

I have put in the ubuntu install disc...I am at the first screen....Where do I choose 'Expert install'?

---

### Post by Autolycus on 2006-01-11
Found expert...will keep you posted....I may have to repartition....if I can figure that out....I'll be back..

---

### Post by brargh on 2006-01-11
error 18 sounds like the one I had untill I decided to put my Kubuntu slice within the first 18 Gig of my harddisk....installation went fine just couldn't boot after installing.

To get GRUB out of MBR (if you really must ;) ) you can use the "recovery mode"  after booting off the windows CD/DVD - a dos bootdisk will also work; use the command "FDISK /MBR"

succes!

---

### Post by Sef on 2006-01-11
Here is a fix for GRUB error 18 from Gentoo documents:

> 6. Grub Error 18

Situation

Code Listing 6.1: Grub Output

kernel (hd1,4)/bzImage root=/dev/hdb7

Error 18: Selected cylinder exceeds max supported by BIOS

Solution

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 

Try an update for your BIOS and/or move your boot partition to the front (or at least into the appropriate range).

Link: [http://www.gentoo.org/doc/en/grub-error-guide.xml]("http://www.gentoo.org/doc/en/grub-error-guide.xml")

From what is the error is I would suspect that, most likely, you installed a bigger hard disk on your computer.  One solution would be to update the BIOS.  To do that see which BIOS shows up when you turn on yor computer.  To find the website, just google the BIOS that you see and update.  You would need the Breezy Live CD to do it.   Updating your BIOS can render your operating system unusuable with the need to reinstall it.  Possibly, if you had a boot disk, you could reinstall the boot master without having to reinstall your opperating system.

---

### Post by Autolycus on 2006-01-11
If updating the bios does not work how does one change the partitioning so that boot is at the beginning in a small area...(in plain english, please)

---

### Post by Kipper on 2006-01-11
You know if there was a miss match between your BIOS and the hard drive you have installed, surely Windows wouldn't be able to read the whole thing. 

I would only attempt a BIOS update as a last resort. Make a mistake, and you have to buy yourself a new m/baord, or at least get the BIOS chip re-programed.

Somehow, I don't think this is the source of your Error 18. Somebody else with an Error 18 gave up on Ubuntu and installed FC4 instead, it worked. This might suggest there is a fault in the Unbuntu install or GRUB.

I really would give the "expert install" a go, but you might need to ensure you type in a root password as well as create normal user to get the bootloader stage of the install to function correctly.

---

### Post by Autolycus on 2006-01-11
OK...Installed with expert (the system clock is not correct, but I am sure I can fix it later?) and installed LILO to boot from...(I did not see any choice to create a GRUB floppy)

Restarted computer....booted ok...computer is now "Installing packages."  I guess it does this the first time after installing....

will keep you posted....

BTW: thanks so much for your help..

Ken

---

### Post by Kipper on 2006-01-11
Success, great. Sorry, I wasn't very clear about the GRUB boot floppy, it was under the GRUB bootloader option, you just enter /dev/df0 - disk in floppy of course.

Anyway, glad to have got you going at last. I'm begining to suspect a GRUB bug is possible.

---

### Post by Autolycus on 2006-01-11
Thanks...

Everything is as it is on the LIVE CD....

If GRUB is the default, will I run into any problems with LILO?


Ken

---

### Post by jerrykenny on 2006-01-11
Autolysis, what size hard drive r u installing on ?

Iff you're intending to dual-boot, then its best to install windows first . . . 

Sounds like your bios is restricting your bootloader to <7GB, so install windows on a 6.5 GB Primary Partition. . .  .and It has to be the first partition,

Grub will probably be better inasmuch as when synaptic upgrades your kernel, you have to manually update the Lilo bootloader

sudo   /sbin lilo

---

### Post by Autolycus on 2006-01-11
I have a 20GB hard drive...

I don't desire to dual-boot...

Is there a way, via the LIVE CD, for me to install GRUB now that everything is running alright?

---

### Post by jerrykenny on 2006-01-11
Are you using the live CD ?   I reckon you can do it from within the installed Ubuntu, by going into Synaptic, completely removing lilo, then installing Grub.

Sounds like you've already installed, but an ideal partitioning scenario for you might be

Partition 1 (Primary)  100mb   /boot  ext2
Partition 2 (Primary)  300mb  swap  swap
Partition 3 (Primary) rest-of-drive  /  ext3

Any more complex partitioning will make you more and more tight for diskspace. . . 

Remember in future, before you do any upgrades, backup your /home directory, (where all your files are)

---

### Post by Autolycus on 2006-01-11
No I'm not using the LIVE CD....I have Ubuntu installed and running on the hard drive....Where can I go to see within the program (menus, etc) exactly what sizes my partitions are?

---

### Post by jerrykenny on 2006-01-11
System > Administration>Disks

Be very carefull with the above . . . . . 

if you dont have that facility, try Terminal, and type  df then hit enter.

df gives you the lowdown on your disk usage

---

