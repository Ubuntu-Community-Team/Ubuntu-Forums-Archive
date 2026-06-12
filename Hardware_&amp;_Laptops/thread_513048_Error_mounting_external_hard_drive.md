---
title: "Error mounting external hard drive"
date: 2007-07-30
forum: Hardware &amp; Laptops
---

### Post by thelinux_guy on 2007-07-30
Hi,

I get this error when I try to mount my external disk drive
The drive specs are a 80 GB Western Digital hard drive

Since I don't know how to explain this error I will let the screenshot of the problem do it for me:

[[IMG]http://images6.theimagehosting.com/Screenshot.915.th.png[/IMG]]("http://[URL=http://server6.theimagehosting.com/image.php?img=Screenshot.915.png)"]http://[[IMG]http://images6.theimagehosting.com/Screenshot.915.th.png[/IMG]](http://server6.theimagehosting.com/image.php?img=Screenshot.915.png)[/URL]

Thank you in advance for your help :)

---

### Post by merlinus on 2007-07-30
What is the mount point you created for the drive?

-merlin

---

### Post by thelinux_guy on 2007-07-30
The mount point is /media/disk ( as it says in nautilus )

The drive just stopped working ( Mounting ). Im going to pull all my documents off it on my Windows machine and do a reformat to see if that helps..........

:(

---

### Post by thelinux_guy on 2007-07-30
Anybody? :(

---

### Post by merlinus on 2007-07-30
What is the output of:

```

cat /etc/fstab

```

-merlin

---

### Post by thelinux_guy on 2007-07-30
jason@Kompooter:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=91c5d848-f46b-421b-8626-8d1eae36d1ab /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0b87d74a-53b2-4bc0-9f19-f716f756f896 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
jason@Kompooter:~$ 


What also is weird is that the computer can see the drive. Even when I disconnect the drive Gnome warns me about "unsafe removal of drive" , Well, why would it say that if the drive isn't mounted? weird..........

---

### Post by merlinus on 2007-07-30
Two more commands:

```

sudo fdisk -l
mount

```

(l is a lowercase L)

-merlin

---

### Post by thelinux_guy on 2007-07-30
```
jason@Kompooter:~$ sudo fdisk -l
Password:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11882    95442133+  83  Linux
/dev/sda2           11883       12161     2241067+   5  Extended
/dev/sda5           11883       12161     2241036   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9728    78140128+   c  W95 FAT32 (LBA)
jason@Kompooter:~$ 
```

Ok, There you go.  :)

---

### Post by merlinus on 2007-07-30
You will need to add it to /etc/fstab, but you did not post the output of:

```

mount

```

-merlin

---

### Post by thelinux_guy on 2007-07-30
Oh, Sorry ](*,)

```
jason@Kompooter:~$ mount
/dev/sda1 on / type ext2 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
jason@Kompooter:~$ 

```

---

### Post by merlinus on 2007-07-31
Can you mount the drive manually?  If so, what mount point have you created?

As you can see, it is listed in sudo fdisk -l, so ubuntu is recognizing it, but it is not listed in mount.

-merlin

---

### Post by thelinux_guy on 2007-07-31
When you mean what mount point I have created, what do you mean?

I didn't create a mount point for it, It was created automatically ( /media/disk )

I added it to my /etc/fstab but it still dosen't work.......

But my iPod mounts fine, it there something wrong with the HD's file system?

---

### Post by merlinus on 2007-07-31
> 
jason@Kompooter:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=91c5d848-f46b-421b-8626-8d1eae36d1ab /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0b87d74a-53b2-4bc0-9f19-f716f756f896 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
I do not see it in your /etc/fstab, as posted earlier.

What line did you add?

It should be something like this:

/dev/sdb1 /media/disk vfat iocharset=utf8,umask=000 0 0

-merlin

---

