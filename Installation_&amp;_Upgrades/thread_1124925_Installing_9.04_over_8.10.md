---
title: "Installing 9.04 over 8.10?"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by CheesyD on 2009-04-13
I have an old desktop that had XP and Ubuntu 8.10 on it. I wanted to upgrade the 8.10 to the 9.04 Beta. I tried the upgrade command but it didn't work so I figured I'd just do a full install over 8.10. When I get to the partition choice section (yes, I'm a linux noob), I wanted to keep XP while installing 9.04 in the same space currently occupied by 8.10. It wouldn't let me do that. It wanted to keep XP, 8.10, and then install 9.04 in its own space. I went to the "advanced" section but didn't know what the heck I was doing there. I finally just told it to use the entire disk for 9.04, and it installed just fine.

I also have a laptop which is my main PC. It also has XP and 8.10 on it. I really want to keep a dual boot on the laptop, with XP and ultimately 9.04. How the heck do I get 9.04 to install over 8.10? I don't want XP, 8.10, and 9.04. Any advice will be greatly appreciated.

If this should have been posted in the beginner section, my apologies.

---

### Post by whoop on 2009-04-13
Did you try:
Alt+F2 and then update-manager -d
?

---

### Post by Ericyzfr1 on 2009-04-13
> **CheesyD said:**
> I have an old desktop that had XP and Ubuntu 8.10 on it. I wanted to upgrade the 8.10 to the 9.04 Beta. I tried the upgrade command but it didn't work so I figured I'd just do a full install over 8.10. When I get to the partition choice section (yes, I'm a linux noob), I wanted to keep XP while installing 9.04 in the same space currently occupied by 8.10. It wouldn't let me do that. It wanted to keep XP, 8.10, and then install 9.04 in its own space. I went to the "advanced" section but didn't know what the heck I was doing there. I finally just told it to use the entire disk for 9.04, and it installed just fine.

I also have a laptop which is my main PC. It also has XP and 8.10 on it. I really want to keep a dual boot on the laptop, with XP and ultimately 9.04. How the heck do I get 9.04 to install over 8.10? I don't want XP, 8.10, and 9.04. Any advice will be greatly appreciated.

If this should have been posted in the beginner section, my apologies.

What do you mean by it would not let you do that?
You just have to specified your / directory and /home if you have a separate partition in place of 8.10. Do you get a message?

---

### Post by CheesyD on 2009-04-13
> **whoop said:**
> Did you try:
Alt+F2 and then update-manager -d
?

Yes, I did and got an error each time I tried it. I didn't write the error down... doh.

---

### Post by CheesyD on 2009-04-13
> **Ericyzfr1 said:**
> What do you mean by it would not let you do that?
You just have to specified your / directory and /home if you have a separate partition in place of 8.10. Do you get a message?

It showed the prior two operating systems on the bar... XP and 8.10. I could slide the thing back and forth on the bar to resize the existing 8.10 allocation but that was it. I couldn't alter the size of the XP allocation nor did I see how I could tell it to install 9.04 in the same space where 8.10 already was residing.

---

### Post by Ericyzfr1 on 2009-04-13
You have to select the partition, then edit and enter the mount point, the same way you installed 8.10 the first time.
Or you could delete the 8.10 partitions and reformat them for 9.04 so you can use ext4.

---

### Post by CheesyD on 2009-04-13
> **Ericyzfr1 said:**
> You have to select the partition, then edit and enter the mount point, the same way you installed 8.10 the first time.
Or you could delete the 8.10 partitions and reformat them for 9.04 so you can use ext4.


I have EASUS Partition manager on XP that I could delete the Ubuntu partition with, I guess. Then just install 9.04 from scratch. You think that would be the best (safest) way to go? Does 9.04 default to the ext4 or do I have to specify that somewhere?

---

### Post by Ericyzfr1 on 2009-04-13
If you choose to delete any Ubuntu partition you should do it during the 9.04 installation. 9.04 is not selected by default, you need to choose in the file system list.
Please, do not use any XP programs, just follow the Ubuntu installation process. I think you need you look for a procedure to partition manually as I guess the first time you let Ubuntu install 8.10 alongside XP. Now you would need to go in the manual partitioning section and you have to be careful not to erase your XP partition.

---

### Post by Cybie257 on 2009-04-13
> **Ericyzfr1 said:**
> If you choose to delete any Ubuntu partition you should do it during the 9.04 installation. 9.04 is not selected by default, you need to choose in the file system list.
Please, do not use any XP programs, 

So the OP is not confused, the "9.04 is not selected by default" should have said EXT4 is not selected....

Also, Yes, you CAN use windows to delete the partitions. In fact, you can use the windows disk manager to delete the partitions and just leave them/it as undefined/unformatted. 

This will INSURE that you DO NOT delete your XP partition as Windows will not allow you to delete the live partition that is in use. Probably a LOT safer than trying to use the Ubuntu Installer for noobie. I've done it MANY times in the past 10 years. 

Then, do your fresh install of 9.04 on the "Empty Space".

If you want to use EXT4, you will have to do it manually. Don't know why they took that out as Alpha 4 (EDIT: Or was is Alpha 3??, one of those 2) it was by default. I repeat, it was by default. At least when I installed it. I never selected manual and it was an EXT4 partition. 

Hope this helps.

-Cybie

---

