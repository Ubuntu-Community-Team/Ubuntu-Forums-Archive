---
title: "Can't mount my USB Drive"
date: 2008-09-07
forum: Hardware
---

### Post by Erdr1ck on 2008-09-07
Hey guys, I just got an EEE PC (New model 901)  for school, and so I thought it would be a good time to take the plunge and move to Linux - my grad school projects all have to compile on a Redhat server to be graded.  

Made the live disk and did the install no problem, and found the documentation for some of the fixes required of the new hardware: [http://www.ubuntu-eee.com/index.php5?title=EeePC_901](http://www.ubuntu-eee.com/index.php5?title=EeePC_901)

So I got the files they discussed and put them on my thumb drive - the same one I used for the install - but Ubuntu says it can't mount it.  It sees the drive, and displays both its name and size correctly (Memorex Travel Drive, 4gb) but it won't mount it.  

Meaning I can't move the drivers and packages I need to fix the ethernet card, meaning I can't download the stuff I need directly.  I assume its because the thumb drive is Windows/FAT32 formated, but if so, what can I format it to such that its readable on my XP machine (where I download the patches and drivers) and my Ubuntu EEE PC (where they are needed)

Thanks in advance,
Erdr1ck, aka, Brett

---

### Post by banewman on 2008-09-07
I don't know how you are trying to mount it but the manual way is
sudo mkdir -v /media/thumbdrive
sudo mount -t vfat -v /dev/sdb1 /media/thumbdrive
You'll have to check the drives' name in /dev
:)

---

