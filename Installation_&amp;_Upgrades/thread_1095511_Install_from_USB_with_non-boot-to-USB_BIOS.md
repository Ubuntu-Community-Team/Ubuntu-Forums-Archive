---
title: "Install from USB with non-boot-to-USB BIOS?"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by nonconventional on 2009-03-13
I have an 8.04 Ubuntu liveCD and an 8.10 liveUSB, and want to install on an older laptop that has no BIOS option to boot from USB.
What methods can I use to run the 8.10 installer without
a) wasting another CD, and
b) wasting time because CD drives are much slower than USB and I'm trying to be impressive with my marketing (I got permission to do this install as a partial result of doing an install for someone else)
?

I am not sure at this time whether the laptop has a floppy drive; I will post it later if it would still be relevant.
My thoughts:
*Can the  LiveCD boot another kernel? I know System rescue CD has an option for that, but I only have that on a USB drive.
*If there's a floppy disk, can GRUB on floppy boot from USB?
*Do some partitioning from the liveCD (there is information on the hard drive that is wanted to be kept) and then install something (GRUB, if no floppy) to the hard drive that might allow me to boot to USB.
*Run the LiveCD, mount the image from casper/filesystem.squashfs, and chroot (if necessary) and run the installer. (Would I need to mount --bind the squashfs's kernel and initrd to boot to satisfy the symlinks?)
*If all else fails, install 8.04 and then upgrade. Will an installed environment allow itself to upgrade from USB? I will be doing this in a place with non-free Internet access.

Thanks.

---

### Post by upchucky on 2009-03-13
yes to all. look up knoppix 5.3.1 or earlier

knoppix has tools to work around cd, usb, floppy, network issues, however download everything you need in advance since a internet install takes a long time.

---

### Post by nonconventional on 2009-03-13
There is no floppy drive. However, there will also be another, newer laptop with which I could swap the hard drive, assuming it's still IDE. Is there anything to watch out for with this as long as I haven't installed any hardware (particularly, video) drivers manually?

I suppose I should clarify. Not just "which methods can I use" but how do I use them, if I have to?
upchucky: your response was not useful. I can't boot from USB and don't want to burn another CD. Nor do I want to install Knoppix, since I can't support what I haven't used myself. (Although, I do know someone who might have a Knoppix disk available, if there is something that can't be done from Ubuntu. I am providing many possibilities, only one need work in detail.)

---

### Post by upchucky on 2009-03-14
no need to install knoppix at all it is a live cd with many tools to do the funky things any admin may want to do, it lets you create ways of doing things to get any pc configured for any os.

But you do have to download and create the live cd. no offence meant, but if you have limited resources to accomplish this, then either yourself or someone has set you up to fail, prove them wrong :)

installing on a hard drive of another pc then switching the drive will work as long as the other pc is identical, each ubuntu install is custom built for the pc it is on, that is one if the reasons knoppix was invented, combined with a few other tools it is a way to customize a install for any pc setup. if the other pc is not identical, then you can edit all the files needed to make it work on the desired pc, however you are getting into a bigger mess. this is not to say it will not work, but means it is a lot of extra work when this path has already been done and knoppix is the solution that is faster and easier. Any other than "out of the box" standard graphics setup is only done when the installed os is up and running properly.

if you understand the way it works you do not even need a hard drive to have a working linux pc. I have a complete linux usb thumb drive that I can plug into any usb drive and work as if I'm on my own machine at home, without even booting the host machine's drive, and I can also work on the host's drive whether it is booted or not.

even though you cant boot from usb, u can still use the usb to install ubuntu, knoppix lets you do this, it even lets you use a usb floppy adapter to do the deed. 

since this is on an older pc, and the specs are unknown, check to see if ubuntu is too much moxy for the machine, perhaps Pupppy linux would be more impressive? nothing like a 40 meg operating system complete with tinyoffice, and a web browser to make someone go WoW.

I wish you luck, and if you are determined to get this done, then you do have a lot of reading to do. it is impossible to hold anyones hand through such a project in a forum, any nerd such as myself needs to be in front of the actual system to be of any help.

---

### Post by nonconventional on 2009-03-17
Well, I ended up avoided the issue, as that first laptop had only 128 MB RAM, and I'm not sure what speed processor, by installing on a newer laptop that both had USB boot and 256 MB RAM. I know this is minimal, but, oddly enough, it has a 2.8 GHz processor, so it is worth upgrading. I think the previous owner might have removed some RAM before giving it on; I've never seen those number paired. Of course, the processor speed could be lying.

I had issues getting the graphical installer to run on only 256, so I booted to a command-line from my SysResCD jump drive, and ran fdisk and then mkswap. After that, the install ran just fine.

Relating to the original question, I did discover that GRUB will boot from USB (although, I don't know whether or not that is dependent on BIOS support), and the normal find /casper/vmlinuz would give the correct device name. I'm not sure whether the CD's boot loader has the same capabilities, I only know that pressing escape will return to a text boot loader, which is easier that editing the command line by pressing F6.

---

