---
title: "I can't write to my USB Flash drive"
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by Ghuloomo on 2008-02-27
Before I start, I wanna say that I have read all the topics regarding this, and tried everything but it doesn't work!
I have read these topics fully:
				 				[LIST=1]
[*]**[[B]Changing permission way too difficult**]("http://ubuntuforums.org/showthread.php?t=704246&highlight=permission")[/B]
[*]**[Help - Cannot write to usb flash drive]("http://ubuntuforums.org/showthread.php?t=237881")**
[*] 				 				**[[B]Cannot write to USB flash drive**]("http://ubuntuforums.org/showthread.php?t=97353")[/B]
[*]**[How to mount/unmount Windows partitions (FAT) manually, and allow all users to read/write]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite")**[/LIST]I have followed every single solution mentioned on all above's threads, but still can't get it to work. 

I have this 4GB myFlash usb flash, and I want to put movies in it for a friend of mine, but no matter what I do, I don't seem to get writing permission to it.
[CENTER][IMG]http://www.ft-it.com/product/flashdrive/myflash.jpg[/IMG]
[LEFT][B]Some screenshots:
[/B]
[CENTER][IMG]http://i166.photobucket.com/albums/u96/MohamedHusain/Work/Screenshot.png[/IMG]

[IMG]http://i166.photobucket.com/albums/u96/MohamedHusain/Work/Screenshot-1.png[/IMG]
[/CENTER]
[/LEFT]
[/CENTER]

I want to know why is this? Why this happens? I mean I respect the security matters of not giving permissions, but where is the flexibility? Where is the ease of use?
I have spend nearly 5 hours researching for how to **PLUG IN A FLASH, PUT SOMETHING IN IT**, and **UNPLUG IT**! And apparently seems I'm not the only one. Does it really worth it to have a kind of this security that even the owner of the computer has problems breaching it? Why Ubuntu is not taking any steps?

I really hope this will be solved in 8.4..

Now, I'm totally hopeless. Please don't post me solutions already in those topics. If you have something that will **really** work, let's start!

---

### Post by davidbarton on 2008-02-27
Hi Ghuloomo,

What is the output if you go to a terminal and run:
#cat /etc/mtab
#ls -ld /media/SAMOOI
#ls -l /media/SAMOOI

---

### Post by Sef on 2008-02-28
Check the usb key to see if there is a lock/unlock tab on the side.   I had the same problem, and that's what it turned out to be.

---

### Post by Ghuloomo on 2008-03-08
> **davidbarton said:**
> Hi Ghuloomo,

What is the output if you go to a terminal and run:
#cat /etc/mtab
#ls -ld /media/SAMOOI
#ls -l /media/SAMOOI
I can't give you the output as I returned back the flash usb to my friend.

---

### Post by Ghuloomo on 2008-03-08
> **Sef said:**
> Check the usb key to see if there is a lock/unlock tab on the side.   I had the same problem, and that's what it turned out to be.
It has no lock/unlock tab..

---

### Post by eudemus on 2008-03-17
[http://ubuntuforums.org/showthread.php?p=4534923#post4534923](http://ubuntuforums.org/showthread.php?p=4534923#post4534923)

This any good? I have had a day of frustration, but finally got things working.
Hope it works for you. And if not will be interested to hear more ..... tho' no promises, as I'm not the world's greatest techie.

---

### Post by smoka on 2008-03-21
Just had the same problem again myself (it's happened several times now).

Was due to a corrupted file on my USB flash drive.

The quickest way I've found to fix it was to connect it up to one of my WinXP machines and run chkdsk /f on the drive.

Plugged it back into my Ubuntu Machine (Gutsy Gibbon) and it mounted it correctly with read/write instead of just read only as it had been doing.

I'm wondering if anyone has a nice simple solution for a fix without having to depend on a Windows box to fix this problem every time.

---

