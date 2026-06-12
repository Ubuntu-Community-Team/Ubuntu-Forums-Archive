---
title: "Secondary ATA problems"
date: 2005-01-18
forum: Hardware &amp; Laptops
---

### Post by clarke.rainey on 2005-01-18
I have just installed the newest version of Ubuntu on an Asus k8V-SE Deluxe... I have it running on and HD which is on the primary HD channel... I also have a SATA/ATA controller located at the bottom of the board that is a PROMISE PDC20378 controller...

The problem is that it shows up under the "Device Manager" in Ubuntu but the two drives attached to it do not... the are not configured in RAID... and the main system bios has that Promise controller configured to run as a standard ATA through the single ATA port that is provided with the two SATA ports... 

I am new to linux but I do know a little... I have found some drivers for debian for the controller but they are made for the RAID operation, also they are dated as compatible with the 2.4.X kernel... so I am guessing that they are a little old...

I have looked in the /dev/ folder and the only hd is hda which has three partitions and my DVD+-RW which is hdc... I cannot find any mention of any sd disks as I have read theya re normally listed when they are run through an onboard SATA controller...

Any help that could be provided would be greatly appreciated... you can of course reach me here by replying but you can also reach me by ICQ:8586226, AIM:Theos ek, or email: clarke.rainey(at)gmail(dot)com... thanks alot for any help...

oh and I need the keep the data on those two drives intact...

---

### Post by clarke.rainey on 2005-01-19
Well I tried hooking them up one by one as a slave to my primary ATA channel and all the drives worked... which now has me even more confused...

---

