---
title: "HD Problems with Install"
date: 2005-06-28
forum: Hardware &amp; Laptops
---

### Post by ano1 on 2005-06-28
Hello All,

I recently wiped my HD so I could re-install my OS. I originally was going to have an XP/Ubuntu dual boot. However after XP setup gave me problems I decided to scrap it and just use linux. The XP errors also lead me to believe I might have HD errors.

After all of this I installed Ubuntu, however when my computer boots to the HD it goes for about 2 seconds and then reboots. A friend suggested I do a low level format using the diagnostic tool from my HD manufacturer, and see if I have any problems with that. I have tried to do so but the error I get from the Diag tool leads me to believe my HD is dieing. 

I am presently using the Ubuntu liveCD and the computer seems to be working fine for me (minus no HD access). I was wondering what you all would suggest I do to repair my computer? If I need to get a new HD I can but I would like to be sure this is the problem 1st. Might it just be a GRUB problem that is not allowing me to boot? How would I go about mounting my HD from my LiveCD to be able to test it?

Thanks a million for all your help.

---

### Post by tonym on 2005-06-30
After booking the live CD use alt/F2 to get a console.

Partition the disk using cfdisk and create a single partition,  presumably /dev/hda1.

Try formatting the partition with

mke2fs -ccvj

The "cc" invokes write checking of the partition and should find any faults.

---

### Post by ano1 on 2005-06-30
Hi,

Thanks for the info. When I Cfdisk it tells me I have read only permissions (to dev/hda). How do I mount hda1 from the LiveCD so that I can run Cfdisk and mke2fs? I tried sudo mount /dev/hda1 /media/hda1 after I created the dir /media/hda1. However  it asks for the file system type. Your help is greatly appreciated.

---

### Post by ano1 on 2005-06-30
Update: I have reposted my follow up question in the LiveCD forum section, as it is more of a LiveCD question than a hardware one. Those who wish to reply please visit: [http://ubuntuforums.org/showthread.php?p=236488](http://ubuntuforums.org/showthread.php?p=236488)  thanks to you all for your help.

---

### Post by tonym on 2005-07-02
You can't mount it until you have formatted it.

Try running cfdisk and mke2fs with sudo.

---

