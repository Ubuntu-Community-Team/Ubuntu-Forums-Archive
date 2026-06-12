---
title: "what happened to windows?"
date: 2010-03-30
forum: Hardware
---

### Post by omaru_88 on 2010-03-30
Hi all, 

I have this old laptop of a friend of mine who had abandoned it, it used to ran a windows xp, but didn't do it properly, didnt finish any new program installation, nor got connected to the internet or read most of usb memory sticks....
So I installed Ubuntu 7.04 without previously partition the HDD, as I didnt mean to use windows any more.

The first installation trial got wrong, maybe because of the liveCD having some problem...I'm not sure, but it took a couple or three trial to get it installed and running...after the first it did still recognize the other OS...
now it has no problems...

Except for the files it had before the successful ubuntu installation, now it seems to know nothing about the other OS it ran..nor anything about the old files....
this friend of mine allowed to try anything, but would like to have the files back.

Can anyone make a useful suggestion??

thank you

---

### Post by Fafler on 2010-03-30
Ubuntu 7.04 is really old. Why don't you try 9.10 instead. If it's because the laptop is slow, go for Xubuntu instead.

---

### Post by omaru_88 on 2010-03-30
I've just burned the livecd and will install the latest stable version accordingly, thankyou
would you like to make suggestions on how to recover the old files? thankyou again, Fafler

---

### Post by ottosykora on 2010-03-30
I am not sure, but if you just put in the CD and did install without any partitioning, the linux was installed to the first partition probably or did even format the whole disk and did install after to it, so what ever was an that disk before would be gone in that case.

Or do you have any idea to which partition did you install the linux system?

---

### Post by omaru_88 on 2010-03-30
thankyou for the insight! 
now guess the installation by default tried to partition the hdd in recognizing sth existing...
and the problem might be that the 'old things in' partition wasnt meant to be bootable.
so the problem could be a simple matter of configuration, at least at first.
if i'm rigth and it did create a partition, the old files would have prevented from loss, as the blank space in the hdd was large enough (at least 40 gb) so the ubuntu OS mustn't've any problem in looking for single block to store the data in.

Thank you both guys!
I yet have to check it before i declare this thread solved, but im taking an optimistic guess

---

### Post by Mark Phelps on 2010-03-30
From a terminal, enter the following "sudo fdisk -lu" (that's a lowercase L, not a one).

That will list the partitions on your disk.  If you see one or more with NTFS or FAT32 as the filesystem, you didn't overwrite the XP files.  If all you see is Ext3 or Ext4 partitions, you DID overwrite the XP files and they are gone.

---

### Post by theozzlives on 2010-03-30
I'm confused. First, you say you want Windows gone. Then, you say you can't find the files? 7.04 reached EOL (End Of Life) quite awhile ago, it's not gonna be productive to use it.

---

### Post by omaru_88 on 2010-03-31
it was a mess for me too, cuz this friend of mine didnt do any backup copy before leavin the laptop on my hands...but later she asked for some of them with personal value. 'ive already traced the directories, and think am about to get the files back! i dont use windows myself, but she did and even though i use that laptop, its still hers 

than kyou.

---

### Post by omaru_88 on 2010-03-31
Thank you a lot!

yesterday i downloaded and run 'recuva' and it managed to show the existing directories, but not to recover the files yet. it looks as they are still there,at least the directories are ok,it seems there wasnt any overwriting
i'll follow your instructions, if it goes as u say, maybe i could  manage the files directly from ubuntu...
what dou you think?
by the way i'm downloading plenty of appliances (seemingly useful ones) just in case they are needed.
thank you a lot man!

---

