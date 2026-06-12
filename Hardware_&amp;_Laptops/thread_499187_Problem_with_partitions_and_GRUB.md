---
title: "Problem with partitions and GRUB"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by weirdchris on 2007-07-12
Okay, so yesterday I decided to fully install Ubuntu from a Live CD.  The idea was to double boot it alongside XP, because I wanted to keep the choice.

I thought it would be easiest to install it onto my 250 GB external HDD.  This worked absolutely fine, and both Xp and Ubuntu booted fine.  The only problem was that I had made the partition for Linux fill the almost my entire drive (140GB or so).  This meant that the space I used to have for music and such was gone, and unaccesible through windows.

I decided to try to rectify the problem my self using Paragon Partition Manager 8.5.  I thought if I reduced the size of the linux partition i could then reformat the empty part and reunite it with the rest of the XP partition.

I did all of this, and PM told me i couldn't merge the two FAT32 partitions.  It think this was because they were not adjacent. 

On top of this the drive was still not registering in my computer, so I chose to activate it.  A dialogue box popped up telling me that activating it might make the OS (in this case XP) "unbootable".  I thought for a while but chose to carry on, which I now know was a mistake.  When I rebooted the system i recieved an error 17 from GRUB, and the system stuck there.  I left it for a while to see if that would change anything, but it made no differnece.

I then chose to reboot using the Live Ubuntu CD, and obviously this worked fine.  I then loaded the GNOME partition manager (another mistake probably) and tried to rectify the problem.  I started by unmounting the "broken", problem causing partition and then deleting, so that it was clear.  I then even tried reuiting it with the Linux partition, but this was also refused by the partition manager.

My system still won't boot either XP or Linux, and i am sitting in a crappy internet cafe praying someone can help. I would be much ablidged.

Please also note, that I am somewhat of a beginner, and (obviously) don't really know what I'm doing.

---

### Post by LaRoza on 2007-07-12
I cannot follow what happened very well, but I get the impression you deleted linux and still have XP.

If you have nothing essential on the computer, you could reinstall XP and then Ubuntu, or just install Ubuntu.

Are the disks readable? If the are, you could use a live disk and copy any essential data onto a flash drive. (Or if you are using a bootable flash drive, or have more than one optical drive, onto another disk)

If you want to fix XP, you could restore the MBR with the Super Grub Disk, see my sig, since I don't know exactly what you did, this will only work if XP is still there.

---

### Post by dannyboy79 on 2007-07-12
well I am not sure what route you want to go but if you merely want to start again because trying to fix a botched install would take me very long to explain and help you through it, so, here are the instructions for uninstalling grub so that you can at least boot into windows, reunite your partitions or do whatever you have to, delete the ubuntu partitions, then when you do the ubuntu install, chose Manual Partitioning and chose what you want. At a min you'll need a / (root) partition, a swap partition, some people like to create a /home partition so that all their preferences are saved and it's easy to backup if your system goes down. I have even read that you can install another debian based distro and chose to reuse your existing /home partition and it'll work fine. so here's what to do:

You need to go into the BIOS and set the CD to be the first device to boot, put the hard drive second. 
Do you have Windows installed already? If so, boot from the WindowsXP CD, enter the recovery console (press R when it asks you whether you want to install windows etc.) When you're at the console, type: 

fixmbr 

and that will remove GRUB from your system. 

If you don't have Windows installed, GRUB will be overwritten as part of the installation IF you want to reinstall Windows.

---

### Post by LaRoza on 2007-07-12
If you do not have the install disk for XP, the Super Grub Disk will do the same thing.

---

### Post by weirdchris on 2007-07-12
You have both ben very helpful cheers.

don't have the XP CD (it was OEM) so i'll try the super grub disk.

---

### Post by LaRoza on 2007-07-12
The super grub disk looks intimidating when you use it, it is all text. However, it explains everything as you go, and you don't need to type anything, just use the arrow keys and enter.

---

### Post by weirdchris on 2007-07-12
well i now have it on a USB pen drive, but i'm not sure how to load it.

can you shed any light on this?

---

### Post by LaRoza on 2007-07-12
You will have to burn it as an ISO, just like the Ubuntu disk. 

You then boot from it, and follow the prompts, and select "Windows" and read the hints.

-EDIT

Which one did you download?

From this list: [http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61)

---

### Post by weirdchris on 2007-07-12
well i did download the USB one at the bottom, because i will have to pay for a CD.  maybe it's worth it :)

can i do anything with the USB?

---

### Post by LaRoza on 2007-07-12
Why pay for a cd?

Well, hold on, the instructions for the usb version are in the tar.

If you don't have Linux near you, download this while you wait so you can extract it:

[http://portableapps.com/apps/utilities](http://portableapps.com/apps/utilities)

Get 7-Zip, this is a portable edition, so you don't need to install it, just extract.

---

### Post by LaRoza on 2007-07-12
Here are the instructions in the USB_README.txt:

> 

1 - Installation of SGD in a USB device from a Linux with grub installed
(En castellano mas abajo)
2 - Installation of SGD in a USB device in a pc without any OS


1 - Installation of SGD in a USB device from a Linux with grub installed


Mount your usb hd 
untar file in your usb hd (or copy contents of it to usb hd)
umount your usb hd 
open grub as root 
device (hd3) /dev/ubb # my usb device in linux is called /dev/ubb 
root (hd3,0) 
setup (hd3) 
quit 
reboot 

2 - Installation of SGD in a USB device in a pc without any OS
Mount your usb hd untar file in your usb hd 
umount your usb hd (or copy contents of it to usb hd)
umount your hd
(Instead of mounting and umounting on linux you can do it on windows)


Set up your bios so that it boots your cdrom and that your usb device
is recognised as the first hard disk (hd0). 
(Usually first IDE or SCSI disk is set by the bios to be hd0)
Boot from cdrom: Super Grub Disk Cdrom

Choose option Restore Grub on MBR automatically.
As your usb hd or pendrive will be recognised as hd0 you'll usb hd
will be prepared to have Grub on it.

Now you can reboot and set the bios so that your usb device
is recognised as the first hard disk (hd0). And in a such a way
that you can boot this usb hd.


(ES)
Instalar SGD en un usb pen desde linux

    * haces el untar del fichero en tu dispositivo usb montado
    * desmontas
    * abres grub como root
    * device (hd3) /dev/ubb # yo tengo asi el usb
    * root (hd3,0)
    * setup (hd3)
    * quit
    * reinicias o usas qemu y ya lo tienes


---

### Post by LaRoza on 2007-07-12
Looks like it will better to use the Ubuntu Live Cd for this, you will be able to untar and such with 7-Zip, but it may not be bootable.

(The CD is so much easier, just burn and boot)

---

### Post by weirdchris on 2007-07-12
but which one of the images to burn?

---

### Post by LaRoza on 2007-07-12
[http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61)

The first or the second one in the Cd section.

You will need to extract them, 7-zip can do it. (I don't think Windows can)

You are using XP, so you don't need the latest, the second will be fine.

---

### Post by weirdchris on 2007-07-12
:D Problem Solved!!!!!!!!

thank you guys so much!

---

### Post by LaRoza on 2007-07-12
You're welcome, I am always happy to help someone.

If you want good live disks, get GParted also. The Super Grub Disk and GParted are essential tools.

---

