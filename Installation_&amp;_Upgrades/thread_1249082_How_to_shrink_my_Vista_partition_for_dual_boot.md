---
title: "How to shrink my Vista partition for dual boot?"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by TraBruno on 2009-08-24
Hello,
 
I'm running Vista 32 bit now on my laptop, but would like to make it dual boot with ubuntu. I found a tutorial that made it look really simple, but I'm stuck at the first step. Computer manager doesn't let me shrink my C: drive, but I read that's natural since it's a lousy partitioning application. I tried with Paragon though and here I get a warning I shouldn't be shrinking in the middle of the hard drive to avoid boot problems. There are 2 partitions now: BOOT (C:/) that has 118 GB NTFS, and RECOVER (D:/) that has 30 GB FAT. There is 40 GB free space on C:/ but this space seems to be locked in between the two partitions. 
Are ther any suggestions to make this work? I'm not very good with computers when I'm stuck at a command prompt so it would be nice to be able to avoid that situation.
 
Another thing: since I didn't get to that stage yet, I'm not entirely sure, but I think paragon formats a partition by default in NTFS, shouldn't that be a problem if you want to use it for ubuntu?
 
Some basic information about these operations would be really nice.
 
Thanks in advance folks!
TraBruno

---

### Post by garvinrick4 on 2009-08-24
Just use wubi.com it will ask you the size of folder for Ubuntu that you want to give it. At least 10 or so to be comfortable if you
have a lot space open use more. More the merrier. Takes a while to
download and it will put a nice little folder in C: the size you wanted. You can use all files from Windows in Linux. Places, file system, host, users, your windows folders. Drag and drop do anything
you want and use your music, videos, documents whatever in Ubuntu. Sets up your grub for you. It is about the simplest thing there is
for dual boot.

---

### Post by raymondh on 2009-08-25
Hello and welcome TraBruno,

Garvinrick has a valid advice ... using WUBI to install ubuntu.  However, please research the pros and cons of a wubi-installed Ubuntu.  Note that your Ubuntu will suffer the same performance problems prevalent in windows.  Also, consider that should windows crash, so does your access to Ubuntu, etc., etc.

The space you were referring to ... is it unallocated now?  Or are you still trying to create space?  You're trying to get space from C: drive, right?  What do you mean "it's locked in between the 2 partitions"?

Assuming that you have tried the liveCD and Ubuntu and are satisfied with how Ubuntu runs in your system....

1.  Save your files / back-up
2.  Take the time to defrag windows C: drive
3.  Vista has a disk management tool.  Use that to shrink the C: partition which will leave you with unallocated space and then install to it.  

OR

1.  Back-up
2.  Defrag Vista.  2x if you have the time.
3.  Boot into the liveCD and install.  When you get to the partitioning stage (step 4), choose GUIDED RESIZE.  It will give you a slider.  Point your mouse at the center (looks like a hash mark), left clcik and use the slider to allocate partition sizes. If satisfied, continue with the install.

post back if you need further clarifications.  BACK-UP :)

---

### Post by oldfred on 2009-08-25
While Wubi has advantages if you just want to learn a little about Ubuntu before trying it, but it is not the real thing. If windows crashes so does Wubi as it is in Windows. 
You should be able to start with as small as 10GB for a new partition for Ubuntu. You should defrag Vista, delete old applications and houseclean in general and use the Vista partitioner to reduce the size of Vista. Back up any important data as partitioning can cause data loss (usually by the user selecting the wrong install - i.e. use entire disk).
When you install ubuntu the partition will be converted to ext3 (or ext4 if you want to live on the edge). I prefer to partition and then use the manual install since you have more control but you do need to be a little more sure of what you are doing.

---

### Post by TraBruno on 2009-08-25
Hello, 
 
First up, thanks for the reactions and suggestions so far, looks like this is the place! 
 
So, I did try wubi, four times actually, but every time I terminated the process when it got stuck for hours at 20%. I suspect there was some problem downloading the iso file, and since I already dwonloaded that file and burned it on a nice live cd, I might as well go with a proper installation. The main reason why I want to switch, at least partly, to ubuntu, is that vista crashes so regularly I'm not sure you can actually call it an operating system at all. Doesn't make sense mounting ubuntu on that system then does it?
 
Anyway. Raymond, you asked me if that space was unallocated. It is not, otherwise I guess I wouldn't really have a problem. There is one hard disc in the computer, divided in a BOOT partition (c:/) and a RECOVER partition (d:/). The problem seems to be that my program seem to think it is unsafe dividing a partition that isn't last on the hard disc, which would be the RECOVER partition. I would rather leave that one alone and cut a piece of the BOOT partition. So what I meant by 'it is locked between two partitions', well, I don't really know what I meant by that now you mention it..:)
Anyway I backed up most of my data, so I guess I'll give your second option a shot. The only thing I'm afraid of is that the dual boot thing will go wrong and I will be stuck with only ubuntu, or nothing at all. I ran a live session of ubuntu and liked it, but my wireless connection didn't work. I copied a bunch of wireless connection troubleshooting text files to a directory that hopefully will be accesible, in case of problems.
 
If ever there are more suggestions about the situation, I won't be going through with it for a few hours at least, and if I do, wish me luck! Hope my next post on the forum won't be from some stinky cyberbar around the corner...
 
See you around!
TraBruno

---

### Post by raymondh on 2009-08-25
> **TraBruno said:**
> 
 
See you around!
TraBruno


I think in Juanty (9.04), the wordings may be SIDE-BY-SIDE instead of Guided Resize.  Nevertheless, there is a hash mark that you have to grab and slide to allocate sizings.  Otherwise, you're left with a 2.5GB install which gives you an error on your first update.

---

### Post by presence1960 on 2009-08-25
here is a screenshot of that slider raymond is talking about, it is the white tab on the far right of the bottom graphic. Grab that with your mouse and drag it left until you have the size you want for ubuntu's partition.

---

### Post by darksniper404 on 2009-08-25
Ubuntu installer does have an option to resize and partion your HD.

---

### Post by louieb on 2009-08-25
> **TraBruno said:**
>  There is one hard disc in the computer, divided in a BOOT partition (c:/) and a RECOVER partition (d:/)....

When you boot with the live CD do you have internet? if so please open Gparted **System>Administration>Partition Editor  **take and put a screen shot in your next post. (press alt+PrintScreen to capture just the Gparted window).  

Is great information have when helping you get Ubuntu installed.

---

### Post by TraBruno on 2009-08-25
Ok, seems like I didn't defragg my drive properly, that was causing the trouble. I did that now, and was able to shrink my boot drive. I have 15 GB unallocated space, so let's install ubuntu!
 
Thanks all, for sure I'll be back in no time with more trouble!
TraBruno

---

### Post by presence1960 on 2009-08-26
> **darksniper404 said:**
> Ubuntu installer does have an option to resize and partion your HD.

FYI there is a known issue with shrinking vista's paertition with gparted and any partitioning software other than vista's built in disk management utility. here is the [link]("http://bugzilla.gnome.org/show_bug.cgi?id=379482").

Gparted live also has a warning that gparted will sometimes resize Vista and sometimes it will not. What happems in a lot of cases is if Vista is not resized by it's own disk management utilty Vista is rendered unbootable.

---

### Post by Bartender on 2009-08-26
> **presence1960 said:**
> What happems in a lot of cases is if Vista is not resized by it's own disk management utilty Vista is rendered unbootable.

That's exactly what happened to me when I tried to resize Vista with GParted LiveCD.

---

