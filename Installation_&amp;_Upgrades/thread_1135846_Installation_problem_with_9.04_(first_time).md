---
title: "Installation problem with 9.04 (first time)"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by DrBallard on 2009-04-24
Hello,

I'm a new user of Ubuntu and Linux based OS. I don't hate windows, I've just really mastered it and feel like there's nothing else to it, so I want to learn a new OS. After a quick research, it seemed Ubuntu was a good pick.
All right, here's how I partitioned my drive, which is a 100gb sata/ahci drive.

20gb - primary - ntfs - winxp 
40gb - logical - fat32 - partition for sharing files between windows and ubuntu
8gb - logical - ext3 - swap partition (I don't exactly understand it's full use yet..)
8gb - logical - ext3 - /home partition (sharing of my documents, right?)
20gb - primary - ext3 - Ubuntu 9.04!

Ok here's the deal. Everything went fine during the installation and partitioning. When I removed the CD from tray and pressed Enter, I've had a full screen of errors and when I boot Ubuntu, it freezes on "Starting up..."

I'm guessing it has something to do with the partitions...

Anyways, thanks a lot guys ... I'm sticking to that Ubuntu so I'll be around :guitar:

---

### Post by bacardiandwatermelon on 2009-04-24
If I were you I would set it up this way..

20gb - ntfs - winxp
40gb - fat32 - partition for sharing files between windows and ubuntu
35gb - root - ext3 - Ubuntu 9.04! (this includes your home directory)
1gb - swap - swap partition (Its just like you page file in xp)

Sorry I can't really help with your freezing problem

---

### Post by leonardo_neo on 2009-04-24
> **bacardiandwatermelon said:**
> If I were you I would set it up this way..

20gb - ntfs - winxp
40gb - fat32 - partition for sharing files between windows and ubuntu
35gb - root - ext3 - Ubuntu 9.04! (this includes your home directory)
1gb - swap - swap partition (Its just like you page file in xp)

Sorry I can't really help with your freezing problem

I agree with '*bacardiandwatermelon*' for you need not to have such a huge swap partition. You need to have the twice the amount of your RAM only when you want to have the 'hibernation' function intact, because if I am not wrong, the temporary hibernation memory is stored in swap partition.

But hibernation feature is not very essential, and It is not wise to waste so much space just for this. So I agree with him about the size of the swap partition. (Probably personally I will choose 2 Gb for myself)

But I would also like to have a separate /home partition and not everything in / root. I would give 10 Gb for / root, and rest for /home.

---

### Post by TheLions on 2009-04-24
just had same problem as you, i fixed it by some thread on ubuntuforums but can't find it right now...

anyway what happened... it installed grub(program that lets you choose between Win and Ubuntu) on your windows partition instead on your ubuntu partition. So you'll need to fix windows bootloader and ubuntu bootloader (grub)

here is little guide what you need to do: (for ubuntu)
[http://ubuntuforums.org/showpost.php?p=1308395](http://ubuntuforums.org/showpost.php?p=1308395)

for windows you need kick in windows install cd, go to recovery console and there type fixmbr and fixboot

---

### Post by DrBallard on 2009-04-27
Thanks for the replies people.

As for the swap partition, I really don't mind if it's slightly too large. I want to have a fully functionnal dual boot os'(es?)!

All right, more info on the problem...
Ubuntu always stalls when I try to run it (sticks on Starting up... forever, only way to get out is hard reboot). BUT! If i run recovery mode and repair grub, then reboot, it will work. Until the next reboot. Then I have to do the same thing.
Unfortunately, this works 50% of the time. When I run recovery mode the other 50% of the time, it freezes loading the "APCI : .... blah ... intram - something... blah" (lost my piece of paper when I wrote it... )

also, yesterday for some reasons, it wouldn't even load windows, it would bring up the win xp screen then go back to startup screen, and do that over and over.

I was also (also) wondering... when it loads Ubuntu (and fails) it says hd (0,1) --- that means it's on my 2nd primary partition, right?

Thanks a lot for the insights guys (and gals? I wonder... )

---

### Post by DrBallard on 2009-04-27
Also about the HD, since I put my fat and my /home before my ubuntu partition, should it be hd(0,4) or it only takes into account the primary disks?

---

### Post by DrBallard on 2009-04-28
Bump.


*Update*
Installed win7 beta over my windows xp on the ntfs drive. Now grub (dual boot) wont load. Which confirms the problem that grub was installed on my windows partition.

---

### Post by Scooby1 on 2009-04-28
I am pretty sure local partitions are counted as a number in grub, so in the format you listed it should be booting ubuntu from hd(0,4).  The reason you are hung up at start up is because it the boot loader is looking for the OS in the wrong place, hd(0,1) which is your fat32 partition. You need to edit your Grub.

Also note that if you install ubuntu first and then windows, windows will overwrite ubuntu boot loader in the Master Boot Record (MBR) and you will need to repair ubuntu to overwrite the windows boot loader. You do not want the windows boot loader in the MBR because windows boot loader will not recognize ext3 file system.

Also curious if there is a reason you have a fat32 partition? Ubuntu can read and write nfts and can access all your files and folders in your widnows partition. I dual boot and jsut keep my ubuntu partition small and store all my documents, photos, music in my much larger windows partition where they can be accessed by both operating systems. I guess it would be easier to have a seperate partition for this, but why not make it nfts?

---

### Post by Sef on 2009-04-28
> Also note that if you install ubuntu first and then windows, windows will overwrite ubuntu boot loader in the Master Boot Record (MBR) and you will need to repair ubuntu to overwrite the windows boot loader. You do not want the windows boot loader in the MBR because windows boot loader will not recognize ext3 file system.

That is correct.  Easiest way to reinstall GRUB is to use [Super GRUB Disk]("http://www.supergrubdisk.org/").

---

### Post by DrBallard on 2009-05-01
Thanks for the reply guys.
I guess the reason for the fat32 partition is that I read a tutorial about ubuntu install and it said fat32... probably an older version of ubuntu which didn't support ntfs?

Time to try that Super grub disk...!
Thanks again :D

---

### Post by DrBallard on 2009-05-01
Hum... just got some info from reading a manual which says " Primary partitions are marked from 0 to         3 (hd?,0), (hd?,1),         (hd?,2), (hd?,3). Logical partitions in the extended partition are counted from         4 up, regardless of the actual number of primary partitions on the hard disk,         e.g. (hd1,7)."


which means the hd (0,1) was correct?

source: [http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

---

