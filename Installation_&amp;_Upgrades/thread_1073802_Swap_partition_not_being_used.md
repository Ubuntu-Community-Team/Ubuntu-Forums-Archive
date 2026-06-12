---
title: "Swap partition not being used"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by REALfreaky on 2009-02-18
I searched but couldn't find anyone with my seemingly unique problem.

Ok, so here's the deal: After I first installed Ubuntu, I had the plan of slowly moving stuff over from my Windows partition to my Ubuntu partition and occassionally shrinking the Windows one & growing the Ubuntu one.

When I first installed Ubuntu, I used the manual partition creator (I was afraid of it deleting Windows) and I stupidly put the swap partition in between the Windows & Ubuntu ones. So whenever I went to resize them the first time, I had to delete the swap partition and then recreate it at the end of the drive (after the Ubuntu partition). After resizing and everything, I noticed that it now says I have no swap space. (Although I'm not sure if it ever said i had any swap space... I never checked until today.)

There was probably way too much back story there, but basically all I need to know is how to make Ubuntu recognize the swap partition again. The only tutorials I found were for making swap files for use in regular partitions.

Thanks in advance.

---

### Post by cdtech on 2009-02-18
You need to reconfigure your "/etc/fstab" file so it recognizes the location of the swap partition.
```
# /dev/**sda5**
**UUID=f33563e3-48bc-4ec9-9b8c-a4783ed4109a** none swap  sw     0       0
```
Use your own /dev or UUID:
```
blkid
```
and
```
sudo fdisk -l
```
Then just issue the command:
```
swapon -a
```

---

### Post by caljohnsmith on 2009-02-18
If you change your fstab to to use the new swap partition UUID, you should be able to get swap working again, but the disadvantage of that approach is that you probably won't have a Ubuntu splash screen on start up any more. The reason is because the swap partition UUID is hard-coded in all your /boot/initrd images, so you would also have to regenerate all of the initrd images to use the new swap UUID. So instead of taking that approach, I would recommend simply changing your swap partition UUID to the UUID of your original swap partition, and then that should fix everything. To do that, first do:
```
cat /etc/fstab | grep swap
cat /etc/initramfs-tools/conf.d/resume
```
If the swap UUID in both those files agrees, then copy/paste that UUID into the following command:
```
sudo mkswap -U [COLOR="Blue"]<original swap UUID>[/COLOR] /dev/[COLOR="Blue"]sdXY[/COLOR]
sudo swapon -a
```
And of course replace "sdaXY" with the swap partition. Then you should have your swap back and also your Ubuntu splash screen the next time you reboot. You can check to make sure you have swap working with:
```
free
```
And that will show you both your RAM and swap usage. Let me know how it goes or if you run into problems.

---

### Post by REALfreaky on 2009-02-18
Thanks, John. Unfortunately, this happens when I run swapon:
```
shane@shane-laptop:~$ sudo swapon -a
swapon: cannot stat /dev/disk/by-uuid/c1f0cc8f-aaaf-4404-9fb0-ab81d9bd1b03: No such file or directory

```

cdtech's method worked though. I'm not sure I ever had the Ubuntu splash screen... is it the one with the progress bar or no?

---

### Post by caljohnsmith on 2009-02-18
> **REALfreaky said:**
> Thanks, John. Unfortunately, this happens when I run swapon:
```
shane@shane-laptop:~$ sudo swapon -a
swapon: cannot stat /dev/disk/by-uuid/c1f0cc8f-aaaf-4404-9fb0-ab81d9bd1b03: No such file or directory

```

cdtech's method worked though. I'm not sure I ever had the Ubuntu splash screen... is it the one with the progress bar or no?
I'm glad cdtech's method worked OK for you, but do you still have the splash screen with the progress bar on start up? That error you show above might be because you probably have to update your blkid cache file since you changed the swap partition; you can do that with:
```
sudo blkid -c /dev/null
```
How about posting the output of that command, and also please post the output of:
```
sudo fdisk -lu
cat /etc/fstab | grep swap
cat /etc/initramfs-tools/conf.d/resume
```
If the UUID you are using for swap in your fstab does not agree with what is in the resume file, I don't think you will be able to use suspend/hibernate on your computer, and also you probably won't get the splash screen on start up. But merely updating the resume file with the new swap UUID is not enough, you would also have to regenerate all the initrd boot image files. That's why I recommended just changing the swap UUID back to what it originally was, because usually that method is easier.

---

### Post by REALfreaky on 2009-02-18
Here's what happens: (swapon -a still fails)

```
shane@shane-laptop:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="D0782DE7782DCCD2" TYPE="ntfs" 
/dev/sda3: UUID="ba3bf612-8a99-4c9e-9ecb-b6d75e13b6f4" TYPE="ext3" 
/dev/sda5: UUID="c1f0cc8f-aaaf-4404-9fb0-ab81d9bd1b03" TYPE="swap" 
/dev/mmcblk0p1: SEC_TYPE="msdos" UUID="7BBF-109B" TYPE="vfat"
shane@shane-laptop:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x42b142b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   251995589   125997763+   7  HPFS/NTFS
/dev/sda2       307869660   312062624     2096482+   5  Extended
/dev/sda3       251995590   307869659    27937035   83  Linux
/dev/sda4       312062625   312576704      257040   88  Linux plaintext
/dev/sda5       307869723   312062624     2096451   82  Linux swap / Solaris

Partition table entries are not in disk order
shane@shane-laptop:~$ cat /etc/fstab | grep swap
UUID=c1f0cc8f-aaaf-4404-9fb0-ab81d9bd1b03 none            swap    sw              0       0
shane@shane-laptop:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=c1f0cc8f-aaaf-4404-9fb0-ab81d9bd1b03

```

---

### Post by caljohnsmith on 2009-02-18
OK, that looks great; all your UUIDs match so you should be fine, assuming you didn't manually change your resume file to use the new swap UUID. Looks like you're all set. :)

