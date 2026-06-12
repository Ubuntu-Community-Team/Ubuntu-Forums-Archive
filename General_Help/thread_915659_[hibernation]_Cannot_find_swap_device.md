---
title: "[hibernation] Cannot find swap device"
date: 2008-09-10
forum: General Help
---

### Post by Duranxl on 2008-09-10
Hi all.

Well i switched from wubi to normal install using LVPM succesfully.
However i still can't get hibernation to work.
I created a linux-swap partition of 2.5GB (i have 2GBs of ram). And assigned the swap to the partition like this (fstab)
```
/dev/sda5      none            swap    sw              0       0
```

According to free -m, it's working:
```
total       used       free     shared    buffers     cached
Mem:          2013        817       1196          0         24        323
-/+ buffers/cache:        469       1544
Swap:         2557          0       2557
```

However upon hibernation it says: Cannot find swap device, please try swapon -a.

Well, swapon -a doesn't work.
I also tried 
mount -a
swapon -a

to no avail.

Any help?

thanks!!

---

### Post by Duranxl on 2008-09-11
bump

---

### Post by Duranxl on 2008-09-11
Maybe my fstab is wrong?

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda4
UUID=c06b7400-8e88-4259-9a0b-31938eeeb15f     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda2
UUID=AC68407568403FF6       /media/drv0       ntfs-3g         defaults      0   0
/dev/sda5      none            swap    sw              0       0
```

---

### Post by Duranxl on 2008-09-12
```
swapon -s

Filename				Type		Size	Used	Priority
/dev/sda5                               partition	2618552	24	-1
```

Then i found this:

> On success, zero is returned. On error, -1 is returned, and errno is set appropriately.

what's going on?

---

### Post by Duranxl on 2008-09-12
```

wp@wp-laptop:~$ sudo fdisk -l
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          15      120456   de  Dell Utility
/dev/sda2   *          16       16642   133556377+   7  HPFS/NTFS
/dev/sda3           18740       19065     2618595    f  W95 Ext'd (LBA)
/dev/sda4           16643       18739    16844152+  83  Linux
/dev/sda5           18740       19065     2618563+  82  Linux swap / Solaris
```


```
wp@wp-laptop:~$ sudo swapoff -a
wp@wp-laptop:~$ sudo /sbin/mkswap /dev/sda5
Setting up swapspace version 1, size = 2681401 kB
no label, UUID=64d17747-5fd8-4e9a-8b5e-00073d76778b
wp@wp-laptop:~$ sudo swapon -a

```
Yet it doesn't work:confused::(

---

### Post by kaurman on 2008-09-12
Hi!

If /dev/sda5 is swap then do

sudo mkswap /dev/sda5
and then sudo swapon /dev/sda5

If hibernation works right after that then we have something to work with

---

### Post by Elfy on 2008-09-12
Check what UUID you have in /etc/initramfs-tools/conf.d/resume

```
cat /etc/initramfs-tools/conf.d/resume
```

it should match your swap UUID -

If it needs to be changed do so and run this after the change

```
sudo update-initramfs -u
```

[https://help.ubuntu.com/community/UsingUUID#Resuming from Hibernation](https://help.ubuntu.com/community/UsingUUID#Resuming from Hibernation)

---

### Post by kaurman on 2008-09-12
forestpixie's solution is more logical indeed.

Mine is *** as your swap actually works

---

### Post by Duranxl on 2008-09-12
> **forestpixie said:**
> Check what UUID you have in /etc/initramfs-tools/conf.d/resume

```
cat /etc/initramfs-tools/conf.d/resume
```

it should match your swap UUID -

If it needs to be changed do so and run this after the change

```
sudo update-initramfs -u
```

[https://help.ubuntu.com/community/UsingUUID#Resuming](https://help.ubuntu.com/community/UsingUUID#Resuming) from Hibernation
How should my UUID code be the same when i don't have a swap UUID code in my fstab? (see above)
Or do i have to check/change something else?

thanks

---

### Post by kaurman on 2008-09-12
then change the code to /dev/sda5

---

### Post by Duranxl on 2008-09-12
> **kaurman said:**
> then change the code to /dev/sda5

It's already /dev/sda5, right? (please check my fstab file)

---

### Post by kaurman on 2008-09-12
not in fstab, In ...conf.d/resume

RESUME=/dev/sda5

---

### Post by Duranxl on 2008-09-12
> **kaurman said:**
> not in fstab, In ...conf.d/resume

RESUME=/dev/sda5
I changed my resume file to RESUME=/dev/sda5 and then updated via sudo update-initramfs -u..but it didn't work:(

---

### Post by Taxman415a on 2008-09-12
You need to run sudo ```
blkid -c /dev/null
``` or the other methods mentioned in the link in forestpixie's post to get the UUID. Put that in /etc/initramfs-tools/conf.d/resume instead of /dev/sda5
Then you may as well update the UUID in your fstab file as well.

---

### Post by kaurman on 2008-09-13
> **Taxman415a said:**
> You need to run sudo ```
blkid -c /dev/null
``` or the other methods mentioned in the link in forestpixie's post to get the UUID. Put that in /etc/initramfs-tools/conf.d/resume instead of /dev/sda5
Then you may as well update the UUID in your fstab file as well.
Why doesn't using /dev/sda5 work? Basicly it is the same as the UUID code, isn't it?

---

### Post by Duranxl on 2008-09-13
> **kaurman said:**
> Why doesn't using /dev/sda5 work? Basicly it is the same as the UUID code, isn't it?
That's what i thought?
Most of the threads with hibernation problems recommend to change the UUID code to a /dev code!

---

### Post by kaurman on 2008-09-13
Hm...

[quote="Duranxl"]

```
total       used       free     shared    buffers     cached
Mem:          2013        817       1196          0         24        323
-/+ buffers/cache:        469       1544
Swap:         2557          0       2557


