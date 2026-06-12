---
title: "Diskspace doesn't increase after deleting files"
date: 2018-01-25
forum: Hardware
---

### Post by n0c0d3 on 2018-01-25
Hi,

I have a NTFS partition on my harddrive and after I delete files from it, either directly or from the trash, the free space doesn't increase anymore. When I add files to the disk the free space does decrease however, so the free space gets, at least in numbers, smaller and smaller and don't know what happens when it gets to 0, but I'm not eager to try.

I have a a free-diskspace indicator and I checked gparted. They both give the same numbers. But Thunar filemanager in the folder properties gives higher numbers, both for total and free space, but at least the free-space is still too low to what I think it must be. To be honest I forgot what size I actuall formatted this partition to, so I don't know if this indication is somehow corrupted as well, but at least one of them give a wrong number (in GB). After deletion of files the .trash-folder is empty.

My normal drive-area (ext4) doesn't seem inflicted with this syndrome. 

It all happened after I was working on this computer with some music video from this NTFS partition playing in the background. Then I used some wrong keyboard shortcut and got a terminal screen which I couldn't exit, quit or reboot my way out of (while, like on the Titanic, the music was still playing in the background), and had no clue how to get back to my normal desktop, so I had to give the computer a hard reset. I supppose this may have corrupted something on the drive, ending up giving it this erroneous free-space indication. But I actually don't have a clue what's wrong.

For completemess here are some statistics from the indicators and Thunar from before and after adding a 1.2GB file to the partition, and after deleting it. The actual free disk-space must be somewhat over 200 GB.

Thunar (initial -> after add 1.2GB -> after delete)
8165 items totalling 400.9 GB -> 8166 - 402.1 -> 8165-400.9
Free 186.1 of 622.7 GB -> 185.0 of 622.7 -> 185.0 of 622.7

Indicators:
173.35 of 579.96 GB left -> 172.28/579.96 -> the same
406 GB used -> 407.7 -> the same

I hope someone over here does have a clue and can help me figure out what can be done to get a normal free-/space reading back.


Thanks,
Bart

---

### Post by n0c0d3 on 2018-01-27
I don't know why, but even after two days there's only one view of this post. I had and continued to search for answers on the web, but there was nothing concerning erroneous partition-sizes that seemed applicable to my situation. Therefor I resorted to the the most drastic solution: I copied everything to another (external) drive and deleted and repartitioned the weird partition. Now it seems to be in working order again and am currently copying everything back to the partition again from the other drive.

Too bad there seems to be no solution, but I felt it was best to post a message to let people who enter this thread looking for answers to similar situations know how this ended.

The most useful thread, closest to my situation, I could find was this one (though didn't seem to be useful to me): [https://ubuntuforums.org/showthread.php?t=1122670](https://ubuntuforums.org/showthread.php?t=1122670)

I'm going to leave this thread open for in case someone might find an answer and a solution. It might come in handy one day...


Bart

---

### Post by wildmanne39 on 2018-01-27
Our thread count is not working properly, there has actually been 8 people that have viewed your thread including me.

You can bump your thread every twelve hours to keep your thread in view of people that can help so it does not float into oblivion.

Glad you got it working by any means.

---

### Post by n0c0d3 on 2018-01-27
I'm not going to bump it into eterenity either. But if someone is searching for something similar and finds this post who might have an idea it's worth posting of course for other people. That's why I prefer to keep it open, not because I still need an answer as I've "solved" it the brute-force way already.  

But thanks for clearing the counter-issue up, I really found it weird no one had actually read it. Now the counter shows 3.

Bart

---

### Post by oldfred on 2018-01-27
Best not to use NTFS unless also running Windows.
You cannot run chkdsk nor do a defrag from Linux.

Your copy & restore in effect did a defrag so that may have been part of issue?

NTFS also likes 30% free, Linux does need free space to work well but not quite as much as NTFS.
And NTFS gets slower at 20% free and at 10% free space you just about cannot do a defrag.

---

### Post by n0c0d3 on 2018-01-27
I think the issue was some damage caused by the hard reset while the drive was being used (see my original post). But I may be wrong, and there can always be correlated issues as well.

But the use of NTFS is a kind of legacy thing for me from when I was still regularly using both Linux and Windows. Nowadays I hardly ever use Windows anymore, still I like it to be accessible from Windows as well. I may even need to use Windows because now I have to recover another drive which was working fine while connected to another computer, but after diconnecting it to use as temporary storage for the latest exchange no computer can see it anymore. The recovery-software I have only works on NTFS in Windows and the process takes pretty long. And I have to buy another external drive for that as well. But that's for another day...

Thanks for the advice!

Bart

---

### Post by oldfred on 2018-01-27
New Windows 8 & 10 use fast start up or always on hibernation. And that sets hibernation flag on all NTFS partitions. Or no other system even other Windows then can mount that partition. Have not seen a way in Windows to unmount a partition and have the hibernation not set. 
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Be sure to make a Windows repair/recovery flash drive. Then you may have a way to repair NTFS partitions.
       
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by n0c0d3 on 2018-01-27
I've not plugged in my drives into my windows computers for ages. I've not really looked into what caused the drive to malfunction. Maybe it's the adapter or something else with the powersupply. It's absolutly silent when I plug it in. I'm not in a hurry and I'll look into it when I have the time and feel like it. And besides that, I've never upgraded after Windows 7. I'm a happy Xubuntu for many years now, no need for something else for 99.9% of my time :-)

---

