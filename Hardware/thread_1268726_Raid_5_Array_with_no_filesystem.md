---
title: "Raid 5 Array with no filesystem"
date: 2009-09-17
forum: Hardware
---

### Post by sunpyo on 2009-09-17
A lot of you may know I'm having this problem accessing information on my Raid 5 Array. I've done a lot of things and finally resorted to trying out #mdadm --create... 
 
However when I attempted there was no indication of a filesystem. Seeing that nothing was recognized, I decided not to create the array. Normally something like filesystem is recognized or something of that nature would come out, however there is no indication of it.
 
I know that the filesystem in this array is an ext3. I confirmed it with WD. (These HD were taken out of a NAS drive called a "WD NAS ShareSpace". Here are some things that people have been suggesting, here are certain ways I've thought of doing correcting this:
 
First I can try to do the #mdadm --create. I have already tried #mdadm --assemble and the raid is created, however I cannot mount or see any of the files inside. When I do this command:
 
```
 
#mdadm --create /dev/md2 --level=5 --raid-devices=4 missing /dev/sdb4 /dev/sdc4 /dev/sdd4
mount: /dev/sdb4 appears to be part of a raid array
level=raid5 devices=4 ctime=Fri Apr 3 03:55:58 2009
mount: /dev/sdc4 appears to be part of a raid array
level=raid5 devices=4 ctime=Fri Apr 3 03:55:58 2009
mount: /dev/sdd4 appears to be part of a raid array
level=raid5 devices=4 ctime=Fri Apr 3 03:55:58 2009
Continue creating array? n

```
 
Seemed useless in my eyes if there were not going to be any sort of filesystem. People also suggested that I can do this:
 
```
 
#fsck.ext3 -cc -f -v -y /dev/md2

```
 
However I don't know what this does and I'm afraid of losing data. Also this is a pretty huge device. When the raid is assembled it is close to 6 TB or so. Any input would be appreciated. [Here's stats and stuff if you guys need to see it.]("http://www.linuxquestions.org/questions/linux-server-73/help-with-wd-nas-recovery-4-x-2.0-tb-raid-5-755401/")

---

