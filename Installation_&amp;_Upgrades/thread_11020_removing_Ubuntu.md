---
title: "removing Ubuntu"
date: 2005-01-13
forum: Installation &amp; Upgrades
---

### Post by philip41 on 2005-01-13
Guys i have now got a second pc with Ubuntu up and running. What i want to do is reclaim the second drive of my main Windows(sorry for swearing) pc.
How do i go about doing this please.

Sorry if i have posted in the wrong section.

---

### Post by princemackenzie on 2005-01-13
You need a program like "partition magic" or "partition expert" (google for them if you don't have one) in windows to delete the linux partitions, and then reclaim that space for MS.  That can easily be done inside the partition software.  Most are user friendly.

After you do this, you need to get the MBR back from GRUB.  To do this, you will need your windows XP CD.   Boot with it, and when you get to the first menu, enter the recovery console (done with hitting "R" if i recall correctly).  Enter the admin password (if you don't have one, just hit enter).  And run the "fixmbr" utility.  Now reboot without the XP CD in and you should be good.  If I recall, windows will run chkdsk upon boot.

You should be set. 

Let me know from someone if there are any glaring errors in this guide.

---

### Post by philip41 on 2005-01-13
[QUOTE=princemackenzie]You need a program like "partition magic" or "partition expert" (google for them if you don't have one) in windows to delete the linux partitions, and then reclaim that space for MS.  That can easily be done inside the partition software.  Most are user friendly.[/quote]

Ah there is the first problem then, i have partition magic installed but it lists the whole of my second drive ( 2 ntfs +1 linux) as bad, i can not in P M perform any actions on the drive.
The drive is ok though as i can still boot to Ubuntu and use the other 2 windows partitions.
Even in the computer management console i can see the drive .

---

### Post by princemackenzie on 2005-01-13
Well, I might be stumped then.  I don't know what to do if PM thinks its hosed other than reformatting the whole thing, which im sure you rather not do.  Anyone else want to step in with some good ideas?

---

### Post by 3spades on 2005-01-13
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) burn that, boot from it and see if ya can remove the partition from there, should have an mbr utility there as well

---

### Post by az on 2005-01-13
Use the partitionner on the ubuntu install cd to play around with your partitions.  It cannot create ntfs, but windows can.  Boot from your installer.

It can create fat32...

---

### Post by philip41 on 2005-01-13
I checked out the disk with Seatools, and it passed. tried some of the otheer tools on the UBCD but was not sure what to do.

Using windows disk management, right clicking gives me the option to delete the partition.

1) Is this the option i need.
2) after doing this do i then need to  run the "fixmbr" utility.

---

### Post by philip41 on 2005-01-13
Guys thanks for your time and advice, i have now got my drive sorted now.

---

