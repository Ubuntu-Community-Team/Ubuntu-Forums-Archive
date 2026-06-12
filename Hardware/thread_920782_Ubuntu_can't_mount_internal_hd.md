---
title: "Ubuntu can't mount internal hd"
date: 2008-09-15
forum: Hardware
---

### Post by Gras$hoppa15 on 2008-09-15
Hello, I have an inspiron 1520 laptop, It runs xp home, recently i did the microsoft updates and upgraded to SP3 and got all the good stuff. However there was a problem, When i restarted my computer i get an error saying that windows did not start properly, and it gives the following options
Safe mode
safe mode with networking
safe mode with Command prompt
Start from previous config
Start normally

Now, i have chosen EACH one and it has come to a blue screen saying that windows cannot start, it advises to uninstall any anti virus programs and reboot it, However, i can't uninstall it without windows. So then i come to ubuntu, I have gotten ubuntu to load up and all i want to do now is to save some files off my internal HD, and then just reinstall xp itself, However, Ubuntu cannot mount my internal hard drive, It says that windows was not shut down properly and it gives examples on what to do, I can't do anything with windows so i just tried to do the Force mount, However then it says that i cannot mount it because i do not have root, i have tried using Sudo and it still won't work. I have checked my /dev/sda files and it says all of them are unreadable. I really don't want to install ubuntu because i have heard it deletes everything on the hard drive. but if anyone can help me, please post, PS. i am kind of new to linux and using the Terminal, and Reading the codes.

---

### Post by eggdeng on 2008-09-15
Open a terminal and run
```
sudo fdisk -l
``` to check how the disk / partition in question is identified. (I'll assume it's sdb1.)
Now run
```
sudo apt-get install ntfsprogs
```
which will install a program which includes a repair utility. Run the utility
```
sudo ntfsfix /dev/sdb1
```
Again, this is assuming the drive is sdb1 - if not change sdb1 to whatever value you got from the fdisk command.
With luck, this will repair and mount the drive.

---

### Post by Gras$hoppa15 on 2008-09-15
thank you soo much man, saved my entire school work :KS

---

