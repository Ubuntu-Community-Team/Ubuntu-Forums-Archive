---
title: "[SOLVED] Filesystem issues"
date: 2008-09-05
forum: Hardware
---

### Post by d3cline on 2008-09-05
About a week ago, every time i would run Transmission-gtk my system would start locking up and doing all kinds of strange things. After some standard troubleshooting i discovered my ext3 file system has become corrupt. As long as i did not do anything (move, read, delete) to a certain folder containing the anime i was trying to download my system would remain stable. I tried forcing a fsck at boot and it returned a exit code 127. (which a google search lead only to much head scratching) So i did some research and tried booting into the live cd and I ran```
sudo e2fsck -C0 -f /dev/sda3
``` since the folder in question exists on my /home partition. it returned an error that went something like " error reading block xxxx short read, ignore?" and than a "force re-write" after answering yes for about 10,000 of these there was a lot of numbers that flashed by and than the scan completed. I have tried this 5 times now. I have a 500gb drive with 3 partitions a swap at sda1 a 20gb ext3 mounted at / and the rest is mounted at /home. I have tried re-installing Ubuntu (I figured it would be worthless, but i tried it anyway) I have only been using linux for 8 or 9 months now but have been in tech support for both gateway and dell for 3-4 years,(so i have a decent understanding of hardware and file systems) I don't feel in my gut this is hardware failure, since everything else seems to work so long as i do not mess with the folder in question, i have had many reads and writes to the drive in question and i am even using it now and listening to music and it is acting as a samba server as well. I am almost 99% sure it is something wrong with the file system and do not want to format the partition. before i do anything like that i will buy a new HDD and back everything up.  I have done as much research and forum reading as i can, I believe there is a software answer for my issue so i am turning to the forums for help. I am sorry i did not copy + paste any of the terminal outputs verbatim, if it will help i can run the tests again and do this, any ideas would help. it would be important to note i cannot delete or do anything to this folder from the live cd either, but since the OS is loaded from the CD my system does stay stable. I have had may questions and have done all kinds of crazy cool things (jinzora, compiz, cinelerra) with ubuntu since coming over to the light side (linux) about a year ago and this is the first time i have felt i necessary to ask for help here. Thanks for any suggestions  :confused:

---

### Post by d3cline on 2008-09-05
I forgot to note, i have checked the logs for fsck and e2fsck (/var/logs/fsck) and they are always empty, they contain no new information,

---

### Post by d3cline on 2008-09-05
I can't wait for a reply, so i am backing up everything to DVDs and HDDs i have lying around and will reformat, This time i am creating a "scratch" partition that torrents and other data intensive tings can be performed on so i don't have to deal with this again. any insight on why or how this issue could have been caused would be great. I was under the impression the ext3 filesystem was flawless unless hardware failure. I still don't think that is what it is but will post a follow up when the re-format is complete.

---

### Post by d3cline on 2008-09-08
I am a nub, sorry if anyone actually read this post. **Epic Hardware Fail!!**
I backed up everything and deleted the partitions and re-created them and re-installed Ubuntu 8.04. When I started moving data back to the drive the same issues started happening again.

ran in terminal **DO NOT RUN IF YOU HAVE DATA ON THE DRIVE, IT DESTROYED THE FILE SYSTEMS I HAD INSTALLED.** 

```
sudo badblocks /dev/sda3 -s -w -f
```

PWND!!! dead blocks, Mostly at the end of the drive. hope this helps someone.

---

### Post by tytso on 2008-09-09
In the future, if you see filesystem errors, please check your log files, especially /var/log/messages.  If you see lots of kernel messages about disk errors, then you want to do a backup *fast*.   Alternatively, install the smartmontools and set it up to automatically check the health of your disks using S.M.A.R.T.   (Be warned though, S.M.A.R.T. only detects impending catastrophic disk failures about 50% of the time; still, 50% of the time is way better than nothing at all.)

In general, if you see these sorts of errors, there is a distinct chance that the failures will grow expoentially over time, where "time" can be as little as 30 minutes to a few hours.   So running badblocks is not the thing to do.  The best thing to do if you have a spare disk available at least as big as the filesystem is to do a image-level copy (i.e., sudo dd if=/dev/bad-disk of=/dev/good-disk bs=8k conv=noerror,sync).   A better tool to use is ddrescue (in the Universe repository) but if you don't have dd_rescue installed, better to use the dd invocation because dd is always installed.   And as soon as you discover disk errors, it's better to backup first and ask questions later.  The delay in trying to install dd_rescue if you don't have it installed might mean that you lose more data.

---

### Post by dannyboy79 on 2008-09-09
should this get marked as solved?

---

### Post by d3cline on 2008-09-10
Yes i will mark it as resolved. If I was not so scared of data loss,(and the drive only being 6 months old.) I would have used my head and known it was a bad drive instead of posting the forum any way. But man pages answered most of my questions and I appreciate the comment explaining some of the backup options that would have helped me a lot if I didn't already back up everything to a spare drive and DVDs. Although i did check the logs, and had smartmon tools, but it didn't detect anything.(I know I forgot to post :D) and I had no other OS errors whatsoever. That is why I didn't want to admit it was hardware failure. But alas, at least Seagate will honor my warranty. thanks again, Ubuntu is the best!!!

---

### Post by Paretje on 2008-09-23
Yesterday, I installed Xubuntu 8.04 on a computer but I did a mistake in the usernames, and I wanted to reinstall.

Good, but now, when I tried to start, I got the same error. As I see, I have to make an image to an other disk.

No problem, but does this mean that your HDD is broken now, or can you still fix it? If yes: how?

---

### Post by d3cline on 2008-09-23
**if you don't have any important data on the drive **I recommend running 
```
sudo badblocks /dev/sda3 -s -w -f
```
from a live CD. just replace the "/dev/sda3" with your drives/partitions location, typically I run ```
df -h
``` and look for the drive if i am unsure.

badblocks will take a long time to run but it will let you know if the drive is bad. df will tell you what your drive's file system information is, so you can fill out badblocks parameters.

---

### Post by Paretje on 2008-09-24
> **d3cline said:**
> **if you don't have any important data on the drive **I recommend running 
```
sudo badblocks /dev/sda3 -s -w -f
```
from a live CD. just replace the "/dev/sda3" with your drives/partitions location, typically I run ```
df -h
``` and look for the drive if i am unsure.

badblocks will take a long time to run but it will let you know if the drive is bad. df will tell you what your drive's file system information is, so you can fill out badblocks parameters.

OK, so running badlocks, using the information you got from df, has to, repair the system if possible. If the drive is just totally broken, it will tell me?

Thanks!

---

