---
title: "Can't resize/change windoze partition"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by linuxfanboy on 2009-05-25
Hi people...Trying to setup dual boot system. Deleted all partitions including this restore partition (probably) I had... Now it looks like Im missing the space thats around same size as that restore partition....thats a side issue but I'm mentioning it becos it may have to do smth with the problem Im having.

So I delete all partitions and I create one big one for windoze.... I install windoze there. I figure I can always resize it when I add ubuntu....not so.

First I tried this guide

[https://help.ubuntu.com/9.04/switching/installing-partitioning.html](https://help.ubuntu.com/9.04/switching/installing-partitioning.html)

When I right-click on the said windows partition, there is no resize option, there is only edit/delete. According to other guide here

[http://www.easy-ubuntu-linux.com/resize-windows-partition.html](http://www.easy-ubuntu-linux.com/resize-windows-partition.html)

It said right click windoze partition then pick new...but I dont have that option either....

This windows partition is named sda 1 not hda like it said in ubuntu's guide. I also have one other partition named just sda that looks like has no space allocated to it. I didnt make this partition. I only made the windoze one.

Here's the rest of the details for the windoze partition...from disk management in windoze... type basic...file system ntfs...healthy (system)

When I go to properties for the whole hd.... under volumes I get extra bit of info partition style master boot record. Which seems weird.

Thats all the info....basically tried to install ubuntu by going under manual partitioning...then I cant resize the windoze partition. Tried it few times...nothing. Also I cant see a way to resize the partition when I'm in windows. Ive even done defragmenting just to make sure even though I just installed windoze...

Thanks for any suggestions.

---

### Post by Legace on 2009-05-25
Post a screenshot of GParted.

---

### Post by Mark Phelps on 2009-05-25
Don't know what "windoze" is -- you insist on using silly names, you're not going to get much help.  So, is it XP, or is it Vista?  Makes a difference in what you use to resize it.

To do partition work in Linux, you would do better to download and burn a GParted LiveCD from distrowatch.  Also, if you're going to work with NTFS partitions, make sure that the packages ntfs-3g and ntfsprogs are installed as well.

---

### Post by linuxfanboy on 2009-05-25
> **Legace said:**
> Post a screenshot of GParted.

 Just entered gparted using live cd. I cant resize the partition either. Now the option is there, but I can only change the partition by 8mb.  Under information about the partition I get this  ........at least 128 bad sectors. what does that mean? Is that at least like it found 128 and then stopped looking lol or is it an aproximation of how many are there? Total sectors 80 mil so doubt this should make much problems.  

I'm stumbed by this find. I did clean windoze xp install, so during that it should check and repair or bulk those bad sectors together so they're not a problem.  In windoze, Ive also went under properties/tools used error checking....no errors found.  

Here's what gparted suggested....  

run     chkdsk/f/r     and reboot twice.  

Is this different to the error checking under tools? Should I go ahead and do this? The partition holds my windoze install so need to be carefull here. What does that command do?  

And I did have some issues with my HD few years ago, but since then its been ok and I havent lost any data to my knowledge. It couldve just been too much stuff on it or smth bak then.

Thanks for your reply. Lemme know if other info is needed.

---

### Post by linuxfanboy on 2009-05-25
Starting to think this is a bug inside ubuntu 904 live cd or the partitioning software it uses...bunch of other people reported similar issue in this thread.

[http://ubuntuforums.org/showthread.php?t=1167181](http://ubuntuforums.org/showthread.php?t=1167181)

---

### Post by linuxfanboy on 2009-05-26
Follow up....still have same problem. Did chkdsk 3 times in the gui...then 2 more with cmd.

Every time on the final report I would get 512kb of bad sectors, so no idea if it helped.

Then I tried both gparted and installing ubuntu....same problem.

Under info about the windoze partition it said after I ran chkdsk/f/r I could resize ntfs without problem by using -bad sectors in ntfsresize?

Ive got no clue how to do that, new to linux. I only got ubuntu 904 live cd no linux distro installed....can I ran that from the cd?

Also if all fails would clean windoze install help? Is the problem the fact that gparted cant resize ntfs that has errors?

Could I install on ntfs partition that has errors on it? If thats possible how would you recommend partitioning the hd? Ideally I would like 2 windoze partitions, 1 system  1 data and 3 linux partitions so 5 total. But I can only have 4 primary partitions so dunno if that would work well...Guess I could only have 1 windoze partition if I can only have 4...

This is starting to get very frustrating, spent lot of time on this past few days...I may just go ahead with another clean install if that would work.

---

### Post by raymondh on 2009-05-26
> **linuxfanboy said:**
> Ideally I would like 2 windoze partitions, 1 system  1 data and 3 linux partitions so 5 total. 

Hello LinuxBoy

3 separate linux partitions?  You may have your reasons but I ask because a linux partition can be EXTENDED hence giving you the possibility of having as much LOGICAL partitions (for whatever reason) within the main, extended partition.  In that scenario, you will have a total of 3 main partitions (i.e 2 windows and 1 linux)  

Also, it is possible to have 1 windows system partition, 1 data media partition and 1 linux partition and have both windows and linux read tha data/media partition.

Now, are you trying to boot/install some other distros?

Regards,

---

### Post by raymondh on 2009-05-26
Another question for you, did you defrag the drive before installing linux?

---

### Post by linuxfanboy on 2009-05-26
> **raymondhenson said:**
> Hello LinuxBoy

3 separate linux partitions?  You may have your reasons but I ask because a linux partition can be EXTENDED hence giving you the possibility of having as much LOGICAL partitions (for whatever reason) within the main, extended partition.  In that scenario, you will have a total of 3 main partitions (i.e 2 windows and 1 linux)  

Also, it is possible to have 1 windows system partition, 1 data media partition and 1 linux partition and have both windows and linux read tha data/media partition.

Now, are you trying to boot/install some other distros?

Regards,

No by 3 i meant the usual: root home swap. I wanna do them all at once when I do my clean xp install so that later I dont have to resize them. But I dont know if you can install ubuntu on partitions with errors so dunno if that would work.

Also I would like to keep windoze and ubuntu separate to increase security so I dont want them to share data partition... but maybe thats too paranoid or ignorant on my part.

To answer other qs, I wanna dual boot xp and ubuntu 904 and yes I did defragment multiple times even though windoze said I didnt need to.

---

### Post by linuxfanboy on 2009-05-27
What does this do...

using -bad sectors in ntfsresize?

isnt that suppose to resize it minus the bad sectors? How can I start this? Where is ntfsresize? Cant find it on live cd.

Looks like its prolly the last option I have before doing clean xp install.

---

### Post by raymondh on 2009-05-27
here's the manual page for ntsfresize.  It may give you clues about defragmenting and bad sectors.

Ntsfresize is part of the ntsfprogs package

[http://man.linux-ntfs.org/ntfsresize.8.html](http://man.linux-ntfs.org/ntfsresize.8.html)

---

### Post by raymondh on 2009-05-27
> **linuxfanboy said:**
> 
To answer other qs, I wanna dual boot xp and ubuntu 904 and yes I did defragment multiple times even though windoze said I didnt need to.

Apologies ... I should have also stated in my "did you defrag" post that sometimes, defragmenting can put some files at the end of the partition hence making resizing and adventure as some files may be overwritten.

---

