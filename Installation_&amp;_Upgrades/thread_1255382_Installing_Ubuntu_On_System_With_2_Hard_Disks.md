---
title: "Installing Ubuntu On System With 2 Hard Disks"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by san65 on 2009-09-01
[SIZE=2]Hi all,[/SIZE]
 
[SIZE=2]This is my first foray in the Linux environment, so I am looking for guidance from all the masters... here goes...[/SIZE]
 
[SIZE=2]My machine has two physical hard disks. CompMgmt.msc gives the following information: [/SIZE]

[SIZE=2]- Disk 0 is basic disk, with Primary Partition C: and 2 logical drives D: and E:; all NTFS. [/SIZE]

[SIZE=2]- Disk 1 is dynamic disk, with Simple Volume G:, and a lot of unallocated space. [/SIZE]

[SIZE=2](F: is DVD Drive.) [/SIZE]

[SIZE=2]C: has WinXP while D: has Win Server 2008. Which means that I already have dual booting; when the system comes up, it asks me to choose between these two.[/SIZE]
 

[SIZE=2]I have just now downloaded an ISO image and burned it on CD. My questions are - [/SIZE]
 
[SIZE=2]1. whether I can install Ubuntu on the unallocated portion of the dynamic disk (Disk 1)? Or whether Ubuntu insists that it has to sit on the Primary partition C: ? If so, whether I can change the primary partition (basic disk) size without disturbing the existing WinXP in any way? (I would hate to have to reinstall XP all over again!)[/SIZE]
 
[SIZE=2]2. Since there is already some program that is handling the dual booting functionality, whether the inbuilt program that comes with Ubuntu (I think it is called Grub or Lilo) will have any issues with this program? Or whether they can co-exist peacefully?[/SIZE]
 
[SIZE=2]I want to be abs sure before proceeding with the installation! :D[/SIZE]
 
[SIZE=2]Thanks in advance for your time... much appreciated![/SIZE]

---

### Post by oldos2er on 2009-09-01
Ubuntu will work just fine from either a primary or extended logical partition. You probably will want to install it to a logical partition, so your drive letters won't change (if I'm remembering my DOS/Win history correctly).

 Ubuntu will install grub, which should find your Win* partitions and add them to its boot menu. If it doesn't for some reason, it's not too difficult to edit grub's menu post-installation, and add the OSes you want.

 Backup any sensitive data first, and you should be ok.

 Here's more info: [https://help.ubuntu.com/9.04/switching/index.html](https://help.ubuntu.com/9.04/switching/index.html)

[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

---

### Post by san65 on 2009-09-01
[SIZE=2][FONT=Verdana]Hello oldOs2er,[/FONT][/SIZE]
 
[SIZE=2][FONT=Verdana]Thank you for your reply. [/FONT][/SIZE]
 
[SIZE=2][FONT=Verdana]By "extended logical partition", you mean the unallocated space on the dynamic disk Disk 1? [/FONT][/SIZE]

---

### Post by oldos2er on 2009-09-02
Yes, if you use manual installation you can create partitions from the unallocated space. See [https://help.ubuntu.com/9.04/installation-guide/i386/module-details.html#di-partition](https://help.ubuntu.com/9.04/installation-guide/i386/module-details.html#di-partition) , scroll down to the Manual Partitioning Section.

---

### Post by stlsaint on 2009-09-02
a key factor here is to ensure that you DO NOT choose the option to install ubuntu "to the entire disk" at the partition menu during install because ubuntu will do just that and will overwrite your other partitions. select the manual option and setup the partitions you want from there. Also you are in a very delicate sisutation right now with the rig you have and with you being very new to linux...its a easy process but can go wrong quickly and with your setup you dont want to lose much at this point. DO LOTS OF research before you go installing things. you can see my signature below for a good starting point for learning jaunty(if thats what you choosen) and GRUB.

WELCOME TO UBUNTU

---

### Post by san65 on 2009-09-03
[SIZE=2][FONT=Verdana]Hello oldos2er,

Thank you for your advice, really appreciate it.

Hello stlsaint,

You hit it right on the head when you said that I don't want to lose my rig which is already complicated as it is! :D That is the reason for the triple-precaution; asking and reconfirming everything before proceeding. Thank you also for the excellent link about Ubuntu:Jaunty. The information to be sifted through is rather overwhelming!

Right at this moment, I am on my nth iteration of downloading... the checksum fails to match!!! Hopefully, after I have succeeded in downloading the ISO file, I will have something to report.

[/FONT][/SIZE]

---

### Post by san65 on 2009-09-10
[SIZE=2]Hi all,[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]After successfully downloading an .iso copy whose checksum matches correctly, I burnt it to a DVD, and did a checksum verification of the copy on the DVD also. My next problem is that the system is not booting with the DVD![/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]The system bios has been set to boot from DVD drive first. When I boot the system with an XP OS CD, it boots correctly. But when the Ubuntu DVD is inserted, the system bypasses to boot from the hard disk.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Should the iso file be unzipped and then the unzipped material be burnt to the DVD, in order for the booting to happen? [/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Looking forward to your guidance, thanks in advance... :)[/SIZE]

---

### Post by Vector_Matt on 2009-09-10
> **san65 said:**
> [SIZE=2]Should the iso file be unzipped and then the unzipped material be burnt to the DVD, in order for the booting to happen?[/SIZE]Not quite. [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
I recommend isorecorder as it's pretty simple, just make sure to set the burn speed to the lowest setting to help prevent write errors. (though I may just be paranoid about that.)

Edit: Infrarecorder (see post after this) would probably work to.

---

### Post by presence1960 on 2009-09-10
> **san65 said:**
> [SIZE=2]Hi all,[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]After successfully downloading an .iso copy whose checksum matches correctly, I burnt it to a DVD, and did a checksum verification of the copy on the DVD also. My next problem is that the system is not booting with the DVD![/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]The system bios has been set to boot from DVD drive first. When I boot the system with an XP OS CD, it boots correctly. But when the Ubuntu DVD is inserted, the system bypasses to boot from the hard disk.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Should the iso file be unzipped and then the unzipped material be burnt to the DVD, in order for the booting to happen? [/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Looking forward to your guidance, thanks in advance... :)[/SIZE]

No that is not the way to burn it. you need to use burning software which can burn the iso as an image to the DVD-R. if you aren't sure how to do it or if your burning sofware will do that see [here]("https://help.ubuntu.com/9.04/switching/installing-burning.html"). Download infrarecorder and use that. burn it at the slowest possible speed (4x-8x is good)

---

### Post by san65 on 2009-09-10
[SIZE=2]Hello Vector_Matt, presence1960,[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Yes, you are right. InraRecorder did the job well! :)[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Thank you very much... appreciate it! :)[/SIZE]

---

