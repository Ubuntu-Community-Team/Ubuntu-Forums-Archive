---
title: "Help Needed With Dual Boot Setup"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by Russell_S on 2009-06-03
Hi, this is my first post and am very new to this. I have spent most of the day Googling and reformatting to try and sort my own problem out but I appear to have failed which is why I'm now posting here.

Firstly some background. I have a Dell D600 laptop with a 40gb HDD and Windows XP installed and working. I decided to try Ubuntu 9.04 and went through the install routine and had it shrink my Windows partition down to free up some space for Ubuntu. This worked absolutely fine and I could dual boot into either operating system with no issues. I was starting to enjoy using Ubuntu and was learning a lot about installing packages and configuring the system which is where I've always come unstuck before.

At this point I decided that I would keep Ubuntu on the laptop but was restricted by the 40gb drive. So, I got a new 160gb drive so that I would still have plenty of space for Windows but also be able to use Ubuntu productively. Firstly I tried using Symantec Ghost to clone the old drive to the new one and resizing the partitions at the same time. This didn't work correctly as when I rebooted I just got the screen filled with "GRUB" constantly scrolling. However, after fixing the MBR I could then boot into Windows fine but obviously Ubuntu was not available. I've since found out that Ghost is known not to work well with Linux so I abandoned this approach.

I then decided to try just re-installing Ubuntu onto the new HDD. I booted of the live CD and deleted all the partitions except the Windows one. I then re-installed Ubunto telling it that I wanted Ubuntu & Windows side by side. This seemed to go fine until I rebooted and then I got a "GRUB error 18"

Now I have tried using "CloneZilla" to clone the old disk onto the new one without resizing the partitions as a test as I thought I could use "GParted" to resize them afterwards to my requirements. This again appeared to work fine until I rebooted. Now it doesn't bring up the boot menu and just presents me with a GRUB> command prompt. If I enter the following commands I can boot int Windows ok:

GRUB> root (hd0,0)
GRUB> makeactive
GRUB> chainloader +1
GRUB> boot

This will boot into windows fine. However I've followed lots of advice on commands to enter to boot into Ubuntu but none seem to work. I've connected the old disk up and booted from the liveCD and checked both hard disks and the menu.lst file is present in both and the contents are the same. So I don't know why the boot menu doesn't appear.

This is the disk structure as reported by GParted:

/dev/hda1 . . . . . . fat32
/dev/hda2 . . . . . . extended
   . . /dev/hda5 . . . . ext3
   . . /dev/hda6 . . . . linux swap


I've tried following the advice here [http://users.bigpond.net.au/hermanzone/p15.htm#Find_out_which_partition_is_your__or](http://users.bigpond.net.au/hermanzone/p15.htm#Find_out_which_partition_is_your__or)
but when I enter the command "GRUB> find /sbin/init" it just returns "error 15: File not found". However, I know the file is there because I could see it when I booted from the LiveCD and browsed the disk. I've tried the following commands to boot into Ubuntu but it doesn't recongnise the kernel file as shown.

GRUB> root (hd0,4) . . . . . . . . . . . . . . returns "Filesystem type is ext2fs, partition type 0x83"

GRUB> kernel vmlinuz-2.6.28-11-generic root=/dev/hda5 . . . . . . . . . returns "Error 2: Bad file or directory type"

So, this is where I'm now at. I can still boot into either OS with the old HDD but I'm at a loss now what to do with the new one. Could someone give me some advice about, firstly why the boot menu is not coming up and, secondly what I can do about it and boot into my Ubuntu installation.


Many thanks and sorry for the long post. I just thought it would help to give as much info as possible.


Regards

Russell

---

### Post by logos34 on 2009-06-03
Try reinstalling Grub (not the windows bootloader) to the MBR from the live cd -- see "Restore Grub..." link in my tagline below.  But if even a fresh install of ubuntu didn't get grub right, then it probably won't work

actually sounds like a Bios limitation--maybe flash it if possible wioth update

or check the bios hard disk detect settings

---

### Post by Russell_S on 2009-06-04
Thanks very much for the reply.

I followed your advice and updated the BIOS (it was quite an early version) and followed your tutorial to restore GRUB. Unfortunately, after this it didn't even display the GRUB> command prompt. When booting the following came up:-

> GRUB Loading stage1.5

GRUB Loading, please wait
Error 2...So I gave up on that idea and tried a different approach.

I firstly restored the MBR so that Windows booted normally. I then booted from a GParted LiveCD and deleted all the partitions except the Windows (FAT32) one. I resized the Windows partition to 40gb which was the size of the original HDD. I then created two PRIMARY partitions, one 2gb swap partition at the end of the disk and the other using the remaining disk space between the Windows and swap partitions to create a Primary ext3 partition for Ubuntu.

I then booted the Ubuntu LiveCD and installed as normal but selected manual partitioning and told it to use the two existing primary partitions for Ubuntu & Swap. The install finished and I rebooted. To my amazement the GRUB boot menu came up and I can now boot into either Windows or Ubuntu.

If anyone can explain why this worked whereas all my previous efforts failed I would be very interested. Was it because I used Primary partitions or was this just a red herring and Is there any downside to using this approach. I have to say that although it has been a very frustrating experience, I have learned a lot about Linux filesystems & GRUB that I probably wouldn't have learned had it all gone smoothly in the first place (I've just got to try and regrow my hair now :)).

Anyway, many thanks for your help, I'm sure I'll have more questions in the future.


Regards

Russell

---

### Post by raymondh on 2009-06-04
Hi,

Congratulations on your dual-boot set-up =D>

I was also thinking along the lines as logos34.  I was thinking of the cylinder limit which, in a nutshell; certain vintage BIOS (even updated) can only go as far into the HD to look for an OS or bootloader.  On an old computer, I had about 8GB.  On a 1998 (although updated phoenix BIOS), I could only go about 30 GB. 

I may be wrong and this may have just been a fluke.  Nevertheless, congratulations on your 2-boot set-up and have a fun Ubuntu-ing :)

Regards,

---

### Post by logos34 on 2009-06-04
> **Russell_S said:**
> 
...So I gave up on that idea and tried a different approach.

I firstly restored the MBR so that Windows booted normally. I then booted from a GParted LiveCD and deleted all the partitions except the Windows (FAT32) one. I resized the Windows partition to 40gb which was the size of the original HDD. I then created two PRIMARY partitions, one 2gb swap partition at the end of the disk and the other using the remaining disk space between the Windows and swap partitions to create a Primary ext3 partition for Ubuntu.

I then booted the Ubuntu LiveCD and installed as normal but selected manual partitioning and told it to use the two existing primary partitions for Ubuntu & Swap. The install finished and I rebooted. To my amazement the GRUB boot menu came up and I can now boot into either Windows or Ubuntu.


yeah, pretty odd, because you say you basically tried the same thing earlier 

i.e.:
> I then decided to try just re-installing Ubuntu onto the new HDD. I booted of the live CD and deleted all the partitions except the Windows one. I then re-installed Ubunto telling it that I wanted Ubuntu & Windows side by side. This seemed to go fine until I rebooted and then I got a "GRUB error 18"

I doubt it's related to primary vs. logical...ubuntu boots fine either way...but who knows

---

### Post by Russell_S on 2009-06-04
Yes, very odd indeed. However, I'm sure stranger things have happened. I'm just glad it's now working fine and I learned a few things in the process.


Russell

---

