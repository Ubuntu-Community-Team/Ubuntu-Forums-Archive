---
title: "Remove Ubuntu"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by ElectricGypsy72 on 2009-03-05
I used a cd to install Ubuntu. I decided not to leave a partition for Windows and just let the install format the HDD when it installed. 
Now that I have decided to install Ubuntu on a different computer and put XP back on this computer I am having a problem.
All the unistall forum posts I see talk about dual boots. Since I don't have one I am unsure how to uninstall or even reformat the drive so that I can use the recovery CD for XP. I have tried using the CD. but after it starts to load the setup files a Blue Screen comes up and says that there is a fatal error that might damage the computer so Windows has shut down. 
From what I have read on this forum, I was guessing this has something to do with the mbr trick that everyone suggests for those with a dual boot. 
I saw a post about DBAN that can wipe a HDD. If I did that would I then be able to use the XP Recovery CD without getting a fatal error?
Any help would be greatly appreciated.

---

### Post by x33a on 2009-03-05
you don't need to use dban. just use the ubuntu live cd. open gparted, and format the hd to ntfs.

---

### Post by howefield on 2009-03-05
Load up your ubuntu live cd and use the partition editor (system > administration > partition editor) and delete your ubuntu partitions and create a new one and format to ntfs.

Remember to back up any files you want to keep from that partition.

---

### Post by Andi064 on 2009-03-06
I installed ubuntu with the gparted and make a 20 gb space unalocable for windows. How can I undo it and intall ubuntu inside windows? I know how to instal it inside windows but how to restore the 20 gb. Could some1 help me ?

---