```

[/quote]

To me it seems a bit odd that there is no free swap.


I'd still recommend using /dev/sda5 as a reference in both files.
I am not an expert but I would do the following:

Backup the files you mess with just in case something happens!

1) Make sure that the only line in /etc/initramfs-tools/conf.d/resume is RESUME=/dev/sda5 
2)Now I'd still try sudo mkswap /dev/sda5 and then sudo swapon /dev/sda5

---

### Post by Duranxl on 2008-09-13
> **kaurman said:**
> Hm...



To me it seems a bit odd that there is no free swap.


I'd still recommend using /dev/sda5 as a reference in both files.
I am not an expert but I would do the following:

Backup the files you mess with just in case something happens!

1) Make sure that the only line in /etc/initramfs-tools/conf.d/resume is RESUME=/dev/sda5 
2)Now I'd still try mkswap /dev/sda5 and then sudo swapon /dev/sda5
I already tried the /dev/sda5 in resume and mkswap/swapon /dev/sda5. but it didn't work

---

### Post by Duranxl on 2008-09-13
Okai:
[B]
blkid -c /dev/null[/B]
```
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0908" TYPE="vfat" 
/dev/sda2: UUID="AC68407568403FF6" TYPE="ntfs" 
/dev/sda4: UUID="c06b7400-8e88-4259-9a0b-31938eeeb15f" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="64d17747-5fd8-4e9a-8b5e-00073d76778b" 
```

**/etc/initramfs-tools/conf.d/resume**
```
RESUME=UUID=64d17747-5fd8-4e9a-8b5e-00073d76778b
```

**/etc/fstab**
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda4
UUID=c06b7400-8e88-4259-9a0b-31938eeeb15f     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda2
UUID=AC68407568403FF6       /media/drv0       ntfs-3g         defaults      0   0
# /dev/sda5
UUID=64d17747-5fd8-4e9a-8b5e-00073d76778b    none            swap    sw              0       0
```

**free -m**
```
   total       used       free     shared    buffers     cached
Mem:          2013        723       1290          0         17        299
-/+ buffers/cache:        406       1607
Swap:         2557          0       2557
```


[B]
Result: swsusp: cannot find swap device[/B]

---

### Post by Duranxl on 2008-09-13
Sorry for making another post, but i just tried
```
swapoff -a
mkswap /dev/sda5
swapon /dev/sda5
swapon -a
```

once again.. and the *Cannot find swap device* went away!!
So i turn on my laptop again, and it seems it's resuming. (startup procedure is different) 
But once i get into ubuntu all my previous stuff is gone.. like it has been shutdown.:confused:

ARg why doesn't this just work!?

---

### Post by Elfy on 2008-09-13
@kaurman - Don't forget to move the  > total       used       free     shared    buffers     cached along a bit - to me the free -m says op has used 0 of the swap

---

