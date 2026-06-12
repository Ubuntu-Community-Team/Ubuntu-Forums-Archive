---
title: "Unblocking drives in Ubuntu"
date: 2008-07-26
forum: Hardware
---

### Post by SonicRacer1412 on 2008-07-26
Hello again.

This time, I am having trouble with my CD Drive and my Slave hard drive in Linux. In the beginning, I disabled the second hard drive when I had WinXP on that computer, I tried to get it working again in Linux so I can install OpenSuse on it. Now, I screwed up and can't get to any of my drives. Whenever I insert a CD, I get an error message: "Can't mount volume" and I type in "mount /dev/hdc" (my CD-ROM drive) and I get a long message saying "Device is blocked... see dmesg | tail for more info" or something like that. BTW, my second hard disk is a Samsung.

---

### Post by pytheas22 on 2008-07-26
Please insert a CD and immediately after, open a terminal and type:
```

dmesg | tail
```

and post the output here.  It should help figure out what's wrong.

Also, could you please post the whole error message that you get when you try to mount /dev/hdc?

---

### Post by SonicRacer1412 on 2008-09-19
Sorry it took months to reply...

Anyway, here's the output:
[COLOR="SeaGreen"]
[    33.948000] [drm] Initialized readon 1.27.0 20060524 on minor 0
[    36.036000] agpgart: Found an APG 2.0 Compilant Device at 0000:00:00.0
[    36.036000] agpgart: Putting AGP 2.0 Device at 0000:00:00.0. into 4x mode
[    36.036000] agpgart: Putting AGP 2.0 Device at 0000:01:00.0. into 4x mode
[    36.400000] [drm] Setting GART Location based on new memory map
[    36.400000] [drm] Loading R200 Microcode
[    36.400000] [drm] Writeback test succeeded in 1 uses
[    57.580000] cdrom: hdc: mrw address space DMA selected
[    57.732000] cdrom: hdc: mrw address space DMA selected
[    57.736000] udf: bad mount option "swap" or missing value[/COLOR]

NOTE: This may not actually be the real code. I wrote it down the best I can. I have no internet access on the computer upstairs (the Ubuntu computer), so I can't copy and paste it directly to you (my parents don't feel it's safe to allow me internet access up in my room).

