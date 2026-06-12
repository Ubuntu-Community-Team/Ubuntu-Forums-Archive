---
title: "Grub Error 18"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by Greenbeans on 2009-07-09
Hi All,

I am not sure this is the correct forum, but I hope so. First off, I must say that I am completely new to Linux/Ubuntu. I have gone through days of struggle trying to install Ubuntu on my wife's old Sony Vaio laptop. Initially my installations kept failing with Input/Output errors. After trying multiple discs, I took a guess that the drive may be dead. I replaced the hard drive and after many more tries I was finally able to get a succesful install of 9.04. Now when I try booting from the hard drive I get an Error 18 grub error. My searches haven't found anyone else with the error. I tried the standard sudo grub root attempt and it hasn't worked. I don't have anything on my hard drive - its brand new. I don't know if that can be contributing to the problem? I ran the boot info while running off the LiveCD. Here it is:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00038971

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   309,604,679   309,604,617  83 Linux
/dev/sda2         309,604,680   312,576,704     2,972,025   5 Extended
/dev/sda5         309,604,743   312,576,704     2,971,962  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00064b37

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    15,695,504    15,695,442   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="f609f87c-d3e9-4c90-a45c-cd7649d5723e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="4f4b84bd-e692-42bb-9974-53eef0c9811c" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 
/dev/sdb1: UUID="EA0E-34A3" TYPE="vfat" 

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
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f609f87c-d3e9-4c90-a45c-cd7649d5723e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f609f87c-d3e9-4c90-a45c-cd7649d5723e

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        f609f87c-d3e9-4c90-a45c-cd7649d5723e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f609f87c-d3e9-4c90-a45c-cd7649d5723e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f609f87c-d3e9-4c90-a45c-cd7649d5723e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f609f87c-d3e9-4c90-a45c-cd7649d5723e ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f609f87c-d3e9-4c90-a45c-cd7649d5723e
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=f609f87c-d3e9-4c90-a45c-cd7649d5723e /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4f4b84bd-e692-42bb-9974-53eef0c9811c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 149.3GB: boot/grub/menu.lst
 149.3GB: boot/grub/stage2
 149.2GB: boot/initrd.img-2.6.28-11-generic
 149.3GB: boot/vmlinuz-2.6.28-11-generic
 149.2GB: initrd.img
 149.3GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```I beg all of you out there that actually have a clue about this stuff to help me out. My wife is getting close to killing me.... thank you for helping!

---

### Post by merlinus on 2009-07-09
[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

---

### Post by wojox on 2009-07-09
Error 18: Selected cylinder exceeds maximum supported by BIOS

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.

The kernel itself does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem.
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot.

Read more: [http://wiki.linuxquestions.org/wiki/GRUB#Error_18#ixzz0Kjoci2Od&C](http://wiki.linuxquestions.org/wiki/GRUB#Error_18#ixzz0Kjoci2Od&C)

---

### Post by kanhaiya lal panchal on 2009-07-09
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.
[affordable web services.]("http://www.seoguruonline.com")

---

### Post by Greenbeans on 2009-07-09
Thanks for the prompt responses. Based on the wiki page, I am a bit confused. Is my only solution making about 5 different partitions, even if I don't have/want Windows at all? Would this cause any performance issues? If someone could give me the rundown of what I'm actually supposed to do to correct the error, I would reallly appreciate it! The wiki is helpful, but I still feel kind of lost.

---

### Post by Greenbeans on 2009-07-09
Just in case any runs into this thread with a similar problem.

I found this thread (don't know why I couldn't find it before):

[http://ubuntuforums.org/showthread.php?t=1111541&highlight=designate+partition+root](http://ubuntuforums.org/showthread.php?t=1111541&highlight=designate+partition+root)

Now I have Ubuntu up and running. Only problem is that Ubuntu can't find my secondary partition with the bulk of my hard disk space. I am going to try Partition Editor and see if that works... otherwise I may need to do another clean install which isn't too tragic.

Hope this help someone that finds themselves in a similar situation to me. Thanks for the help guys!

---

### Post by 0x29a on 2009-07-09
Now that you've got Ubuntu running, well done! :-)

Your inability to see the rest of your disk sounds like a matter of mounting it somewhere. I typically lay out my hard drive like this:
```