### Post by Elfy on 2008-09-13
I  would return to the start, get the swap as a UUID - set fstab to use UUID then reboot, make sure that swap is recognised from then.

Only go to the hibernate part once you know that swap is working - reset as UUID in the RESUME= and update initramfs again.

---

### Post by Duranxl on 2008-09-13
How do i check if it's recognized? free -m already says it's recognized, right?

---

### Post by Elfy on 2008-09-13
Ye I know it is at the moment - I want you to set it as a UUID instead of /dev in /etc/fstab - then reboot, to make sure there are no errors.

Once that is ok and it is recognised as such in free -m _then_ change RESUME= in the other file, not foregetting to run the update initramfs command, then reboot again.

---

### Post by Duranxl on 2008-09-13
> **forestpixie said:**
> Ye I know it is at the moment - I want you to set it as a UUID instead of /dev in /etc/fstab - then reboot, to make sure there are no errors.

Once that is ok and it is recognised as such in free -m _then_ change RESUME= in the other file, not foregetting to run the update initramfs command, then reboot again.

Ok here's what I did:
1) sudo blkid -c /dev/null: ```
/dev/sda5: TYPE="swap" UUID="e1854fc7-11a6-4070-93cf-f92948bb3311" 
```

2) fstab: 
```
# /dev/sda5
UUID=e1854fc7-11a6-4070-93cf-f92948bb3311   none            swap    sw              0       0
```

3) Reboot

4) Resume file:
```
RESUME=UUID=e1854fc7-11a6-4070-93cf-f92948bb3311
```

5) sudo update-initramfs -u 

6) Reboot

7) Hibernate (no errors!)

**But when i boot again, it doesn't resume..it just boots up.**
Btw, for some reason i don't see the ubuntu-bar anymore but i have a code-view of what happens. (even with normal reboot)


:(

---

### Post by Elfy on 2008-09-13
Ok - so now we know that the swap is working correctly. The hibernate issue is I think a seperate one, I don't do it myself but there are more than a few threads on it.

Can you let us know what hardware you're using - pc/laptop model it might be a specific issue, also I've been assuming you are using hardy (8.04) - can you confirm that if you're not sure run ```
lsb_release -a
```

---

### Post by Duranxl on 2008-09-13
> **forestpixie said:**
> Ok - so now we know that the swap is working correctly. The hibernate issue is I think a seperate one, I don't do it myself but there are more than a few threads on it.

Can you let us know what hardware you're using - pc/laptop model it might be a specific issue, also I've been assuming you are using hardy (8.04) - can you confirm that if you're not sure run ```
lsb_release -a
```

Yes i'm running Hardy 8.04 64bit.

Laptop:
Dell Vostro 1500
Intel Core2duo T7300
2GBs of RAM
NVIDIA 8600M GT with EnvyNG driver 173.14.12 (proprietary didn't work)
Intel 3945 Wireless

---

### Post by Duranxl on 2008-09-13
Hm i just installed uswsusp and did sudo s2disk and then it got stuck.
BUT!! when i turned my laptop on again it worked:confused::)


So i just have to make sure it doesn't hang when i hibernate

---

### Post by Duranxl on 2008-09-13
guys! i tried s2disk once more and...IT WORKED :o
It shutdown properly and resumed properly as well!!
I guess my initial problem still persists..but using another hibernation program fixed it.
Should I change it to [solved]?

---

### Post by earther on 2010-12-12
> **forestpiskie said:**
> Check what UUID you have in /etc/initramfs-tools/conf.d/resume

```
cat /etc/initramfs-tools/conf.d/resume
```

it should match your swap UUID -

If it needs to be changed do so and run this after the change

```
sudo update-initramfs -u
```

[https://help.ubuntu.com/community/UsingUUID#Resuming from Hibernation](https://help.ubuntu.com/community/UsingUUID#Resuming from Hibernation)
Over 2 years later and still useful info for us lingering Hardy users.  Thank you!

---

### Post by junk3r on 2011-10-05
Whoohoo!

Have similar problem with natty 11.04.

No resume after hibernate, just go normal boot with new session...
in kern.log 
```
PM: Hibernation image not present or could not be loaded.
```In /etc/initramfs-tools/conf.d/ i dont have any file, so i create file "resume" with one line ```
RESUME=/dev/sda3
```then
```
sudo update-initramfs -u
```And got resume from hibernate!
I'm happy. Thank you very much :)

---

