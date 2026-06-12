---
title: "Upgrade from Hardy to Intrepid was interrupted"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by doobiest on 2009-10-05
Hi, I just tried to do an upgrade from hardy to intrepid today and X crashed half way through the process.

using dpkg/apt I was able to clean up the garbage and continue on upgrading the packages. I am able manually get my way into an X desktop and the system reports as intrepid now.  There was a lot of broken stuff I had to fix, all looks good now except when I start linux it failed to mount my root partition as rw, stays in read only.

I've messed with my fstabs/grub menu and ran some commands for update-initramfs as suggested on some old posts on here. and it still doesnt work.

Unfortunately I cannot past what I'm seeing on screen as I don't see that logged anywhere. but to summarize, when grub chooses to load ubuntu, a few init lines appear, and then it outputs what you would see in mount --help.

Essentially it looks like the mount command, which would normally take the root partition from ro to rw is failing.  It makes me believe something is syntactically incorrect, since it's printing the --help output.

Here's my fstab and grub.  Can anyone tell me what's wrong and maybe tell me how to force update-manager to redo a dist upgrade to intrepid?

Also I've tried replacing the UUID's with /dev/sda2 just to see if that would work.

One more odd thing to note is when I choose ubuntu 8.10 recovery it does successfully mount the root as rw, and I don't see a difference between them.

Thanks.


```
FSTABS

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda2
#/dev/sda2 /               ext3    relatime,errors=remount-ro 0       1
#/dev/sda2	/	ext3    errors=remount-ro 0       1

/dev/sda2 /               ext3    defaults,errors=remount-ro,relatime 0       1

# /dev/sda3

/dev/sda3 none            swap    sw              0       0

#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sda1	/media/NTFS	ntfs defaults


GRUB

default		0

timeout		10

splashimage (hd0,1)/boot/grub/splashimages/debian-moreblue-swirl.xpm.gz 

title		Ubuntu 8.10, kernel 2.6.27-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=a7c65cf3-42ff-4af3-affc-cfec79f3ae92 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=a7c65cf3-42ff-4af3-affc-cfec79f3ae92 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.24-24-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=a7c65cf3-42ff-4af3-affc-cfec79f3ae92 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=a7c65cf3-42ff-4af3-affc-cfec79f3ae92 ro  single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.10, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=a7c65cf3-42ff-4af3-affc-cfec79f3ae92 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=a7c65cf3-42ff-4af3-affc-cfec79f3ae92 ro  single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=a7c65cf3-42ff-4af3-affc-cfec79f3ae92 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=a7c65cf3-42ff-4af3-affc-cfec79f3ae92 ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a7c65cf3-42ff-4af3-affc-cfec79f3ae92 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a7c65cf3-42ff-4af3-affc-cfec79f3ae92 ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by doobiest on 2009-10-05
Addendum:

I was wrong about the mount --help not outputting when I go into recovery mode. It does, I just didn't notice it.

However in recovery mode, if I choose to drop to a root console, by time I do that everything is mounted rw.  Testing by 'touch /test' completing successfully.

From the root console I do:

mount -a -o remount

this verifies that fstabs must be OK since it remounted all devices without error.

From there I:

init 2

Which boots me into a multiuser environment with an X desktop.

Another clarification is when I do a normal boot, the mount --help output appears 3 times which I assume is for the 3 devices it's trying to mount.

What would make the mount binary used a boot fail?  Any thought?

Also I've tried booting previous kernel versions with no success

---

### Post by doobiest on 2009-10-05
This is what I mean by the --help being output on screen. And by on screen I mean the text output when booting the system.

```
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
```

---

### Post by louieb on 2009-10-05
Two more ideas.

Remove the "quite splash" from the kernel line in menu.lst. Lets you see all the messages.

Remove the relatime option from / (roots) entry in fstab. My Hardy install does not have that option. 

```
/dev/sda2   /      ext3    defaults,errors=remount-ro 0       1

```

---

### Post by doobiest on 2009-10-05
I'm not using relatime, that lines commented out. I'm using:

defaults,rw,errors=remount-ro,relatime

I was running it without the splash, I will try it without quiet.

I have a feeling this has to do with initramfs being messed up, if anyone knows about that. However I'm not sure why the old kernels wouldnt work if that's the case. Unless initramfs is global and not per kernel

---

### Post by doobiest on 2009-10-05
Without quiet I get something along the lines of

running /scripts/init-bottom
then followed by the mount --help output.

I've noticed that the --help output actually occurs further down the boot process as well.

Anyway one other retraction I must print is that a regular boot does go straight into X, so the filesystem is getting mounted rw at somepoint but not til much later in the boot process.

Once again making me think it's something ramfs related?

---

### Post by doobiest on 2009-10-05
can anyone point me towards how to rebuild my entire boot dir from scratch? I can't find anything on google useful.  I mean recreating initrd, vmlinuz, etc, etc.

---

### Post by louieb on 2009-10-06
Haven't had to try it myself but you might try reinstalling the latest kernel. 
```
sudo apt-get --reinstall install <package-name>
```Not sure what package you need to reinstall - just have to look in Synaptic to fine latest kernel you are using (might try reinstalling the **linux-generic **meta package).

---

### Post by doobiest on 2009-10-06
Actually I did try that last night based on another article I was reading. 

doing a reinstall or purge on 

linux-headers-2.6.27-14-generic 
linux-image-2.6.27-14-generic 
linux-restricted-modules-2.6.27-14-generic 
linux-ubuntu-modules-2.6.27-14-generic  
grub

will rebuild most of the /boot directory.

Anyway that wasn't it I figured out what it was.  These two scripts in /etc/init.d were corrupted, if I ran them manually it would output the mount --help behavior.

/etc/init.d/mountdevsubfs.sh
/etc/init.d/mountkernfs.sh

This adds up as both of these are called in the /etc/rcS.d folder which is executed right away before any runlevel is executed. Makes sense as I was seeing this error early in the boot process and before many services start.

I replaced these from an existing 8.10 install on another computer and now things are fine.

Hopefully all my botched upgrade issues are gone.

---

