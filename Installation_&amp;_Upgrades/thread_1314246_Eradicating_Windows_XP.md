---
title: "Eradicating Windows XP"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by ukapolog on 2009-11-04
I discussed with a few of you yesterday about completely deleting Windows XP from my secondary, ageing computer. The main problem was gaining successful access to Wondows files while using Xubuntu.
I have now discovered that I can do this through Wine.
 
Just now I got successful access to my Windows folder containing 18 files from 'command' to winhlp.exe. Among these 18 are 'gecko,' winsxs, system and system 32. I can freely delete through the Wine prog, I just deleted my Windows temp file.
 
If I now delete all of these files will that effectively get rid of Win XP from my computer to leave only Xubuntu??
 
Any help appreciated.
 
ukapolog.

---

### Post by tripolitan on 2009-11-04
> I have now discovered that I can do this through Wine.
I may not be fully understanding this but you don't need to use wine at all to access ntfs files! If you've installed Ubuntu on a PC that already has Windows XP, the files should be accessible from Nautilus.

> If I now delete all of these files will that effectively get rid of Win XP from my computer 
Yes

> to leave only Xubuntu?
No. it will leave Xubuntu and an empty ntfs partition.

Recovering this empty partition properly requires work, mainly editing your /etc/fstab  (please post your existing file) and possibly editing GRUB upon rebooting...

---

### Post by mxc1090 on 2009-11-04
Have you tried an Ubuntu LiveCD?  I have always been able to access all of my Windows files from it.

Also, is Windows on a different partition? If so, use a partition manager (gparted on the LiveCD...or whatever Xubuntu uses) and delete the partition then expand your Xubuntu partition.

Did I understand you correctly?

---

### Post by tripolitan on 2009-11-04
> ...and delete the partition then expand your Xubuntu partition.

Depending on where his Xubuntu partition(s) is/are, this could render his desktop inaccessible. If XP was installed first, before Xubuntu, it is safe to assume that it resided in /dev/sda1 and so his fstab will point to /dev/sda2 for Xubuntu but once sda1 has been deleted and consequently sda2 becomes sda1, (*GParted does not automagically edit fstab*), once it is finished resizing. Therefore, on the next boot, GRUB will look for /dev/sda2, which had been renamed in the previous step(after re-sizing) to sda1 and will not find it (unless GRUB is edited upon reboot).

I have done this numerous times but never really documented the result, therefore, I maybe wrong.

---

### Post by grandtoubab on 2009-11-04
and think about not to delete the MBR

---

### Post by ukapolog on 2009-11-04
Thanks for all the comments. 
 
As far as I am aware, Xubuntu is not partitioned off. I simply installed it. Now when I boot up, I am given the option of XP or Xubuntu.
Also one of you mentioned the 'MBR' - I don't immediately know what you mean. Is that the memory? If so, how could I delete that by deleting the files in the Windows folder?
The only thing that worries me in all this is that it could all go wrong and I won't be able to boot up Xubuntu.
 
All I really want to know is, as far as you are aware, will deleting the files in my Windows folder cause any serious damage.
 
ukapolog.

---

### Post by ukapolog on 2009-11-04
Sorry, the penny just dropped that is the master boot record, of course. That won't be in the Windows folder will it?
 
apolog.

---

### Post by ukapolog on 2009-11-04
I note that in Vista, the MBR is in the folder called BOOT (unsurprisingly) and that *is in* the Windows file.

I now need to know what this essential folder is called in XP

---

### Post by wilee-nilee on 2009-11-04
If you want just Xubuntu the way your going about it is a good way to end up with a unbootable Xubuntu. So if you want just Xubuntu and you can back up what ever is there that you want to save just back it up use the live cd partition manager to delete all the partitions reinstall Xubuntu add the saved info. It seems that you may have gotten the the Linux is a geek thing when actuality there are some simple ways to have a very custom system without editing a whole bunch or deleting files, and partitions. The fact that you don't know what the MBR is throws up a big red flag in my perception of your experience. If you are trying to learn with this methodology then just make sure you have the backups we all have a starting point and learning curve just be careful.

---

### Post by ukapolog on 2009-11-04
>  If you want just Xubuntu the way your going about it is a good way to end up with a unbootable Xubuntu. So if you want just Xubuntu and you can back up what ever is there that you want to save just back it up use the live cd partition manager to delete all the partitions reinstall Xubuntu add the saved info. It seems that you may have gotten the the Linux is a geek thing when actuality there are some simple ways to have a very custom system without editing a whole bunch or deleting files, and partitions. The fact that you don't know what the MBR is throws up a big red flag in my perception of your experience. If you are trying to learn with this methodology then just make sure you have the backups we all have a starting point and learning curve just be careful.

 
Hey, cool it!
Isn't it nicer when we can all be polite to each other??
If you want to suggest I'm a complete idiot that's your right but I question that attitude on a forum of this nature. I am vastly experienced with Windows systems but Ubuntu is new to me - just a few weeks. I've admitted that. I actually only asked a simple question but I find that you all have opinions about it (which might be fair enough), but now somebody is just really impolite as well. That was not called for.
 
ukapolog.

---

### Post by wilee-nilee on 2009-11-04
> **ukapolog said:**
> Hey, cool it!
Isn't it nicer when we can all be polite to each other??
If you want to suggest I'm a complete idiot that's your right but I question that attitude on a forum of this nature. I am vastly experienced with Windows systems but Ubuntu is new to me - just a few weeks. I've admitted that. I actually only asked a simple question but I find that you all have opinions about it (which might be fair enough), but now somebody is just really impolite as well. That was not called for.
 
ukapolog.

I didn't suggest your a complete idiot, I am the complete idiot and can prove it,;) don't let this perception of my post cloud what I said. I gave you some options that will quickly fix your problem and suggested that it is okay to learn from this but be careful, I will try more smiley face when I respond to you. your frustrations are being projected into my response. I also suggested that my perception could be faulty in a abstract way; but what do you know I was correct that you are new to Linux, I say welcome and I hope we can all help each other here, good luck. ;)

---

### Post by seenthelite on 2009-11-04
I hope I am not missing the point but is there any reason why you can not backup whatever and do a clean fresh install this will give you the best result and definitely remove windows.

---

### Post by tripolitan on 2009-11-04
> Now when I boot up, I am given the option of XP or Xubuntu.

This necessarily means that Xubuntu was installed alongside Windows. I would agree with others in suggesting a complete re-install but next time, when you get to the partitioning stage, select "entire drive" (second option, I believe).

---

### Post by tripolitan on 2009-11-04
For what its worth, I don't think that wilee-nilee was impolite at all.

---

### Post by wilee-nilee on 2009-11-05
> **tripolitan said:**
> For what its worth, I don't think that wilee-nilee was impolite at all.

I could have worded it better, but my concern was that if it was a new user of Linux that I give good solid advice that is understandable and efficient in getting the job done. ;)

---

### Post by tripolitan on 2009-11-09
Fair enough, I guess I have developed a tough skin. For many years, I attended USENET, where RTFM or "Google is your friend" are considered good answers; and, in many respects, they are. :]

---

