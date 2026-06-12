---
title: "Moving files between dual booted partitions"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by techdude300 on 2009-06-21
I decided to go with a dual boot with XP - Ubuntu, but there is a problem.
My hard drive currently just has one big XP partition. I know in order to install Ubuntu I need to make another. But what I want to do is move my files from XP to Ubuntu partition, then used the freed up XP space to add space to Ubuntu. I have nowhere to store files except my hard drive. Any suggestions?

---

### Post by presence1960 on 2009-06-21
> **techdude300 said:**
> I decided to go with a dual boot with XP - Ubuntu, but there is a problem.
My hard drive currently just has one big XP partition. I know in order to install Ubuntu I need to make another. But what I want to do is move my files from XP to Ubuntu partition, then used the freed up XP space to add space to Ubuntu. I have nowhere to store files except my hard drive. Any suggestions?

if i understand you correctly Ubuntu is not installed yet?. if that is true you have the cart before the horse (for moving the files). You need to defrag Windows at least once or twice then resize the Windows partition using partition editor on the Ubuntu Live Cd or use the gparted Live CD. Then once you create the partition(s) for Ubuntu you can install. Then you can move your files over. If you move your files over to a single Ubuntu partition when you install Ubuntu they will be gone!

Once Ubuntu is installed you can move your files from windows to ubuntu. You can then resize the windows partition and then use that space to extend Ubuntu's partition. Be careful though don't leave windows so little free space that your windows becomes a bottleneck.

I would suggest some reading prior to installing : 

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  -for  pdf Ubuntu Pocket Guide w/ a great how to for installation
[https://help.ubuntu.com/9.04/switching/index.html](https://help.ubuntu.com/9.04/switching/index.html)

This should pretty much get you familiarized with what you are going to attempt to do. it is a good idea to know what you are going to do prior to attempting to do it.

P.S. I would find a way to back up your files because although the partitioning & install processes work well there is always the chance something can go wrong and result in lost/corrupted data. Don't get caught with your pants down on this! Look into a USB flash drive, DVD-R, CD-R or something to use to back up your files.

---

### Post by techdude300 on 2009-06-21
The thing is, once I move the files to the Ubuntu partition, I will have to extend my Ubuntu partition backwards onto empty the newly created space coming before it on the disk. Is that possible?

EDIT: Found the answer. For some reason I thought you couldn't do that. Thanks for the help.

---