---

### Post by REALfreaky on 2009-02-18
> **caljohnsmith said:**
> OK, that looks great; all your UUIDs match so you should be fine, assuming you didn't manually change your resume file to use the new swap UUID. Looks like you're all set. :)
Sadly, I'm still getting the same error with swapon -a:
```
shane@shane-laptop:~$ swapon -a
swapon: cannot stat /dev/disk/by-uuid/c1f0cc8f-aaaf-4404-9fb0-ab81d9bd1b03: No such file or directory
```
:(

---

### Post by caljohnsmith on 2009-02-18
Try:
```
[COLOR="Blue"]sudo[/COLOR] swapon -a
```
And also post:
```
free
```

---

### Post by REALfreaky on 2009-02-18
Here you go:

```
shane@shane-laptop:~$ sudo swapon -a
swapon: cannot stat /dev/disk/by-uuid/c1f0cc8f-aaaf-4404-9fb0-ab81d9bd1b03: No such file or directory
shane@shane-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       1543476    1419784     123692          0     172656     461672
-/+ buffers/cache:     785456     758020
Swap:            0          0          0
```

---

### Post by caljohnsmith on 2009-02-18
How about rebooting and running the same commands again just to be sure.

---

### Post by REALfreaky on 2009-02-18
Sweet. Didn't have to run anything after rebooting. Thanks alot, man!

```
shane@shane-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       1543476     704412     839064          0      19916     230416
-/+ buffers/cache:     454080    1089396
Swap:      2096440          0    2096440
```

---

### Post by caljohnsmith on 2009-02-18
You're welcome, glad swap is finally working. Cheers and enjoy your Ubuntu install. :)

---

### Post by KingYaba on 2010-05-10
> **caljohnsmith said:**
> If you change your fstab to to use the new swap partition UUID, you should be able to get swap working again, but the disadvantage of that approach is that you probably won't have a Ubuntu splash screen on start up any more. The reason is because the swap partition UUID is hard-coded in all your /boot/initrd images, so you would also have to regenerate all of the initrd images to use the new swap UUID. So instead of taking that approach, I would recommend simply changing your swap partition UUID to the UUID of your original swap partition, and then that should fix everything. To do that, first do:
```
cat /etc/fstab | grep swap
cat /etc/initramfs-tools/conf.d/resume
```
If the swap UUID in both those files agrees, then copy/paste that UUID into the following command:
```
sudo mkswap -U [COLOR="Blue"]<original swap UUID>[/COLOR] /dev/[COLOR="Blue"]sdXY[/COLOR]
sudo swapon -a
```
And of course replace "sdaXY" with the swap partition. Then you should have your swap back and also your Ubuntu splash screen the next time you reboot. You can check to make sure you have swap working with:
```
free
```
And that will show you both your RAM and swap usage. Let me know how it goes or if you run into problems.

Oh perfect! Thank you. :guitar:

---

