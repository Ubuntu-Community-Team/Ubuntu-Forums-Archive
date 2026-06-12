---
title: "grub stopping access to my computer"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by ehababoud on 2009-04-25
hi, a while back i tried to install ubuntu 8.10 because i tried it out from a few friends. the grub installer didn't work so i decided to install via wubi (via windows). and so i've been using ubuntu like this for a while now. a few days ago, as the world and its mother know, that the new ubuntu was released and i wanted to upgrade. now before upgrade i thought i'd kill two birds with on stone (although i'd never hunt birds :P) by transferring my ubuntu installation to an actual partition. after finding a million things to remove so i can make space, i managed to make a copy of my ubuntu installation on a new partition, which was much larger than the wubi installation. after i done that the grub install didn't allow me to access the "new" ubuntu installation and therefore i deleted it by removing new partition i made for it. i later understood that it was a big mistake because now it comes up with grub errors and i can't access any of my OS's on this computer. i'm currently using a live cd to post this, and i was hoping if anyone could help me get access back to my wubi installed ubuntu and possibly move my ubuntu successfully on a partition without the grub killing the computer? 

sorry for the long post but i needed to add as much detail as possible

help would be greatly appreciated

ehab

---

### Post by Bauldronius on 2009-04-25
Hi i had the exact same problem just yesterday and i did everythin "the wrong way" but now i know more so i hope this link helps you [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Big_Croc7 on 2009-04-25
Basically, the things you need to know are the following:

The first part of the boot process involves loading code from the very start of the hard disk, in an area called the master boot record (MBR).  Grub is installed here, but need to look in the installation partition to find its configuration.  It seems like you still have grub installed on the MBR, but no partition for its configuration data.

So, to get back to booting just into Windows, and running Ubuntu through Windows, you'll need a Windows CD to reinstall the Windows bootloader to the MBR.  You can do this by booting from a Windows CD, entering the recovery console, and typing 'fixmbr' (I think, although it might be 'fix mbr' or something, but I think it's 'fixmbr').

I assume you're talking about Windows XP, not Vista, and when you transfered your Wubi installation to the partition you copied it, rather than moving it and deleting it from the Windows partition.

When that's done, you'll be back in the same situation as before, and can follow a guide or ask questions in the forums about how to transfer the Wubi installation to a 'proper' installation (i.e. on its own partition).  (I would recommend starting afresh with a clean install, but that's just my preference.)

Hope that helps - any questions just ask. (If the above procedure doesn't work, you might want to try running 'fixboot c:' or something like that, from the recovery console too, to reset the bit of the bootloader on the Windows partition too, as well as the bit that sits on the MBR.)

---

### Post by Big_Croc7 on 2009-04-25
By the way, the link posted tells you how to restore Grub to the MBR, but this won't actually work if you've deleted the Ubuntu partition (Grub needs its other data files as well as the bit stored on the MBR, and I don't think it can get those from the Windows partition, though I may be wrong).

---

### Post by Bauldronius on 2009-04-25
Just wondering what to do if you don't have windows install cd as is the case with many people running vista these days 
anyhow i was wondering that could you do a new partition with livecd and then install grub in there

---

### Post by Big_Croc7 on 2009-04-26
Yes, that's definitely a possibility. I don't have time to write a guide for it now, but I'm sure there's information out there - let me know if you can't find information on it. It basically involves creating a small partition (even 8 Mb is enough just for Grub) and then running grub-install.

I do this on my testing machine, that way I have a bootloader that is independent from any operating system, so if I want to replace one I just format the OS partition without worrying about harming the bootloader.

---

### Post by ehababoud on 2009-04-27
first of all i'd like to thank everyone for your input i've started to have a greater understanding on what's going on, sorry for late replies - i haven't configured my user profile to email me notifications yet. you were right Big_Croc7 for what you said about the instructions working or not, i tried it and it returned an error called "error 15: file not found".

just a bit curious about what you last mentioned to Bauldronius and if it will work in my case? i'm using a ubuntu 8.10 livecd at the moment i that helps with as additional information. as Bauldronius mentioned i don't have a windows disc because my windows vista pc didn't come with it at the time so i can't execute that command until i am in the windows OS itself. is there anything specific, such as the grub-install feature you mentioned, that i can do in the livecd? 

thanks again

ehababoud

---

### Post by Big_Croc7 on 2009-05-01
Here is a brief guide to the steps needed to create a separate grub partition.

1. Create the partition which will hold the grub files and nothing else (e.g. using GParted). I usually create an ext2 partition of 8Mb right at the end of disk, within an extended partition. I'll assume for the rest of this guide that this partition is labelled sda6. The number will probably be different for your system; also, it may be refered to as hda instead of sda. (This is simply a label - sda (or hda) is the disk, the number after is the partition on that disk.)

2. Mount the partition and install grub:
```

cd /mnt
sudo mkdir bootpart
sudo mount /dev/sda6 bootpart
sudo grub-install --recheck --root-directory=bootpart

```

3. Check that grub's configuration is ok and edit if necessary:
```

sudo nano bootpart/boot/grub/menu.lst

```
Now make sure that you have the entries you need in here, e.g.
```

title Ubuntu
root(hd0,1)
kernel=/boot/vmlinuz
initrd=/boot/initrd
boot

```
You need to change the code in this file to match your system.

I think this should be ok, but I haven't actually run through it - if someone could check it out that would be useful.

---

### Post by ehababoud on 2009-05-01
thanks for that, looks like a great solution, i tried it and everything is great until this stage:
```

ubuntu@ubuntu:/mnt$ sudo grub-install --recheck --root-directory=bootpart
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.


```

i managed to create the partition but ext2 was only allowed to be a primary partition - not an extended partition. dunno if that info helps but i thought i'd mention anyway.

thanks 

ehababoud

---

### Post by Big_Croc7 on 2009-05-15
Sorry, meant to reply earlier. Do you still need help?

Ps. partitions - you can have up to 4 primary partitions on a disk, or 3 primary plus 1 extended. An extended partition contains logical partitions with no effective limit on how many logical ones you have. It doesn't matter if your new ext2 partition is primary or logical, only if you make 4 primary ones then you can't make any more, even if there is space on the disk.

---

### Post by ehababoud on 2009-05-17
hi, yeah its fine i understand that this help is voluntary so i don't mind the late reply.

i thought to myself one day when i was bored that i should just play around with it (seeing as no more damage can be done than what has already happpened lol) so i managed to find a fedora disc then installed that. i don't really like fedora so i downloaded the ubuntu 9.04 distribution and then got the disc. with that i removed the fedora partition then installed 9.04 on the free space i had on the drive. when i done that it overwrote the original grub thing. after that i could even get into my old WUBI distribution and also my windows vista partition.

and may i say, ext4 and 9.04 are so impressive. my computer is only intel core 2 with 1GB ram and 1.5Ghz but it boots in disgustingly quick speeds and i can do everything amazing with it! love it lol.

thanks for your help anyway i have learned a great deal about my computer and how partitions work with linux. thanks to everyone else who have tried to contribute. another [Solved] thread :D

Ehab

---

### Post by Big_Croc7 on 2009-05-20
Great news - glad you got it working!

I haven't tried ext4 yet but I've heard good things about it from others too :-)

---

