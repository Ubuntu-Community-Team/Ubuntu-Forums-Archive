---
title: "Weird Problems Please help!"
date: 2008-08-22
forum: General Help
---

### Post by Terry19 on 2008-08-22
Hey, Can anyone please help me, My ubuntu is acting very odd l8ly. 
Eg. When it does its Disk check when i turn on the computer it gets to the end 99% and then goes to a black screen with a lot of writing on it, i miss the first few lines because its to quick for me to read, it has part of file system missing or something manual disk check required, blah blah then is has press CTRL + D for something or other i press ctrl d and it restarts my computer... I end  up just having to skip the disk check each time, Ubuntu seems to run normally except sometimes it will send me to the log in screen for no reason or shut down, usually after using a full screen application. How do i fix this problem or do a manual disk check, or turn off auto disk checking, i have edited it once b4 when i was using the last release of ubuntu but have since forgotten. please help

[email]terryk_tv@hotmail.com[/email]

---

### Post by Terry19 on 2008-08-22
Hey, Can anyone please help me, My ubuntu is acting very odd l8ly.
Eg. When it does its Disk check when i turn on the computer it gets to the end 99% and then goes to a black screen with a lot of writing on it, i miss the first few lines because its to quick for me to read, it has part of file system missing or something manual disk check required, blah blah then is has press CTRL + D for something or other i press ctrl d and it restarts my computer... I end up just having to skip the disk check each time, Ubuntu seems to run normally except sometimes it will send me to the log in screen for no reason or shut down, usually after using a full screen application. How do i fix this problem or do a manual disk check, or turn off auto disk checking, i have edited it once b4 when i was using the last release of ubuntu but have since forgotten. please help

---

### Post by livestockPimp on 2008-08-22
when it comes to the "needs to do a disk check enter root password or press ctrl+d to continue" you are meant to type the root password. The fun part is ubuntu defaults to no root password and using sudo.

if you can get into the system get to a terminal and type "sudo passwd root" and set a root password.

When you get to the ctrl+d screen, enter the root password and this will drop you to a # prompt. from here you can run manual disk checks with fsck.

ie; #fsck /dev/sda1

Also are you using ext2 or ext3 partitions? generally you dont get to this screen unless you have ext2 since it doesnt have journaling. I would recommend you check this and look at converting ext2 -> ext3. This is a non-destructive conversion and you can do it on the system without loss of data, formatting, ect.

---

### Post by Sef on 2008-08-22
1) What version of Ubuntu do you have?  

2) How did you update it?

---

### Post by Terry19 on 2008-08-22
Well i update every day using the update manager. And i will try the first option very soon. But can anyone tell me why it just started doing this all of a sudden? 
I use Ubuntu Release 8.04 (hardy) Kernel Linux 2.6.24-21-generic GNOME 2.22.3

---

