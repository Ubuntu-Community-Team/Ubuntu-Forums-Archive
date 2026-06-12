---
title: "After installation, doesn't reboot"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by froggger on 2009-08-17
After I install ubuntu, i let it do its thing, no custom partitioning, it boots up into the live environment.
No biggie, I reboot, and it acts like it can't find a bootloader.
It just says f1 to retry f2 for setup.

I get one error in the installation process:
```
errno2 no such file or directory: \rofs\usr\directfb-1.0-0\gfxdrivers
```
then, once i boot up, i get 
```
Error activating xkb configuration.
xprop -root grep xkb
gconftool -2 -r
\desktop\gnome-peripherals-keyboard-kbd
```


I installed twice, verified disc on burn and on CD.
I don't know what to do, could I boot into the liveCD and see if its just the bootloader needing to be installed, or edited?

I am using an old random HD for this project, I don't think its bad, but I can't be sure. Could that be the culprit?

Oh, and 9.04 x32.

Thanks!

---

### Post by michael37 on 2009-08-17
Try to either do a recovery boot (see if it works) or boot from a livecd again and get a prompt.

Then, run "sudo grub-install".  I assume you used grub -- anything else for boot loader is kinda outdated.

If you succeed running grub-install and then reboot from HD doesn't work again, I suspect a damaged master boot record on your old HD.

---

### Post by froggger on 2009-08-17
Alright, I'll go try that.

Would a damaged MBR be something that a lowlvl format could sort out?
or would that mean the HD is toast?

Oh, and if its relevant to the diagnosis, the hd used to have XP on it and it started to boot up XP when i installed the HD.

How do I perform a recovery boot?

---

### Post by michael37 on 2009-08-17
> **froggger said:**
> Alright, I'll go try that.

Would a damaged MBR be something that a lowlvl format could sort out?
or would that mean the HD is toast?

Oh, and if its relevant to the diagnosis, the hd used to have XP on it and it started to boot up XP when i installed the HD.

How do I perform a recovery boot? 

A recovery boot option is available from this menu: see pictures at [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

grub-install will rewrite MBR.  Chances are it will work. If it tries and says OK, but then you still can't boot, your MBR on HD might be physically damaged. In that case, nothing you can really do except using another HD.

---

### Post by froggger on 2009-08-17
I don't even get to that stage.
I never see anything about grub.
The message I get is from my BIOS.
I'm currently attempting the livecd method.

---

### Post by froggger on 2009-08-17
Sorry for double post, but it has nothing to do with my last one, so i thought it deserved a new post.
sudo grub-install ouputs this:
```

install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.

```
What should I do?

---

### Post by michael37 on 2009-08-17
> **froggger said:**
> Sorry for double post, but it has nothing to do with my last one, so i thought it deserved a new post.
sudo grub-install ouputs this:
```

install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.

```
What should I do?

Gotta be your device.  Usually /dev/sda or /dev/sdb (SATA) or /dev/hda or /dev/hdb (old ATA).

Try running command "sudo fdisk -l" to see what drives you have in the system.

---

### Post by froggger on 2009-08-17
new error...
```
ubuntu@ubuntu:~$ sudo grub-install /dev/sda1
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

```

---

### Post by michael37 on 2009-08-17
> **froggger said:**
> new error...
```
ubuntu@ubuntu:~$ sudo grub-install /dev/sda1
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

```

MBR is usually on the drive, not on partition.  /dev/sda1 is a partition.  /dev/sda is a drive.  That's what you should be using.

/boot may be also the problem for you.  that's where grub config is located.

Do me a favor, run these commands
cd /boot
pwd
pwd -P

also tell me what command "mount" returns.

---

### Post by froggger on 2009-08-17
First off, Thank you so much for helping me!
and now to the good stuff.

theres the modified  grub install command.
```

ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Could not find device for /boot: Not found or not a block device.

```
heres the next set
```

ubuntu@ubuntu:~$ cd /boot
ubuntu@ubuntu:/boot$ pwd
/boot
ubuntu@ubuntu:/boot$ pwd -p
bash: pwd: -p: invalid option
pwd: usage: pwd [-LP]
ubuntu@ubuntu:/boot$ pwd -P
/boot

```
and here's mount
```

ubuntu@ubuntu:/boot$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


```

---

### Post by michael37 on 2009-08-17
Now I'm double posting, but this may help you understand what I am trying to do.  I am using strategy (IMHO most foolproof I know) to recover MBR from this post: [http://ubuntuforums.org/showpost.php?p=169013&postcount=6](http://ubuntuforums.org/showpost.php?p=169013&postcount=6)

Hope it helps you understand what we are trying to do.

---

### Post by michael37 on 2009-08-17
Linux is case sensitive!  The command is "pwd -P" not "pwd -p" :)  Gotta be careful.  

The mount output actually has all the details to run MBR recovery.  Your sequence of commands is:

1. Boot with any live CD (I've done it with Knoppix 3.x and Ubuntu)
(SKIP, ALREADY DONE) 2. Get a root shell and make a folder 
(SKIP, ALREADY DONE) 3. mount the root (/) partition of ubuntu 
4. chroot the mounted partition (chroot /media/disk)
5. grub-install /dev/hda
5. Exit the shell (exit)
6. Reboot (/sbin/reboot)

---

### Post by froggger on 2009-08-17
```

ubuntu@ubuntu:~$ sudo chroot /media/disk
root@ubuntu:/# grub-install /media/disk
Your /usr is broken; please fix it before calling this wrapper!

```

this just doesn't seem to want to work...

---

### Post by michael37 on 2009-08-17
> **froggger said:**
> ```

ubuntu@ubuntu:~$ sudo chroot /media/disk
root@ubuntu:/# grub-install /media/disk
Your /usr is broken; please fix it before calling this wrapper!

```

this just doesn't seem to want to work...

I believe the script.  Sorry, I don't think your partition (/dev/sda1) has a valid Ubuntu installed.  

Try re-installing again with a careful manual partioning.  Google to find a guide to manual partitioning on Ubuntu.  Otherwise, try another hard drive.  This one may not be worth the time.

---

### Post by froggger on 2009-08-17
Alright, I'll give it one more reinstall before I call it quits for this HD.

Thanks for all the effort.

---

