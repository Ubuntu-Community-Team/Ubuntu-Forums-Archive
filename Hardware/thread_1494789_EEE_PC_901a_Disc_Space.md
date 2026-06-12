---
title: "EEE PC 901a Disc Space"
date: 2010-05-27
forum: Hardware
---

### Post by Fechter1813 on 2010-05-27
Hi all!

I have had an EEE PC 901a for about 18 months now. Until last week I had  Win XP running on it, but since XP was slow and suck, I finally decided  to replace it with the newest Ubuntu Netbook Remix (excellent choice). 

My last experience with Linux was about 10 years, when I used SuSe (I  think...) for 2-3 years. So I have a general idea of how things work,  but due to not having used Linux for a good 7 years I am basically a new  Linux user again.

_Here is my situation/problem_: I installed Ubuntu Netbook Remix  last week and everything is working wonderfully now (way better than  XP). The problem is my 901 SSD drive setup. The EEE PC 901a comes with a  4GB SSD drive (which I have installed the Ubuntu Netbook Remix on) and  an 8GB SSD drive (slower than the 4GB SSD drive), which I currently only  have mp3's/podcasts on. However, after merely approx 6 days using  Ubuntu I already have disc space issues on the 4GB SSD drive. I've  attached (I hope the attachments work) some screen shots I made with df  -h and the Disk Usage Analyser. 

(If the screenshots don't work: I have approx 40MB free space on sda1  (the 4 gig drive) left, the entire sdb1 drive can be deleted and used  for whatever, and sdc1 is an external drive with plenty of free GB's,  but I only put mp3's/videos/etc on there since it is not always  attached)

The point is, since I installed to the 4GB sda1 drive everything is  crammed on there I already do not have any more space. But my 8GB drive  (which now has mp3s and podcasts on it which can be removed to my 200GB  external drive) is free to be used. So altogether I have 12 GB that  could be used for the system, but I don't know how to get Linux to use  the 8GB drive as well for programs/system files/etc. My solution to this  problem under Windows was to install Windows XP to the 4GB and move the  Programs folder to the 8GB drive. This worked fairly well although the  ridiculously large Windows updates also quickly filled up the 4GB drive.

_So my question is_: Does anyone have any suggestions how I could  move the parts my file system that are large or likely to grow (such as  Evolution e-mail folders, other programs, etc. - ideally all programs)  to the 8GB drive and just leave the system relevant files on the 4GB  drive? Since I managed to do this in Windows, I am sure the same has to  be possible in Ubuntu, I just don't know how. Ideally I would move as  much as possible over to the 8GB drive, but I do not know what I am  allowed to move and don't want to move something that shouldn't be moved  and have to reinstall.

I also found this on the forums already, but I am not sure if it does  what I want it to:  [http://ubuntuforums.org/showthread.php?t=1287496&highlight=eee+pc+901](http://ubuntuforums.org/showthread.php?t=1287496&highlight=eee+pc+901)

So, I'm open for any suggestions about how to free up space on that 4GB  drive (its not as bad as it seems on the screenshots - I have some  things that I can remove such as Amarok -or- Rhythmbox, since I've been  playing around with programs a lot to see what I want to use, but the  point remains the same: I will need more disc space on the 4GB drive  very soon even after removing unecessary programs). If anyone has any  suggestions, please keep them minimally technical since my last Linux  experience was over 7 years ago! And if this doesn't work... I guess  I'll have to reinstall windows. And cry. A lot :(

Thanks in advance for any suggestions!!

---

### Post by dino99 on 2010-05-27
[http://swiss.ubuntuforums.org/showthread.php?t=1463870](http://swiss.ubuntuforums.org/showthread.php?t=1463870)

you may need the latest kernel from this ppa:

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by Fechter1813 on 2010-05-27
Yeah, removing the swap (first link) is definitely something I will have to consider. I can do without hibernation, etc. Anything is better than going back to Windows. I will probably have to do this with time. But my swap partition is only 234 MB, so that alone isn't going to do the trick - as new upgrades, e-mail, etc come along, the 234 MB aren't enough...

I am still more interested in moving some of the larger parts of the file structure over to my second SSD (8 gig) drive. Then I'm fine. The thread below is essentially the same topic, but he wanted to move to an external drive (instead of second SSD internal drive as with me), and didn't get the issue resolved:

[http://ubuntuforums.org/showthread.php?t=1350417&highlight=eee+pc+disc+space](http://ubuntuforums.org/showthread.php?t=1350417&highlight=eee+pc+disc+space)

---

### Post by dino99 on 2010-05-27
instead of installing the standard desktop you can choose the minimal or remove these meta-packages to install only what you need to make room, then can resize the partitions booting with partedmagic

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by Fechter1813 on 2010-05-27
Is it possible to move my /usr folder to the other partition, sdb1 using this method?:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Has anyone ever done this or know if it will work? If it works with HOME like in the guide then probably with /usr, right? That would be ideal, cuz that would save 2.2 gig on a 4.0 gig drive. I don't see anything that says I shouldn't do this, so I'm probably going to try it...

Also: Does anyone know what all the "none" Filesystems (left-hand column) in the first attachment are (i.e. all entries between /dev/sda1 and /dev/sdb1??? They all appear to have approximately 490M space available, but I can't figure out what they are...

---