### Post by thelinux_guy on 2007-07-31
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=91c5d848-f46b-421b-8626-8d1eae36d1ab /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0b87d74a-53b2-4bc0-9f19-f716f756f896 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1 /media/disk vfat iocharset=utf8,umask=000 0 0
```

Ok, Sorry. Above is what it looks like as of now. But now when I attempt to mount the drive it says I don't have the permission to do so.....

I'll play around with the permission settings to see if that helps :)

---

### Post by merlinus on 2007-07-31
You may need to use

sudo 

in front of the mount command.

-merlin

---

### Post by johntkucz on 2007-07-31
Kind of a similar problem.

Okay now, 
I'm pretty sure my system can ACCESS the external hd (fiesty fawn installation) to boot from, but it just blinks black screen white cursor indefinitely (no grub errors).
the device ids for that external 80gb hd are 
sda1 = /home
sda2= /
sda3=swap

Whenever I boot from the internal hd (which had windows xp installed on it) it loads grub and gives this error. 
GRUB stage 1.5
Grub loading please wait....
error 22

What is up?  I can't even seem to boot from windows now.  (note upon installing to the external hd, I selected the option to "migrate" the windows account, and that just seemed to create a few empty folders)

---

### Post by thelinux_guy on 2007-07-31
> **merlinus said:**
> You may need to use

sudo 

in front of the mount command.

-merlin

I did. But I still get the same warning about permissions.......

---

### Post by merlinus on 2007-07-31
Can you post the mount command you tried?

-merlin

---

### Post by thelinux_guy on 2007-07-31
```
jason@Kompooter:~$ sudo mount
/dev/sda1 on / type ext2 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
jason@Kompooter:~$ 

```

I think this has something to do with the kernel as I updated my system's kernel just before things stopped working. So, I will download another kernel from the repo's and see if I have any problems doing it that way.

---

### Post by merlinus on 2007-07-31
ok -- let me know what happens.

btw, i was asking how you tried to mount the drive manually, not the "mount" command in a terminal.

-merlin

---

### Post by thelinux_guy on 2007-07-31
Thanks for being patient with me.......

When I would try to mount the drive, I would click on the drives name in Nautilus in the side pane and also in the "computer"  area which would display both the "could not mount" and the "you do not have the permission" messages.

As for the new kernel, I have yet to choose one in Synaptic. But I am convinced that this should solve my problem.

And I just remembered, this happened to me once before on version 6.06 while using the default Ubuntu kernel so this leads me to believe that this might be a bug.

---

### Post by malcorry on 2007-07-31
Hi, I had similar issues with a Western Digital hard drive. Check the drive jumper setting. It should be set to Single, not Master or Slave.
Regards, mal.

---

### Post by thelinux_guy on 2007-07-31
> **malcorry said:**
> Hi, I had similar issues with a Western Digital hard drive. Check the drive jumper setting. It should be set to Single, not Master or Slave.
Regards, mal.

Not to be such a n00b. But how do I do that? :oops:

---

### Post by malcorry on 2007-08-01
The jumper/link is next to the ribbon cable on the front edge of the drive. There should be a sticker on top of the drive showing the settings. If you purchased the drive casing with the hard drive sealed inside then it should be correct. If you assembled it yourself with a hard drive out of a PC then this could be the issue. REgards, Mal.

---

### Post by thelinux_guy on 2007-08-01
Yes. I bought the drive all assembled together, so it should be correct.


Update: The new kernel dose not work. I still get the permissions error.

But I'm in no hurry to get the drive working as I make backups regularly and wont lose anything important :)

---

### Post by NZ-Wanderer on 2007-08-01
You may find this link

[http://ubuntuforums.org/showthread.php?t=403725](http://ubuntuforums.org/showthread.php?t=403725)

May help you a little...

Seems there is a growing problem with external devices not mounting or being seen..

I thought I had solved my problem by editing my fstab, but alas it's come back to haunt me again, so I'm back in the same boat as everyone else.

---

