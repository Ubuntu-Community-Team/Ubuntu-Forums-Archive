---
title: "mounting screwed windows drive to recover data"
date: 2008-07-28
forum: Hardware
---

### Post by braddarb12345 on 2008-07-28
Ive got a dell inspiron 6400 and it was running windows xp home service pack 2 also running now latest version of the live ubuntu 8 not installed but the first option try without installing when u boot the cd

Ive found other threads about this but have got lost in what they were talking about also i ran a few other commands which might help aswell so you wont have to ask maybe.... please help me get my data back

getting a message of

```
ubuntu@ubuntu:~$ sudo /bin/bash
root@ubuntu:~# mkdir /media/disk
root@ubuntu:~# mount -t ntfs-3g /dev/sda2 /media/disk -o force
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

```


also

```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6       14017   112551390    7  HPFS/NTFS
/dev/sda3           14018       14409     3148740   db  CP/M / CTOS / ...

```


anyone help? thanks :)

---

### Post by cdtech on 2008-07-28
What do you get with:

```
dd if=/dev/sda2 of=/dev/null
```

---

### Post by lisati on 2008-07-28
This kind of thing sometimes happens if Windows isn't shut down properly. Try booting Windows, allow the boot process to complete, shut Windows down normally, and then restart Ubuntu.

---

### Post by braddarb12345 on 2008-07-28
i cant boot windows it has some message

pbr2 ...done

thats y im using the ubuntu to get back my data and prob neva use windows again haha

also when i type the code you wrote it cdtech it just returns to the next line with no root@ubuntu:~# or anything or no error that was no a command etc?

wait got sumthing took ages tho b 2 secs and ill post it!!!

---

### Post by braddarb12345 on 2008-07-28
cdtech i got

```
ubuntu@ubuntu:~$ sudo bin/bash
sudo: bin/bash: command not found
ubuntu@ubuntu:~$ sudo /bin/bash
root@ubuntu:~# dd if=/dev/sda2 of=/dev/null
dd: reading `/dev/sda2': Input/output error
10669400+0 records in
10669400+0 records out
5462732800 bytes (5.5 GB) copied, 191.817 s, 28.5 MB/s
root@ubuntu:~# 

```

---

### Post by cdtech on 2008-07-28
> **braddarb12345 said:**
> i cant boot windows it has some message

pbr2 ...done

thats y im using the ubuntu to get back my data and prob neva use windows again haha

also when i type the code you wrote it cdtech it just returns to the next line with no root@ubuntu:~# or anything or no error that was no a command etc?

wait got sumthing took ages tho b 2 secs and ill post it!!!

It takes a bit (depending on how much data you have on that partition)

The point is to see how many bytes were copied also records in and records out. It will not acually copy anything just spit out information.

---

### Post by braddarb12345 on 2008-07-28
did u see the result above?

---

### Post by cdtech on 2008-07-28
I'm thinking trying to run ntfsfix on the sda2 partition through Ubuntu or use your windows install disk to fixmbr. I just got home so not a whole lot of time right now. Try the above, I'll return soon......

---

### Post by braddarb12345 on 2008-07-28
i will try thos thankyou for ur help anyway:)

---

### Post by braddarb12345 on 2008-07-28
tryed them did not work be great if when you are free to maybe keep helping me 
 
thanks.
ill check back if u reply:)

---

### Post by tom66 on 2008-07-28
You said you couldn't boot into Windows, there was an error message. What was this message?

---

### Post by braddarb12345 on 2008-07-28
it was PBR2...done but this does not come up now after the fixmbr atempt with the windows recovery consol i used from previous advice in this thread only a black screen w3ith a underscroe blinking as if it was me to type but u cant do anything....:confused:

---

