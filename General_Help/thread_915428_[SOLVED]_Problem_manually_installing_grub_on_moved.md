---
title: "[SOLVED] Problem manually installing grub on moved Ubuntu (now on a diff HDD)."
date: 2008-09-09
forum: General Help
---

### Post by Predator106 on 2008-09-09
Hello, I just moved Ubuntu from one hard drive to another, everything is there, permissions correct, I set the HDD I copied everything to as primary in the boot order, and I removed my old hard drive from the boot order just to be sure. All of that was in the BIOS, of course. But now, after booting to that hard drive, I get Error loading Operating System. Yeah, I figured that would happen, I needed to reinstall GRUB on this new HDD.

Well this is what I typed in, this is the hard drive I need GRUB on, but it doesn't want to do it... I can't figure it out...

This is the entirety of what I had done. Well, excluding trying other things to try to get it to work, but this is the example of it...not working :).

I'm on the LiveCD naturally, also.


```

ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeaa4c889

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaf1caf1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux

Disk /dev/sdc: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdd1759df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       18241   146520801   83  Linux

Disk /dev/sdd: 30.0 GB, 30005821440 bytes
255 heads, 62 sectors/track, 3706 cylinders
Units = cylinders of 15810 * 512 = 8094720 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1          11       80293+   0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sdd2              11        3707    29222234+   b  W95 FAT32
    
Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001e542

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       30401   244196001   83  Linux
root@ubuntu:/home/ubuntu# grub-install /dev/sdc
Could not find device for /boot: Not found or not a block device.

```

---

### Post by Predator106 on 2008-09-10
Bump....can't use Ubuntu til' this is fixed :(.

---

### Post by Titan8990 on 2008-09-10
Type the following commands:

sudo grub

Then you will get a grub prompt. From the grub prompt:

root(hd2,0)

setup(hd2)

quit


This assumes that your new install is sdc partition 1.

---

### Post by Predator106 on 2008-09-10
Well, it's not working either:

      ```
 [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root(hd2,0)

Error 27: Unrecognized command

grub> setup(hd2)

Error 27: Unrecognized command


```

---

### Post by -Zeus- on 2008-09-10
> **Predator106 said:**
> Well, it's not working either:

      ```
 [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root(hd2,0)

Error 27: Unrecognized command

grub> setup(hd2)

Error 27: Unrecognized command


```

You need to boot to a live CD, i think.

---

### Post by Predator106 on 2008-09-10
> I'm on the LiveCD naturally, also.

:) Already said that I was :).

---

### Post by caljohnsmith on 2008-09-10
Predator106, from the Live CD, try the following:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That will reinstall Grub to the MBR of your Ubuntu HDD. You may still have to tweak your Grub's menu.lst, but do the above first, reboot, and let us know exactly what happens on start up (any errors, etc).

---

