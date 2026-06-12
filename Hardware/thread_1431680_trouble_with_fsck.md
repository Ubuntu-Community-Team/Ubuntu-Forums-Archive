---
title: "trouble with fsck"
date: 2010-03-16
forum: Hardware
---

### Post by vanstratum on 2010-03-16
when I frist installed ubuntu I got a notice that my hard drive had bad sectors. I have since replaced that drive and would now like to format the old drive as fat 32 and use it to back up data from my wife's xp machine and from my Ubuntu machine. I have managed to format the old 160GB hard drive to vfat wit gparted, but i still need to mark the bad sectors. a little research revealed that fsck was likely to be helpful. unfortunately it is giving me a response that I really don't know what to do with:
ubuntu@ubuntu:~$ sudo fsck.vfat -av /dev/sda
dosfsck 3.0.3 (18 May 2009)
dosfsck 3.0.3, 18 May 2009, FAT32, LFN
Logical sector size (190 bytes) is not a multiple of the physical sector size.


I have already tried to solve the problem with the manufacturers software(estools) without much luck. It recognizes the bad sectors, but offers no way to mark them so as not to be used in the future.

any help would be appreciated.

---

### Post by Fir3chi3f on 2010-03-17
I don't have much experience with fsck, but ubcd has some tools that might solve your problem. [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Good luck and post back!

---

### Post by vanstratum on 2010-03-17
thanks for recommending the UBCD seems like a good thing to have around. UBCD utilities that I tried were unable to find the bad sectors. I do seem to have found my answer so let me know what you think. Palimpset is saying among other things that the bad sectors will be remapped if there is a write error. this would seem to suggest that other than my hard drive crashing. which would be ok since it is just a back up I don't have much to worry about. I think this is right anyways...

---