andrew@no-bot:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              21G  6.2G   14G  31% /
varrun               1008M  172K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M   80K 1008M   1% /dev
devshm               1008M     0 1008M   0% /dev/shm
/dev/sda6             107G  101G  6.3G  95% /apps
/dev/sda2             251M  107M  132M  45% /boot
/dev/sda5              21G   14G  6.4G  69% /home
```
If you ignore varrun, varlock, udev, and devshm, you will see how I laid out my partitions. /dev/sda1 isn't listed because it's the swap area. /dev/sda2, however, is mounted as /boot. From your description it sounds like you just need to create a partition and mount it somewhere useful. In my table above I have 107GB mounted as /apps.

The nice thing about this is that even if I reinstall the OS, that partition doesn't need to be erased to do it. In fact, it can be remounted under the new installation by editing /etc/fstab.

Why would I renistall? Well, sometimes I still do stupid things and decide a fresh install is easier than repairing the problem. Typically I only trash my test machine that badly anymore. I tend to not be that cavalier on my primary workstation nowadays. Or, if I just want to install a newer version, or (*gasp*) a different distribution altogether.

One other reason to consider this layout is that back in the ext1/2 days running a fsck on a small /boot partition took a very minimal amount of time as opposed to doing the entire disk. Note my /boot partition is only 250MB, and that's with several old versions of the kernel sitting around.

So, my suggestion would be to run the following to find the rest of your disk:
```

andrew@no-bot:~$ sudo fdisk -l
[sudo] password for andrew:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16331632

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         262     2104483+  82  Linux swap / Solaris
/dev/sda2             263         295      265072+  83  Linux
/dev/sda3             296        2906    20972857+  83  Linux
/dev/sda4            2907       19457   132945907+   f  W95 Ext'd (LBA)
/dev/sda5            2907        5517    20972826   83  Linux
/dev/sda6            5518       19457   111973018+  83  Linux
```
The unused portion of your disk should be readily apparent. Then just figure out where you want to mount it and add it to /etc/fstab. For brevity I'll not get in to that here, but do let me know if this helps, and if you'd like some info on where to go next.

Hope this helps,

Andrew

---

### Post by Greenbeans on 2009-07-09
I am not sure how to run this search? Is it as simple as "sudo fdisk -1"? That's not working for me. Installing Ubuntu was a great achievement, but I'm still basically clueless. I would appreciate so more details on how to accomplish what you're saying. I think I currently have the entire 142gb partition set up as /home. I am not sure what /home is for? Clearly I can't use it to save pictures and documents... A walkthrough with code on how to get my hard drive available for actual disk storage space would be amazing... let me know if you need any more info from me.

---

### Post by Greenbeans on 2009-07-10
df -h works and shows me the following:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.7G  2.6G  986M  73% /
tmpfs                 249M     0  249M   0% /lib/init/rw
varrun                249M  104K  249M   1% /var/run
varlock               249M     0  249M   0% /var/lock
udev                  249M  156K  249M   1% /dev
tmpfs                 249M  696K  248M   1% /dev/shm
lrm                   249M  2.2M  247M   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda6             142G  247M  134G   1% /home
```

