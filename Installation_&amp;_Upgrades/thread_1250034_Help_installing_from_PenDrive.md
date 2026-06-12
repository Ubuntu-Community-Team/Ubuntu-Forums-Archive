---
title: "Help installing from PenDrive"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by Luca_turicci on 2009-08-26
Hi there, me again.

I've been testing many distros in my netbook only for the curiosity of seeing the "new stuff", since netbooks have no CD/DVD reader, i generally use a pendrive (my bro has an external CD RW unit, but i don't want to ask him all the time, plus it's too much money on blank CDs) so, my only pendrive is a 4gb one, and making backups of it and restoring them every 3 days is just too annoying, so I thought: "Hey, what if I partition it with gParted, leave a 1gb partition to "burn" live images on it, and 3 gb for other stuff?" So I partitioned it, 1 ext3 partition for live images, and 1 FAT32 for files.

the problem was:

When i rebooted and chose the pendrive as boot device it went to a shell screen saying "boot:" and that was all. I tried typing "/dev/sdb1" since that's where the pendrive was, but nothing it returned "Can't locate linux image" or something like that, so I rebooted again.

I formatted the 1gb partition as fat32 and burned the image on it, rebooted and the same result.

Anyone can tell me if is it possible to do such thing? and how? please help!

---

### Post by P4man on 2009-08-26
the live image doesnt need ext3, ironically perhaps, but it uses FAT32. I think thats your only mistake. How do you "burn" the live image though? Are you using USB creator or doing it "by hand" ?

---

### Post by P4man on 2009-08-26
btw, you dont even have to partition to achieve this. If you just make a 4GB live cd, there will be 3+Gb free space on it that you can use for files.

---

### Post by Luca_turicci on 2009-08-26
First, I burn with UNetBootin because i'm trying moblin, slitaz, fedora and some others that are not Ubuntu.

Second, I already tried with FAT32 and didn't work.

Third, i wanted to partition because everytime i burn a new image it formats everything, I know i could still store data on the LiveUSB, but i'd have to backup and restore that data before burning a new image.

---

### Post by P4man on 2009-08-26
FWIW AFAIK, you can burn fedora, moblin and other iso's with ubuntu's usb creator too, but Im not sure its  any better than what you're using.

Anyway if neither USB creator nor UNetBootin handle usb sticks with > 1 partition well, try the manual approach:

[https://help.ubuntu.com/community/Installation/FromUSBStick#Manual%20Approach](https://help.ubuntu.com/community/Installation/FromUSBStick#Manual%20Approach)

Also note that windows is unable to read anything other than the first partition on a USB stick. You can make 2 FAT32 partitions, it will only see the first.

---

### Post by Luca_turicci on 2009-08-26
Thanks, i'll have to try that way.

Btw, i tried to burn them with the Ubuntu's default application, but it doesn't work, so I had to install Unetbootin, and also, my LiveUSB is the first partition of the pen drive...

---