And my main problem happened because I have edited a file (which name I cannot remember, I haven't used the computer since I was last on here). I reverted it, but still no progress.

---

### Post by pytheas22 on 2008-09-19
I googled and am still not certain what's wrong, although this error does seem to pop up in a few other cases.

> And my main problem happened because I have edited a file (which name I cannot remember, I haven't used the computer since I was last on here). I reverted it, but still no progress.

Was the file that you edited /etc/fstab?

Please post the output of the following commands.  Keep in mind that you can copy and paste the output into a text file on Ubuntu (Applications>Accessories>Text Editor), then transfer it via a USB drive or something to a computer that has Internet.
```

cat /etc/fstab
```

and please also post the exact output that you get when you try unsuccessfully to mount the drive at the command-line.

Also, if you boot to a live CD, does the drive work?  If so, what is the output of:
```

cat /etc/fstab
```

when you're running the live CD?

---

### Post by SonicRacer1412 on 2008-09-20
I'm pretty sure the file was /etc/fstab. Besides, I had to revert it manually (I should have saved it as a copy).

---

### Post by SonicRacer1412 on 2008-09-20
Also, I accidentally wiped out all knowledge of WinXP when I screwed up Ubuntu and had to re-install it. I don't know how to tell my uncle, who lended the computer to me, that I accidentally wiped out XP, because he has a short temper sometimes.

---

### Post by pytheas22 on 2008-09-20
> I'm pretty sure the file was /etc/fstab. Besides, I had to revert it manually (I should have saved it as a copy).

If the file that you edit was /etc/fstab, then you should be able to resolve the problem by following these steps:

1. boot to the Ubuntu live CD
2. in the Ubuntu live CD environment, run this command:
```

gedit /etc/fstab
```

A file will open.  Go to "Save As" and save the file to a USB drive, or save it to the desktop and then email it to yourself.

3. log out of the live CD session and boot to your Ubuntu system on your hard drive.  There, find the /etc/fstab that you obtained from the live session and save it to your desktop.  Give it the name 'fstab.LIVE'

4. run these commands to have the fstab file from the live session replace the broken one:
```

cd ~/Desktop
cp /etc/fstab ~/Desktop/fstab.bak
sudo cp fstab.LIVE /etc/fstab
```

Then reboot and see if the issue is fixed.
> 
Also, I accidentally wiped out all knowledge of WinXP when I screwed up Ubuntu and had to re-install it. I don't know how to tell my uncle, who lended the computer to me, that I accidentally wiped out XP, because he has a short temper sometimes.

Did you install Ubuntu in the place of Windows (removing the Windows partition completely), or did you just make it impossible to boot to Windows?  In the latter case things are not that bad.  Under your 'Places' menu in Ubuntu, do you see any drives listed that would belong to Windows (they won't say Windows, but if there's anything there like '20 GB Media' then click on it to see if it's a Windows drive)?

You could also of course just reinstall Windows; it's not that hard.  It would wipe out Ubuntu (you could reinstall it again afterwards and you wouldn't hurt Windows as long as you're careful about which partition Ubuntu gets installed on, or you could install it using [wubi]("http://wubi-installer.org/") to avoid partitioning altogether), but at least you'd make your uncle happy.

---

### Post by SonicRacer1412 on 2008-09-20
The output of:

```
sudo cat /etc/fstab
```

Results:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=a1ac8411-c403-4b34-b522-9b762931949a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=cc6e1895-4d58-4ddb-9b26-5b729d99a0d9 none            swap    sw              0       0
/dev/hdc        /media/cdrom   udf,iso9660 user,noauto,exec,swap                 0       0
```

The output of:

```
sudo cat /etc/mtab
```

Results in:

```
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/sda1 /media/LEXAR\040MEDIA vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0
```

---

### Post by SonicRacer1412 on 2008-09-20
> **pytheas22 said:**
> If the file that you edit was /etc/fstab, then you should be able to resolve the problem by following these steps:

1. boot to the Ubuntu live CD
2. in the Ubuntu live CD environment, run this command:
```

gedit /etc/fstab
```

A file will open.  Go to "Save As" and save the file to a USB drive, or save it to the desktop and then email it to yourself.

3. log out of the live CD session and boot to your Ubuntu system on your hard drive.  There, find the /etc/fstab that you obtained from the live session and save it to your desktop.  Give it the name 'fstab.LIVE'

4. run these commands to have the fstab file from the live session replace the broken one:
```

cd ~/Desktop
cp /etc/fstab ~/Desktop/fstab.bak
sudo cp fstab.LIVE /etc/fstab
```

Then reboot and see if the issue is fixed.


Did you install Ubuntu in the place of Windows (removing the Windows partition completely), or did you just make it impossible to boot to Windows?  In the latter case things are not that bad.  Under your 'Places' menu in Ubuntu, do you see any drives listed that would belong to Windows (they won't say Windows, but if there's anything there like '20 GB Media' then click on it to see if it's a Windows drive)?

You could also of course just reinstall Windows; it's not that hard.  It would wipe out Ubuntu (you could reinstall it again afterwards and you wouldn't hurt Windows as long as you're careful about which partition Ubuntu gets installed on, or you could install it using [wubi]("http://wubi-installer.org/") to avoid partitioning altogether), but at least you'd make your uncle happy.
Well, the XP installation had a lot of programs on it... then again, he might be happy, because it will run faster. Besides, he gave it to me permanently, so I guess I shouldn't worry.

---

### Post by pytheas22 on 2008-09-20
> **SonicRacer1412 said:**
> The output of:

```
sudo cat /etc/fstab
```

Results:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=a1ac8411-c403-4b34-b522-9b762931949a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=cc6e1895-4d58-4ddb-9b26-5b729d99a0d9 none            swap    sw              0       0
/dev/hdc        /media/cdrom   udf,iso9660 user,noauto,exec,swap                 0       0
```

The output of:

```
sudo cat /etc/mtab
```

Results in:

```
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/sda1 /media/LEXAR\040MEDIA vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0
```

Was this the output from the live CD session or from Ubuntu on your hard drive?  If it was from the live CD, then try copying the live CD's /etc/fstab file to your hard drive by following the instructions in post #7.

---

### Post by SonicRacer1412 on 2008-09-21
> **pytheas22 said:**
> Was this the output from the live CD session or from Ubuntu on your hard drive?  If it was from the live CD, then try copying the live CD's /etc/fstab file to your hard drive by following the instructions in post #7.
Nope. It was from the hard drive. And it's fixed now. Thank you, everyone.

---

