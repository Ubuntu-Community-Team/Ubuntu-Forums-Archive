---
title: "HELP! My /home partition is damaged...."
date: 2006-04-18
forum: Hardware &amp; Laptops
---

### Post by Muiske on 2006-04-18
Hello everyone,



The situation is as follows. I have a laptop with dual boot Ubuntu and Windows XP. To obtain some space that both operating systems could read and write to, I decided to shrink the NTFS partitions and use the free space to make a FAT32 filesystem partition. I resized the NTFS partition in Windows, which went fine. I then booted in Ubuntu and used GParted to make a new FAT32 partition. (The free space was adjacent to the /home partition, which had -and hopefully still has- some 10 GB of data on it. The filesystem was ext3.) 

When I rebooted, everything went wrong. I got error messages all over the place - the root could not be mounted, /dev/proc could not be found, etc. etc. The time I rebooted after that even GRUB was giving me an error 17. While this is now solved and I can boot in both Windows and Ubuntu, the /home partition is damaged and cannot be recognized by Ubuntu. Curse me for a fool for not making backups occasionally, but I thought that quite little could go wrong.... Anyway, my and my roommates suspicion (who as quite some knowledge about Linux) is that the index-files of the partition are destroyed or damaged. It is strange that such a thing could happen with creating a new partition, but still it happened. And I want my data back!! Now I am asking you; is there anyone who was done a positive recovery? Using what software? Any general advices?


Thanks,
Muiske.

---

### Post by audax321 on 2006-04-18
Just a suggestion, but do you think when you created the new partition the other partition's partition number changed. For example it could have gone from /dev/hda1 to /dev/hda2 causing the /etc/fstab to try to mount the incorrect partition as ext3 and giving you the error? Kind of a long shot, but try downloading and burning a Knoppix LiveCD and see if it detects all your partitions. If it does, you can take a look in its /etc/fstab file to see what the new /dev path is.

---

### Post by Sef on 2006-04-18
If you can burn to a disk, try these two rescue disks:

[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

[http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/")

---

### Post by Muiske on 2006-04-18
[QUOTE=audax321]Just a suggestion, but do you think when you created the new partition the other partition's partition number changed. For example it could have gone from /dev/hda1 to /dev/hda2 causing the /etc/fstab to try to mount the incorrect partition as ext3 and giving you the error? Kind of a long shot, but try downloading and burning a Knoppix LiveCD and see if it detects all your partitions. If it does, you can take a look in its /etc/fstab file to see what the new /dev path is.[/QUOTE]


Thanks for your suggestion. Indeed, the partition numbers were changed but that is solved now. 

I have heard many good things about Knoppix, might as well try that one. :D

Thanks again!

---

### Post by Muiske on 2006-04-18
[QUOTE=Sef]If you can burn to a disk, try these two rescue disks:

[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

[http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/")[/QUOTE]


Thanks Sef, as soon as I get home I will burn these and boot with them.

---

