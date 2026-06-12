---
title: "Get windows files to ubuntu like my documents and music"
date: 2005-11-25
forum: General Help
---

### Post by Fittersman on 2005-11-25
How do i transfer my windows files from windows to ubuntu. I am using a dual boot system.

---

### Post by aysiu on 2005-11-25
Follow the directions in here:
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

The directions assume your Windows partition is /dev/hda1
To find out what it really is type ```
sudo fdisk -l
``` in a terminal.

To get a terminal, go to Applications > Accessories > Terminal

---

### Post by Fittersman on 2005-11-26
is there  anything for ubuntu 5.10?

---

### Post by aysiu on 2005-11-26
[QUOTE=Fittersman]is there  anything for ubuntu 5.10?[/QUOTE] It's called the 5.04 Guide, but the instructions for mounting Windows partitions applies to 5.10 as well.

---

### Post by Fittersman on 2005-11-26
that thing lost me

what does unmounting and mounting and all that stuff and when i unmount it or mount it or whatever will it just automatically go to ubuntu or what do i need to do to get it there?

---

### Post by dodongo on 2005-11-26
[QUOTE=Fittersman]that thing lost me

what does unmounting and mounting and all that stuff and when i unmount it or mount it or whatever will it just automatically go to ubuntu or what do i need to do to get it there?[/QUOTE]

Think of "mounting" as "make this accessible" -- when you mount a partition or device, you tell the system you want to be able to work with it.  "Unmounting" is just the opposite: "put this away; I don't want to work with it anymore".

Once you've mounted your old Windows partition, you'll be able to access it via Ubuntu.  In GNOME, I think once you've mounted a new device, it should automatically show up on your desktop.

Does that help at all?  Is the terminology just what's tripping you up, or are there other technical difficulties?

---

### Post by dodongo on 2005-11-26
> will it just automatically go to ubuntu or what do i need to do to get it there?

Sorry I didn't address this right out.  Your files from Windows *will not* automatically go to Ubuntu.  You should be able to do what you want with them, though.  If you want to copy them into Ubuntu, you can move things from your My Music folder from Windows into your home folder in Ubuntu.

---

### Post by aysiu on 2005-11-26
[QUOTE=Fittersman]
what does unmounting and mounting and all that stuff and when i unmount it or mount it or whatever will it just automatically go to ubuntu or what do i need to do to get it there?[/QUOTE] Think of mounting a partition as making a "shortcut" to it (or an "alias" in Macspeak). It will appear as a folder you can browse to in Ubuntu, but it's not really a folder--it's a partition.

---

### Post by ngnr on 2005-11-26
Breezy help already have the "Ubuntu 5.10 starter Guide"

System > Help > Ubuntu 5.10 Starter Guide

Look for "Windows Partitions".

Good Look

:)

---

### Post by Fittersman on 2005-11-26
dondogo how do i do that?

---

### Post by dodongo on 2005-11-26
[QUOTE=Fittersman]dondogo how do i do that?[/QUOTE]
I'm going to guess that you're talking about moving your files onto the new Linux partition?  (Or else I'm going to sound afool giving you directions that don't have anything to do with your problem :)  )

Your newly-mounted partition should automagically show up on the desktop -- or in the places menu, probably called something odd like hda2 or hdb3 or something*.  Open it and look for the 'Documents and Settings' folder.  Inside that should be a folder with your Windows user name, and inside that should be 'My Documents'.

You can drag those files and folders into the Linux partition to make a copy of them in Linux.

-----------------
If this is confusing, ignore it.  If it's helpful, great!

* - For reference, the first two letters (i.e., 'hd' or sometimes 'sd') refer to the kind of drive it is and how the computer talks to it.  The next letter (i.e., hd'a' or sd'b') is what "channel" the drive is on.  The number is the order of the partition on that drive.  So for example, most hard drives (c:\ in Windows) are the IDE primary master drive, so they show up as hda{some_number}.

---

### Post by Fittersman on 2005-11-26
it tells me that im not qualified enough or something to do that

---

### Post by aysiu on 2005-11-26
[QUOTE=Fittersman]it tells me that im not qualified enough or something to do that[/QUOTE] Let's take it one step at a time.
First of all, do you know what a terminal is? Open one up: Applications > Accessories > Terminal.
Once the terminal opens up, type in ```
sudo fdisk -l
``` You'll be prompted for your password. Enter it. Then whatever shows up in your terminal, highlight it, copy it, and paste it into a new message in this thread. We'll go from there.

P.S. By the way, the point of this command is to find out the location of the NTFS partition from Ubuntu's perspective. Mine looks like this:

```
sudo fdisk -l
Password:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
**/dev/hda1   *           1        1911    15350076    7  HPFS/NTFS**
/dev/hda2            1912       18494   133202947+   f  W95 Ext'd (LBA)
/dev/hda3           18495       19457     7735297+  83  Linux
/dev/hda5            1912       14763   103233658+   b  W95 FAT32
/dev/hda6   *       14764       16434    13422276   83  Linux
/dev/hda7           18363       18494     1060258+  82  Linux swap / Solaris
/dev/hda8           16435       18362    15486628+  83  Linux

Partition table entries are not in disk order
``` From this, I can see that my NTFS is /dev/hda1. I need you to put the output of the command from your computer, so we can see what yours is called.

---

### Post by Bachstelze on 2005-11-26
wow aysiu, you're very devoted :p

---

### Post by dodongo on 2005-11-27
Thanks, aysiu.  I'll keep monitoring this thread and take notes on how you're working to resolve this.  If I have anything useful to add, I'll chime in.  

The fdisk -l command is new to me, but I've already seen it in a couple threads tonight!  Always so much to learn!

---

### Post by Fittersman on 2005-11-27
ill be able to get you the data you need after i get an internet connection set up because then it will be easier and im not really into writing it out then retyping it. thanks alot though

---

### Post by aysiu on 2005-11-27
[QUOTE=Fittersman]ill be able to get you the data you need after i get an internet connection set up because then it will be easier and im not really into writing it out then retyping it. thanks alot though[/QUOTE] Retyping? You could put the command in the terminal, copy and paste the output into a text file and transfer (via floppy or USB pendrive) that text file to a computer that has an internet connection. Copy and paste. No retyping.

---

### Post by Bachstelze on 2005-11-27
Copy and Paste is the most wonderful invention of mankind :p

---

### Post by anil_robo on 2005-11-27
Interestingly, Ubuntu can use a FAT16/FAT32 windows partition just as it is! I use windows and Ubuntu both, and frequently switch between the two while working on my school projects. I have created a 10GB FAT32 partition in Windows, and have mounted that in Linux. I can open my document from both Windows and Ubuntu, and save/edit/move/copy/paste or whatever without any problems whatsoever!

To make things easier, I have moved everything that I might need in Ubuntu to that partition. For example, movies, music and school projects. Makes life much easier, I do not have to reboot in Windows each time I want to listen to those mp3s.

---

### Post by Fittersman on 2005-11-27
i only have this one computer so that wouldnt work.

(you wouldnt happen to know how to get ubuntu to use my modem. It is listed in ubuntu's device manager but it cant be autodetected so im stumped on that one)

---

