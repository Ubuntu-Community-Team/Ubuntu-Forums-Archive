---
title: "deleted vmlinuz from /boot, now can not boot anymore"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by baserunner_ams on 2009-05-17
Hello all,

thanks for the help.

I have deleted the vmlinuz files/symlinks from /boot (i was not clearly thinking, thought it had to do with vmware -> dont do such stuff if ur not 100% clear in your head).

I have searched this forum and coulndt find a solution that fits my situation.

my system:
CPU - Quad core intel Q6600
RAM - 4GB
Disks - 3 disk (software raid-raid5 ) /home (md0)
        2 disk (software raid-mirror) / (md3)
          on same disks as / i also have the /boot which is md1
OS - ubuntu 8.04 64-bit 
kernel's 2.6.24-23 and 2.6.24-24

while i was trying to run a update i got the error message that my /boot was full. I have had that before so i wanted to clean it out. decided to remove everything but the last two kernels/version. The vmlinuz files i thought were vmware related and delted them as well...:(

Then rebooted and got (of course) grub error 15, file not found.
Then i new what i did wrong...started to search the forums.

I found following:
[http://ubuntuforums.org/showthread.php?p=6532436]("http://ubuntuforums.org/showthread.php?p=6532436")

and thought that sounds similar enough to give it a try.

I booted with my 8.04-64bit alternate CD, but couldnt connect to network due to driver issues.
So i downloaded the 9.04 versions (also 64-bit) and had another try with the alternate version.
After booting from the 9.04-64bit alternate CD, I selected 'rescue a broken system' and went to the command line in / (md3).
Then i mounted /boot
then i ran:
```
sudo apt-get purge linux-image-2.6.24-24-generic
sudo apt-get install linux-image-2.6.24-24-generic
```

it did clean out my menu.lst and i can boot from the pc but it is not solved yet.

when i boot using the grub option:
Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
I can see that after scanning the scsi bus it sits for a couple second/minutes. (i have not timed how long it takes, i guess it is a kind of timeout for not finding the Hd -> so my guess is that the kernel cant see the software raids)

last line is:
> 
[  25.771357] sd 0:0:0:3: Attached scsi generic sg9 type 0
Done


then i get following messages:
> 
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/md3 does not exist. Dropping to a shell!


BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


I am not an very experienced ubuntu user, although i have setup and installed my system myself.
I need to be sure to NOT loose my data in /home.

while i was searhing the forums i found following link:
[http://ubuntuforums.org/showthread.php?t=1152508&highlight=vmlinuz]("http://ubuntuforums.org/showthread.php?t=1152508&highlight=vmlinuz")

and from that thread i got the info about the
Boot Info Script

the output of that script is as follows (i had to boot with the 9.04-64bit desktop version, as the alternate does not give me the option to boot without altering the existing system):
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => No boot loader is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       mdraid
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'mdraid'

sda2: _________________________________________________________________________

    File system:       mdraid
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'mdraid'

sda3: _________________________________________________________________________

    File system:       mdraid
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'mdraid'

sdb1: _________________________________________________________________________

    File system:       mdraid
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'mdraid'

sdb2: _________________________________________________________________________

    File system:       mdraid
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'mdraid'

sdb3: _________________________________________________________________________

    File system:       mdraid
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'mdraid'

sdd1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdd3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sde1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sde3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4068345c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       208,844       208,782  fd Linux raid autodetect
/dev/sda2             208,845    39,294,989    39,086,145  fd Linux raid autodetect
/dev/sda3          39,294,990   160,071,659   120,776,670  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4068345c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63       208,844       208,782  fd Linux raid autodetect
/dev/sdb2             208,845    39,294,989    39,086,145  fd Linux raid autodetect
/dev/sdb3          39,294,990   160,071,659   120,776,670  fd Linux raid autodetect


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sdd1             132,039       133,005           967  c7 Syrinx
/dev/sdd3       2,147,615,687 2,147,616,653           967  c7 Syrinx

/dev/sdd3 ends after the last sector of /dev/sdd

Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sde1             132,039       133,005           967  c7 Syrinx
/dev/sde3       2,147,615,687 2,147,616,653           967  c7 Syrinx

/dev/sde3 ends after the last sector of /dev/sde

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="ea36c52a-42d0-5cd6-a684-c549b80d0bd6" TYPE="mdraid" 
/dev/sda2: UUID="fca27ca6-f32d-808b-ff35-0840943b001c" TYPE="mdraid" 
/dev/sda3: UUID="bbd60942-f3b5-1e05-5e66-3f37b994a97f" TYPE="mdraid" 
/dev/sdb1: UUID="ea36c52a-42d0-5cd6-a684-c549b80d0bd6" TYPE="mdraid" 
/dev/sdb2: UUID="fca27ca6-f32d-808b-ff35-0840943b001c" TYPE="mdraid" 
/dev/sdb3: UUID="bbd60942-f3b5-1e05-5e66-3f37b994a97f" TYPE="mdraid" 
/dev/sdc: UUID="99152118-c7d0-f2cc-24bf-68e341ce0fbd" TYPE="mdraid" 
/dev/sdd: UUID="99152118-c7d0-f2cc-24bf-68e341ce0fbd" TYPE="mdraid" 
/dev/sde: UUID="99152118-c7d0-f2cc-24bf-68e341ce0fbd" TYPE="mdraid" 

=============================== "mount" output: ===============================

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

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdd1


Unknown BootLoader  on sdd3


Unknown BootLoader  on sde1


Unknown BootLoader  on sde3



=======Devices which don't seem to have a corresponding hard drive==============

sdf sdg sdh sdi 
=============================== StdErr Messages: ===============================

hexdump: /dev/sdd1: No such file or directory
hexdump: /dev/sdd1: No such file or directory
hexdump: /dev/sdd3: No such file or directory
hexdump: /dev/sdd3: No such file or directory
hexdump: /dev/sde1: No such file or directory
hexdump: /dev/sde1: No such file or directory
hexdump: /dev/sde3: No such file or directory
hexdump: /dev/sde3: No such file or directory

```


what should i do next?
what is the best solution--save old system or reinstall os with keeping data in /home?

thanks for all the help
I promise not to do this again ;)

---

### Post by coffeecat on 2009-05-17
> **baserunner_ams said:**
> So i downloaded the 9.04 versions (also 64-bit) and had another try with the alternate version.
After booting from the 9.04-64bit alternate CD, I selected 'rescue a broken system' and went to the command line in / (md3).
Then i mounted /boot
then i ran:
```
sudo apt-get purge linux-image-2.6.24-24-generic
sudo apt-get install linux-image-2.6.24-24-generic
```it did clean out my menu.lst and i can boot from the pc but it is not solved yet.

I think you were almost on the right lines, but what you needed to do was to boot up from a live CD and chroot into the broken system, and then run those two apt-get commands. I'm not familiar with the rescue utility from the alternate CD, but I doubt it's doing a proper install of the kernel which is why you are getting the error messages.

I used to know how to chroot, but I've forgotten the exact sequence of commands. I'll have a look around and post back, or perhaps you could do a little searching for yourself. :wink: And see if you can find an explanation of what chroot is - just to add to your Linux education. :p

> **baserunner_ams said:**
> I need to be sure to NOT loose my data in /home.

One of the first things you need to do is to boot up from a live CD, mount the broken system and copy the data from your home folder onto a USB drive.

---

### Post by coffeecat on 2009-05-17
> **coffeecat said:**
> I used to know how to chroot, but I've forgotten the exact sequence of commands.

I found this:

[http://ubuntuforums.org/showthread.php?p=4640544](http://ubuntuforums.org/showthread.php?p=4640544)

Adapting this to your situation of having to chroot from a live CD, try this:

Boot up from live CD (Use 64-bit if the broken system is 64-bit, 32 if 32). Make sure you're connected to the internet otherwise apt-get won't work. Now go to the Places menu and mount your root partition. Make a note of the mountpoint. I'll assume it's /media/disk, so adjust as necessary if it's different.

Open a terminal and:

```
$ sudo -i
# mount --bind /dev/ /media/disk/dev
# mount --bind /dev/pts /media/disk/dev/pts
# mount --bind /dev/shm /media/disk/dev/shm
# cp -L /etc/resolv.conf /media/disk/etc/
# chroot /media/disk
# mount -t sysfs sysfs /sys
# mount -t proc proc /proc 
# apt-get purge linux-image-2.6.24-24-generic
# apt-get install linux-image-2.6.24-24-generic
# exit
# exit
$ exit
```The $ and # represent non-root and root prompts, so don't type them in. And when you get to the apt-get commands, you don't need sudo because you're already root.

I've added the resolv.conf line otherwise your chrooted environment won't be able to download anything (if it needs to). I'm not 100% sure this will work because the sequence of commands is different from what I've used before.

---

### Post by baserunner_ams on 2009-05-17
thanks a lot.

I will try this.

One question i only have a live cd (were can get into the graphical interface) with the desktop the other one is the alternate CD.
I thought i must use the alternate as i am having the software raids.

I will try with the regular desktop Cd and see if that works....

thanks again

edit:
i dont have a usb device that can hold my data....unfortunatly :(

---

### Post by baserunner_ams on 2009-05-18
hmmm....i got a slight problem....

I went and bought a seagate 1TB USB disk  (External Desktop Drive) so i can backup my data from my raid5.

I booted from the Desktop 9.04 64bit CD (the live CD with the xwindows) and the new USB Disk as recognized as 'Expansion Drive'.
Then i went looking for my data and cant findem.

```
ubuntu@ubuntu:~# sudo -i
root@ubuntu:~# cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
root@ubuntu:~# cat /proc/mdstat
Personalities:
unused devices: <none>
root@ubuntu:~#
```

So i think i will need to boot from the alternate CD to be able to access my raids. Unfortunatly there is no live alternate CD (afaik), so i will have to do all (copy my data from my /home) on the commandline.

How can i do that effectivly? and can i do this in one go (copy data to usb disk, then chroot)?
I think what i did wrong was to not chroot but only use apt-get install...

thanks

---

### Post by coffeecat on 2009-05-18
I'm afraid I've absolutely no experience of RAID, so I can't help you with that one. It seems to me that you've got two issues:

Your need to rescue your data from an unbootable system with a RAID setup, and...

Using chroot to repair the system - which may or may not work.

Of the two I would say rescuing the data is more important. You can always reinstall.

If no one with any experience of RAID joins this thread, may I suggest you start a new one with the emphasis on how you rescue your data? You could always link to this thread to give the background.

Best of luck.

---

### Post by baserunner_ams on 2009-05-19
> **coffeecat said:**
> I'm afraid I've absolutely no experience of RAID, so I can't help you with that one. It seems to me that you've got two issues:

Your need to rescue your data from an unbootable system with a RAID setup, and...

Using chroot to repair the system - which may or may not work.

Of the two I would say rescuing the data is more important. You can always reinstall.

If no one with any experience of RAID joins this thread, may I suggest you start a new one with the emphasis on how you rescue your data? You could always link to this thread to give the background.

Best of luck.

I agree  on the priorities.
Thats why i bought a 1TB usb disk yesterday.
I booted with the alternate 64bit CD.
- mounted my /home dir at /mnt/x (my home is at md0)
- mounted the usb disk at /mnt/backup (it showed up as sdj)
then i tryed copying with (matt is the user that has all data in his home dir ; /home/matt):
```
cp -r /mnt/x/matt /mnt/backup/matt
```

the command was done fairly quickly so i was suspicious.
Decided to do it again with rsync
```
rsync -av /mnt/x/matt /mnt/backup/matt
```

that took a few hours to complete amd ended with an error (code23)
when i re-did  the rsync without the verbose option i got some invalid errors (not at the hardware atm so i cant type the exact errors over) but i guess that either those few files are broken or this is the best i can save.

Tonight i will try to rescue the system as i have now the data copyed to the usb disk (well as much as possible i guess)


thanks for all the help so far.

---

### Post by dave37 on 2009-05-31
> **coffeecat said:**
> I found this:

[http://ubuntuforums.org/showthread.php?p=4640544](http://ubuntuforums.org/showthread.php?p=4640544)

Adapting this to your situation of having to chroot from a live CD, try this:

Boot up from live CD (Use 64-bit if the broken system is 64-bit, 32 if 32). Make sure you're connected to the internet otherwise apt-get won't work. Now go to the Places menu and mount your root partition. Make a note of the mountpoint. I'll assume it's /media/disk, so adjust as necessary if it's different.

Open a terminal and:

```
$ sudo -i
# mount --bind /dev/ /media/disk/dev
# mount --bind /dev/pts /media/disk/dev/pts
# mount --bind /dev/shm /media/disk/dev/shm
# cp -L /etc/resolv.conf /media/disk/etc/
# chroot /media/disk
# mount -t sysfs sysfs /sys
# mount -t proc proc /proc 
# apt-get purge linux-image-2.6.24-24-generic
# apt-get install linux-image-2.6.24-24-generic
# exit
# exit
$ exit
```The $ and # represent non-root and root prompts, so don't type them in. And when you get to the apt-get commands, you don't need sudo because you're already root.

I've added the resolv.conf line otherwise your chrooted environment won't be able to download anything (if it needs to). I'm not 100% sure this will work because the sequence of commands is different from what I've used before.

Thank YOU coffeecat!  That code worked perfectly--I had the same oopsy today--and I'm back up and running, without any loss of data!

---

### Post by coffeecat on 2009-05-31
> **dave37 said:**
> Thank YOU coffeecat!  That code worked perfectly

Whew! I'm so relieved. I'll bookmark this thread in case I have to use the code sometime. :p 

> **dave37 said:**
> --and I'm back up and running, without any loss of data!

I'm glad. :)

---

### Post by baserunner_ams on 2009-06-03
hello all,

well the code did not work for me.

Booting from the HD ended up at:

<initramfs>

I assume that somehow the wrong kernel was installed (without RAID support) although i started the process form the alternate CD and RAID support.

I solved this by reinstall the OS.
Reformating the OS drives but kept the data drives (/home)

I did not loose any data and were up and running in no time.

A nice surprise was that the 9.04 ubuntu was able to recognize the 'fake raid' from my motherboard. So now the mirror (RAID1) is done via that fake raid while the RAID5 is done via software raid.

All works fine
thanks for the help

---

### Post by matzipan on 2010-05-16
Instead  linux-image-complicated number here-generic, you can use linux-image-generic.

Downloading now, fingers crossed.

---

