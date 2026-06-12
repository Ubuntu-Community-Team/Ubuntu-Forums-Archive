---
title: "install XP Tablet AFTER Ubuntu"
date: 2006-01-28
forum: Installation &amp; Upgrades
---

### Post by andrewsawyer on 2006-01-28
In the hope that someone can help me with this, I have a question.  I own an Acer Travelmate C110 laptop.  It came with Windows XP Tablet Edition, however unlike normal versions of Windows, this version comes on three CD's + a startup CD, and formats your drive before placing an image of Windows onto your system.  I guess anyone with a Tablet pc will know what I mean.

To give you an example of the CD layout, on disk 2 there is a rcd2.dat file in the root, with a directory called images.  This dir contains 80e46z01.002 (624.6Mb), size.dat (435b), and source.pqi (11.1Mb).  I have established that the pqi extension is used by a program called PowerQuest Drive Imaging Software.

I have Ubuntu already installed, with 8Gb free, un-formatted space, and I wish to put Windows Tablet onto it.  I was to do this without formatting the drive.  Yes I know I can just back up and then reinstall Linux and whatnot, however there is a specific reason that I want to do it this way around.

Is there anyone out there that can help me with this, or is it an impossibility?  Acer Australia say that my warranty is out, so they won't help and it's not something that is covered by them anyway, and Microsoft want $50 just to put me thorugh to a tech support guy, with no guarantee that they will be able to help.

If anyone has any info that I may be able to use, it would be very much appreciated.

Andy

---

### Post by TechSonic on 2006-01-28
Usually you want to install Windows first, then Linux second.  Linux on the first partition, Windows on the second.  Sounds fustrating? NOT AT ALL HAHAHAHA!

No really.  Just install Windows on the second partition, then install Linux on the first partition.  Use Grub, have fun.

And if it's a Tablet, what would the the point?  XP is like, worthless on a tablet, not to mention a tablet is worthless to start off.  But I'm sure you found a use for it, never mind how minimal it's priority is.
8Gigs... Oh boy... Speaking of over populating your hard drive, usually leads to malfuntions and eventuall failure of the device.

---

### Post by andrewsawyer on 2006-01-28
Thank you for the reply, however please note that I can't just instal windows on the second partition as the version of Windows that I have wipes the drive before installing.  This means that as a standard install, when complete my 40Gb hard disk would be formatted to one partition (NTFS) with Windows on it.  Which I really don't want.

Just out of interest, where did you get the idea I was overpopulating my hard drive?  8Gb Linux root, 8Gb Windows, 17Gb /home, 1Gb swap, leaving 6Gb for something I can't really mention due to legal implications, but anyway, the 6Gb 'thing' is already installed, and has to go on first.  I'm therefore trying to get Windows on as a non-standard install - not just recreating the image.

---

### Post by alamba on 2006-01-28
Could installing XP, reducing the partition size with gparted or qtparted and then installing ubuntu be a possible solution? Or do you have to have XP installed second?

Akshay

---

### Post by Titus A Duxass on 2006-01-28
I may be wrong here but if you creat two or three specific partitions format the windows one with NTFS and the others with rieser f, can you not instruct windows to install it on the first partition?  It will think that it is a small drive but should still install.

You may have make a new installation of ubuntu afterwards, but that shouldn't be a problem and practice makes perfect.

---

### Post by andrewsawyer on 2006-01-28
Ok, full detail - to give you all the full picture.  I have OS X installed on partition 1, ubuntu root installed on partition 2, space for Windows on 3, /home on 4, with then a 1Gb swap partition too.

To install OS X, you have to use dd, and so it wipes everything out.  It creates a 6Gb partition, and leaves the rest blank.  So then I created the other partitions in Ubuntu and installed Dapper.  Now I need to stick Windows on, however the version I want to use - the Tablet edition is on 3 cd's as a drive image.  I am trying to extract the files from the drive image onto the blank 'windows' partition.  I don't need the MBR bit as I'll be using GRUB.

Unless there is a way to get dd to not wipe everything else out (and I don't think there is), I've gotta get the Windows image extracted manually.

I hope this clears it up.

---

