---
title: "[SOLVED] Windows no longer detects second partition"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by Hunsrus on 2009-01-04
Gentlemen,

I completely f*cked up.
Here's the story in short:

I had a dual boot with Windows XP 64-bit and 64-bit Ubuntu. Ubuntu was really just for messing around, but for nothing serious. One day, I screwed up Ubuntu beyond all recognition so I decided to go into windows and delete the whole partition from there. This worked but apparently the bootloader wasn't removed, meaning I was left with an "Error 22" leaving me with no boot whatsoever.

So I decided I'd reinstall Ubuntu. This is where things get messy.

I added the freed space from the Ubuntu to my second partition (Z:\), and after that, during the install, I chose a guided partitioning where Ubuntu resized my Z:\ partition, being careful not to screw things over. The size of the new Ubuntu partition was about the same size of the old one. This technique had worked before without any trouble. I remember going into "Advanced" in the final step of the installation process, to set the boot loader install location to sda5, being my ext3 from what I know.

Now for the trouble: I reboot into Windows without any problems, but it doesn't recognise my Z:\ partition anymore! Just the C:\ partition for booting. I'd be happy to reformat it but there's a lifetime of REAAAAAAAALLY important stuff on there. The funny thing is, it DOES show up in My Computer, and whenever I click it it tells me "The disk in drve Z is not formatted. Do you want to format it now?" with the options to answer yes or no.

I'm sure the data is still intact. The size of the partition should easily contain my data, and I defragmented it before the whole thing, so that all my empty space on the partition was moved to the "back end" of the disk, or the part that linux has taken it's space of. There's GOT to be a way to have windows recognize my disk without formatting it.

Please guys, I'm in a real pickle here, any help would be greatly appreciated.

All the best,

Hunsrus

---

### Post by Herman on 2009-01-04
Okay, firstly, can you 'see' the data in the partition from Ubuntu?

Secondly, can you run the command 'sudo fdisk -lu' to take a look at your partition table please, and copy the results and post them back here,
```
sudo fdisk -lu
```

---

### Post by Herman on 2009-01-04
To 'see' the data from Ubuntu, you just need to click 'Places'-->'Removeable Media'-->', (and pick an icon), if your data partition's file system is okay, and you have a modern version of Ubuntu, it should open it for you and you should be able to 'see' your files.
If you can't find your data that way, (there's no icon for it), don't worry, because maybe you only need to run CHKDSK /R from a Windows Recovery Console on it.

The 'sudo fdisk -lu' command is to see if your partition table is okay, and if so, what partition numbers you have in Linux terms. It also gives the start sectors of each partition.

You can use a Live CD to obtain the information in case your installed Ubuntu doesn't boot, (you said you installed the boot loader to /dev/sda5).

If you need more help, don't be shy to ask questions, I can give more detailed explanations if required.

---

### Post by Hunsrus on 2009-01-05
Hi Herman, thanks so much for your reply.

I've looked in "places" in Ubuntu. The C:\ partition shows up, the Z:\ one does not. After that I took a look at Gparted in ubuntu, I can see the NTFS Z:\ partition in there, however it has a "!" mark next to it. Unfortunately I'm at school at the moment, but I will perform the actions you suggested, and post the requested screenshots as soon as I get home.

The GRUB boot loader works fine by the way, I thought installing it on my Linux partition would be a good idea, thinking that if I just delete the partition I'd delete the Bootloader as well, causing the system to boot directly into windows. Windows is still the system I use most of the time for it runs the applications and games I use at the time, but I'm currently looking into the possibilities to run these apps and/or replacements in Linux.

Anyway, I'll keep you posted. Thanks again!

Hunsrus

---

### Post by Herman on 2009-01-05
> After that I took a look at Gparted in ubuntu, I can see the NTFS Z:\ partition in there, however it has a "!" mark next to it.:D Hey, that sounds like good news! The ! sign (usually in a yellow triangle), means it needs a file system check. That's not so bad. If you read the GParted documentation, they advise a file system check after resizing any NTFS partition. A file system check is a good thing in at any time.
If it was very bad, it would have had a black rectangle around it. I'm optomistic that you'll only need to use your Windows XP "installation Disc', open a [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and run CHKDSK /R on it and it'll be fine.

---

### Post by Hunsrus on 2009-01-05
Good afternoon,

I did as you said, but unfortunately the only thing I got from the CHKDSK /R in the recovery console was in the neighbourhood of "The disk seems to be damaged beyond repair".

Here are the screenshots for fdisk -lu and Gparted:

[IMG]http://img53.imageshack.us/img53/2691/fdiskey9.png[/IMG]

[IMG]http://img378.imageshack.us/img378/6775/gpartedds6.png[/IMG]

[IMG]http://img220.imageshack.us/img220/5660/gpartedinfo2mj1.png[/IMG]

Hope this helps. I'll continue investigating on my own for some more.

Best regards and thanks,

Hunsrus

---

### Post by Hunsrus on 2009-01-05
Never mind, I fixed it.

Here's what I did for those with the same problem:

I downloaded testdisk [http://www.cgsecurity.org/wiki/TestDisk_Download]("http://www.cgsecurity.org/wiki/TestDisk_Download")

---

### Post by Hunsrus on 2009-01-05
Never mind, I fixed it.

Here's what I did for those with the same problem:

I downloaded testdisk at [http://www.cgsecurity.org/wiki/TestDisk_Download]("http://www.cgsecurity.org/wiki/TestDisk_Download"). Man, what a lifesaver.

In testdisk, select your drive, partition table type (usually Intel on PC), then select Advanced, and then select the ****** up partition and select "boot". Give it a minute to search your mft, after that I can't quite remember if you were done already, or you'd had to select some sort of "fix this ************" option, but anyway, you're done. When I selected Z:\ in My computer, I could see and open all my files as before. Apparently this operation is called a "bootfix", where it rewrites your master boot record. Testdisk is available for pretty much every OS out there, so it's possible to run it under liveCD.

Herman, I'd like to thank you for your help and time. The world could use more people like you :D.

All the best,

Hunsrus

---

### Post by Herman on 2009-01-05
:D Okay, you figured it out yourself! Well done and congratulations! Good work! :D

---