### Post by Predator106 on 2008-09-10
Well, there are two listed, the first one yielded the same startup problem (Grub doesn't load at all, not even a sign of it failing to load), the second one I am trying now. Also note, for other people, you have to have the space in the parentheses, which is really annoying, and I didn't think of it until you posted this and I wondered why it didn't work :).

---

### Post by bodhi.zazen on 2008-09-10
By moving the partition to a new hd, your UUID changed. You will need to manually edit and update /boot/grub/menu.lst and /etc/fstab (update your root and swap partitions).

Easiest way is to use a live CD.

This thread reviews how to do this :

[How to run bleeding edge - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=316237")

And this can help as well. 

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018")

---

### Post by Predator106 on 2008-09-11
So would me not re-doing the HDD's UUID, show the effects of this thread that I made?

Well, the thing is with that problem, I removed all other Hard drives (old ones) and tried to use the new one, and set it as the master HDD, so it should be all good, shouldn't it? It booted into Usplash, just couldn't mount the filesystem...

[http://ubuntuforums.org/showthread.php?p=5770417#post5770417](http://ubuntuforums.org/showthread.php?p=5770417#post5770417)

---

### Post by caljohnsmith on 2008-09-11
> **Predator106 said:**
> So would me not re-doing the HDD's UUID, show the effects of this thread that I made?

Well, the thing is with that problem, I removed all other Hard drives (old ones) and tried to use the new one, and set it as the master HDD, so it should be all good, shouldn't it? It booted into Usplash, just couldn't mount the filesystem...

[http://ubuntuforums.org/showthread.php?p=5770417#post5770417](http://ubuntuforums.org/showthread.php?p=5770417#post5770417)
Yes, if you copied everything over to your new HDD without changing your fstab and menu.lst, you could get the kinds of behavior you are seeing, including not being able to mount the file system. Like bodhi.zazen said, you'll need to update both of those files; but in addition, I believe you'll need to update your initramfs images in /boot, and check two other files listed below if you use your computer's suspend feature.  

Just boot from your Live CD, and do the following:
```
sudo mount /dev/sdXY /mnt

```
Where sdXY is your new Ubuntu partition. Next do:
```
sudo blkid
sudo cp /mnt/etc/fstab /mnt/etc/fstab.backup
gksudo gedit /mnt/etc/fstab &
```
Change the UUIDs in your fstab to match the UUIDs that blkid gives you, making sure you change the UUID of the main Ubuntu partition mounted on root "/" and also the swap partition UUID. Next correct the UUIDs in your menu.lst:
```
gksudo gedit /mnt/boot/grub/menu.lst &
```
Look for your Ubuntu entries:
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		[COLOR="Red"](hdX,Y)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=[COLOR="Red"]UUID=77677cb5-6e56-4936-a373-80c15de06bca[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
Make sure you have the (hdX,Y) correct and also the UUID that corresponds to that partition.

Next you will most likely need to change the UUIDs in the following two files if you have them:
```
gksudo gedit /mnt/etc/initramfs-tools/conf.d/resume &
gksudo gedit /mnt/etc/uswsusp.conf &
```
After you've got all the UUIDs corrected, do the following command to update your initramfs images:
```
sudo chroot /mnt
update-initramfs -u -k all
exit
```
That should be all it takes, but let us know how it goes or if you have more questions.

---

### Post by Predator106 on 2008-09-11
Well this is what my fstab file looks like on the new hard drive... but... it doesn't even display the HDD that it is actually on..

The drive is /dev/sdc1

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=33d87c3e-8b41-4332-82da-43d15be051e3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d391e3d4-8059-40fa-bf90-5497c57db8c7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
########/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Oh crap, I just realized, it doesn't have a swap partition either.... hopefully I can create that in gparted...

So how would I add the HDD's to be the way they should be... Do I just replace the /dev... name, and the UUID and it should be all good, just don't touch the other stuff like realatime, errors, etc.

---

### Post by caljohnsmith on 2008-09-11
> **Predator106 said:**
> 
Oh crap, I just realized, it doesn't have a swap partition either.... hopefully I can create that in gparted...

So how would I add the HDD's to be the way they should be... Do I just replace the /dev... name, and the UUID and it should be all good, just don't touch the other stuff like realatime, errors, etc.
Yes, don't touch anything except the /dev/sdXY references and the UUIDs for those devices. And if you add a swap partition, you'll have to add it to your fstab of course. You could just use a swap file within your new Ubuntu partition, but it is up to you. If you add the swap partition, just add a line to your fstab like:
```
# /dev/[COLOR="Blue"]sdc2[/COLOR]
UUID=[COLOR="Blue"]e01cf0e2-3ae1-42f0-a07f-c5167cba8ae[/COLOR]5 none swap sw 0 0
```
And make sure you use change sdc2 and the UUID to be whatever they should be.

---

### Post by bodhi.zazen on 2008-09-11
List your partitions from a live CD with :

```
sudo blkid
```

Update grub and fstab with the appropriate uuid.

make sure your grub boot stanzas point to the correct hard drive.

---

### Post by Predator106 on 2008-09-13
Alright, thanks, everything is working fine now, perfect.

Thanks everyone, so much, now I'm back to Ubuntu :).

---