I notice that all my randoms are significantly smaller (249mb v 1008mb) than yours. That last part (sda6) is what I want to change. When I try sudo fdisk -l (i tried "1" and "l" it just asks me for my password but doesn't allow me to type anything but press enter? I'm lost from there....

---

### Post by merlinus on 2009-07-10
l is a lowercase L.  When it asks for your password, type it in, although you will not see any characters, and then press Enter.

---

### Post by 0x29a on 2009-07-10
Sorry about that. The command actually uses a lowercase L, instead of a 1 (one), and is run from a terminal window, which is the Linux analog to the Windows command prompt. 

The directory /home is owned by root, so it stands to reason that you can't write to it. If you've set up that 142GB you mentioned as /home you will find the /home directory is analogous to C:\Documents and Settings\ under Windows. For example running:
```
andrew@no-bot:~$ pwd
```
should result in similar output, except with your username in place of 'andrew':
```
/home/andrew
```
User profiles, various program configuration files, and other stuff is stored there. For example, if you open a terminal window (I can't think of what this is called under Gnome) and run (and those are lowercase L's, not 1 (one):
```

andrew@no-bot:~$ ls -l /home
```
you get similar output below:```

total 4
drwxr-xr-x 87 andrew users 4160 2009-07-09 19:54 andrew
```
The 'd' at the beginning of second line means the object listed is a directory, or folder as shown under Nautilus. You should see a directory that matches your username. If you add your wife as a user, her home directory will show up here, too. If you run:
```
andrew@no-bot:~$ls -a /home/andrew
```
You'll see several objects that you normally don't see by just running 'ls' (no quotes).

Just to see what you're working with, open a command prompt, and post the output of:
```
df -h
```

And thanks for the clarification, Merlinus. Sometimes, I think them, but neglect to type things that are rote.
Andrew

---

### Post by Greenbeans on 2009-07-10
Thanks Andrew and thanks Merlinus. I *think* I am starting to understand whats going on. Since I made the entire 142gb /home, is my best bet at this point to reinstall the entire OS? Or can I modify the partition at this point? When I boot off the LiveCD, it does not allow me to mess with the partitions without deleting everything - at that point I'd have to reinstall, no? Or is just messing with the /home partition?

Also, what would be the ideal setup for someone who plans on using Ubuntu exclusively? /boot, /swap,/home are all necessary, right? I know my /boot needs to well under 8gb - what's a good size for the swap and home partitions? Also how do i designate the portion I want to just be a good ol' hard drive?

Thanks for the help guys, I can see the end in sight! I already managed to print wirelessly from Ubuntu to an HP printer - the wife was almost impressed with my meager attempts.

---

### Post by merlinus on 2009-07-10
/boot is not necessary, especially if you are only running one operating system.  /home is definitely needed, for the reasons outlined by Ox29A.  And if you need to reinstall, or want to install a newer version, all the application settings, configurations, browser bookmarks and email are safe, simply by choosing to not format that partition during the installation process, and only formatting / (root), which contains the system files and such.

You can divide your large /home partition into smaller ones, e.g. data, photos, docs, if this will make managing your files easier.  There is no one way -- whatever works for you is best.

/swap need be no more than 1.5G, unless you use the hibernate feature.

As for resizing and/or dividing up existing partitions, you can only do this when they are unmounted.  That is why I prefer to use the gparted live cd, which is bootable, for this purpose.  It also is a more recent version, compared with the one on the live ubuntu install cd, and is a very small download.

Also be aware that an hdd can only have four primary partitions, as opposed to many, many logical ones that reside inside an extended partition.  I think it best to have one primary at the beginning of the hdd, and then an extended for all the rest of the space, and logicals within that.

Here is some good info on partitions:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Greenbeans on 2009-07-10
You guys are great!

I ran gparted LiveCD.... it was MUCH better than whats on the Ubuntu disk. In less than five minutes, I had my /home partition down to 10gb and my 130gb partition that could be mounted. Beautiful! 

My last minor issue is how can I get it to mount automatically at startup? Does it involve editing the mount point? I am not sure if you guys already told me this, its getting late over here. Heck, if I need to click on it to mount, it won't bother me too much. 

Thanks again for all the help - you guys provide better service than most (all) commercial places!

---

### Post by 0x29a on 2009-07-10
@merlinus:
Agreed. /boot, or even /home for that matter, do not need to be contained on their own discrete partition. It just facilitates management, depending on needs. ;) However, /boot and /home will be created automatically as directories unless defined otherwise, because they are required by the OS. But I know you already know this. :)

After looking more closely at the output of you 'df -h' command and seeing that your / (root) partition is 3.7GB with 73% of that 3.7GB already full, you may want to consider reinstalling. The root partition will begin to fill up rapidly as you start adding programs and functionality. I Generally try to make the root partition about 20GB. It's more than enough, and hardly anything in terms of such large drives as exist today.

I don't know that I'd worry too much about splitting /home in to discrete partitions for each user you plan on having, though, unless you plan on both you and your wife having a battle over who can fill the partition the fastest.

I do like having a partition mounted directly off of /. That's the /apps directory you see in my earlier post. I use it to store music, random downloads, and other jive that may need to be accessed and edited by more than a single user.

Getting it to mount at boot time is simple to do during installation. You have to use the expert/manual partitioning option to do it, though. Otherwise, edit /etc/fstab. My /etc/fstab file looks like this:
```

andrew@no-bot:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sdb3
UUID=38ba9d31-bec9-4590-90c4-820d2151a659 / reiserfs nouser,relatime,atime,auto,rw,dev,exec,suid 0 1
# /dev/sdb6
UUID=058cb4e6-aea7-444d-806f-7940054e8ef8 /apps reiserfs nouser,relatime,atime,auto,rw,dev,exec,suid 0 2
# /dev/sdb2
UUID=3738c5bc-326d-482d-8127-1835dcdaa271 /boot ext3 nouser,relatime,atime,auto,rw,dev,exec,suid 0 2
# /dev/sdb5
UUID=3595c5eb-6871-496d-807c-f8e9e2d76ca3 /home reiserfs nouser,relatime,atime,auto,rw,dev,exec,suid 0 2
/dev/sdb1 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,utf8,atime,noauto,rw,dev,exec,suid 0 0
192.168.1.4:/apps /mnt/fembot nfs user,rsize=8192,wsize=8192,atime,auto,rw,dev,exec,suid 0 0
[COLOR="Red"]/dev/sdc1 /mnt/external jfs users,noauto,atime,rw,nodev,noexec,nosuid 0 0[/COLOR]
```
I added /dev/sdc1 manually, therefore it does not have those long uuid numbers that you see on the other devices. They aren't really needed by the OS as long as the filesystem type and other settings are correct. In fact, I never encountered them until I started using ubuntu.

It's late here as well, so we can cover adding that 130GB partition somewhere in your filesystem tomorrow, if you'd like.

Good luck!

Andrew

---

