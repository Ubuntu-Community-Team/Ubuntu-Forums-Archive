---
title: "THe switch vista to Ubuntu and my HDDs"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by Ceahorse on 2009-01-10
Was thinking about making the change from Vista to Ubuntu. I have 2 hdd and a 3rd external that are all in NTFS. there are files on some that i NEED to keep. i have read that its best to convert the hdds to ext2(this might be wrong) but how can i do this without losing any of the file i have. 

ps. ill be formatting away the vista which is on C:/

HDDs are as follows. 1 120G parted into 2 60G NTFS (C: D:) and 1 120 G with one part NTSC (H:)

The externat is a USB 80G NTFS

Any suggests would be great 

THanks.

---

### Post by theozzlives on 2009-01-10
> **Ceahorse said:**
> Was thinking about making the change from Vista to Ubuntu. I have 2 hdd and a 3rd external that are all in NTFS. there are files on some that i NEED to keep. i have read that its best to convert the hdds to ext2(this might be wrong) but how can i do this without losing any of the file i have. 

ps. ill be formatting away the vista which is on C:/

HDDs are as follows. 1 120G parted into 2 60G NTFS (C: D:) and 1 120 G with one part NTSC (H:)

The externat is a USB 80G NTFS

Any suggests would be great 

THanks.

Backup your data first then put it back on after your done. BTW: it's ext3. CDs or DVDs come to mind, or backup your internal HDs to your external, I don't know how much you have.

---

### Post by ajgreeny on 2009-01-10
Why not keep Vista at the moment and dual boot to your choice of OS at boot time?  That way you can keep all the files on your ntfs windows disk or partition, and you will be able to read and write to that partition from Ubuntu, if that is your choice.  Having more than one hard disk is no problem to Ubuntu, and I would suggest that one way to go is to move the files from your H drive to C or D and then use all of drive H for Ubuntu.  When you install you can simply use the option to use all of what Ubuntu will probably see as /dev/sdb, which may mean nothing at the moment, but should become clear when you get to the partitioning bit of the install.  Choose to use all of that disk, and then let the system set everything else up for you, wait for the install to finish, reboot and you should see grub offering you the choice of Vista or Ubuntu

Have a look at these two sites for more detailed info.
[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

When you are comfortable with Ubuntu, then you can think about getting rid of windows if you really want to, but many users simply keep windows, even if like me they never or almost never use it simply as a fallback if Ubuntu ever went wrong and left them high and dry.

Good luck, and welcome to this great forum and community.

---

### Post by Ceahorse on 2009-01-10
between writng and reading a thought of something else that worried me. It my pc is an ACER with some onboard stuff. (vid card) and im worried about drivers for the unboard gear

and thanks for the welcome and the info.

---

### Post by ajgreeny on 2009-01-11
Boot to the live CD and you will get a clue, at the very least, about whether or not your video card will work OK.  Many Acer laptops certainly do; my wife has one running Mint very well, and as long as you don't have the very newest graphics hardware, there is a good chance yours will too.

---

### Post by Ceahorse on 2009-01-12
is Ubuntus MAX reso 600X800?

---

### Post by glotz on 2009-01-12
[QUOTE=Ceahorse]is Ubuntus MAX reso 600X800?[/QUOTE]lol no! See 
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

