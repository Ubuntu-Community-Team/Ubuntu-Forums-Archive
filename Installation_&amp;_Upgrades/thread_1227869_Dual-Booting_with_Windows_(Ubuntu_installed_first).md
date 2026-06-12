---
title: "Dual-Booting with Windows (Ubuntu installed first)"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by PooAvenger on 2009-07-31
OK so here's my sob story lol. This process began a few hours ago and now I'm all out of ideas lol.

So I have a hard disk with Ubuntu installed on it's entirety. I want to dual boot with xp for things I cant do on Ubuntu (game, c# coding for certain projects, etc.) and I tried formatting a new partition onto the disk with some spare space and then loaded my xp disk and it stated the disk was an Unknown Disk and that there wasn't any partitions there that I could install on. So I don't know what to do, I tried the recovery console and trying mkdir and trying to format the partition I'm meaning to use for Windows as ntfs and unformatting it but nothing I do works. I can't get the installation program to see any of my disks partitions. Anyone else have this problem? Can anybody help me?

---

### Post by wojox on 2009-07-31
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

---

### Post by presence1960 on 2009-07-31
Boot from Gparted Live CD or Ubuntu Live CD. If Ubuntu Live Cd choose "try ubuntu without any changes...", when the Desktop loads open a terminal and run ```
gksu gparted
``` or go System > Administration > Partition Editor.

Make sure your unallocated space is enough to install windows to. if it isn't you are going to have to create some more space by shrinking your ubuntu partition.

When that is done create a new NTFS primary partition from that space. Then try booting the windows installation disk and choose the new partition to install windows to.

If that does not work we may need a little more info about your setup and your machine.

P.S. while your at it boot into ubuntu and run this command > sudo fdisk -l that is a lowercase L. Post the output back here and we'll see what your partition scheme is.

---

### Post by PooAvenger on 2009-07-31
Ok so I tried deleting the ntfs partition and doing it again but the windows setup still comes up with that unknown disk <a disk is not in the drive> message and wont allow me to mess with partitions.

I did the fdisk, here is the results:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb02f3de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12569   100960461   83  Linux
/dev/sda2           18705       19457     6048472+   5  Extended
/dev/sda3           12570       18704    49279387+   7  HPFS/NTFS
/dev/sda5           18705       19457     6048441   82  Linux swap / Solaris

Partition table entries are not in disk order


Anyway, thanks for your help.

---

### Post by ronparent on 2009-07-31
This is just something I am experiencing and I don't know if it pertains to your problem. I had aquired a 32 Gb usb key to Install ubuntu to and used gparted to partition it with a 10Gb ext3 partition for installing ubuntu to. So far so good. I got ubuntu installed and it boots fine on any of my computers. The remaining space was just the fat32 partition on the drive I had shrunk to make roon for ubuntu and I expected to be able to access from both ubuntu and windows as a common storage space. To make a long story short, I have subsequently discoverd that none of my windows installation will recognize the usb key as having any formatted space! Neither will any windows based disk partitionerl recognize the drive as being already formatted!? I am on the verge of reformatting the drive with a windows based partitioner and reinstlling ubuntu after the fat32 partition in the hopes I'll end up with a key that is readable by both a windows and ubuntu environment. This suggests that for some strange reason that a disk formatted for use exclusively with ubuntu and later partitioned to include windows is unreadable to windows. I plan on following this thread with interest to see what may be at play here.

PS: Is the ntfs partition actually within the extended partition? Installing XP to and extended partition can also be a problem.

---

### Post by PooAvenger on 2009-07-31
I resized the extended partition to allow space for the ntfs one so it shouldn't actually be within it but at this point idk. I did install ubuntu over the entire hard disk originally so maybe windows is just being a dirty skank and not letting me install it because of that >.< . If that's the case is there any way I can just wipe the hard disk entirely so I can try windows and then dual boot ubuntu from there? I heard about something called Killdisk that does something like that, anybody have any experience with that? Just trying to keep all my options open.

---

### Post by merlinus on 2009-07-31
dban works well for completely wiping your hdd.

[http://dban.org](http://dban.org)

---

### Post by PooAvenger on 2009-07-31
*Bump for more ideas*

---

### Post by presence1960 on 2009-08-01
> **PooAvenger said:**
> Ok so I tried deleting the ntfs partition and doing it again but the windows setup still comes up with that unknown disk <a disk is not in the drive> message and wont allow me to mess with partitions.



the "a disk is not in the drive" error sounds like a problem with your optical drive. Is that an original windows CD/DVD or did you burn a copy?

P.S. Ok I think I misread your post. It says the windows installer is giving you that message so it probably isn't the optical drive.

---

### Post by PooAvenger on 2009-08-01
Yea I don't think it's the optical drive since the installer program is giving me that message.

IDK it just sounds like because I didn't partition the disk originally and just installed Ubuntu over all of it I'm screwed and will need to wipe my disk to get it to dual boot. Is this what it's gonna come down to?

---

### Post by presence1960 on 2009-08-01
> **PooAvenger said:**
> Yea I don't think it's the optical drive since the installer program is giving me that message.

IDK it just sounds like because I didn't partition the disk originally and just installed Ubuntu over all of it I'm screwed and will need to wipe my disk to get it to dual boot. Is this what it's gonna come down to?

I know things can be a real pain when you can't get stuff to work. But to get a clearer picture of your setup and boot process can you boot into Ubuntu and download to your desktop the [Boot Info Script 0.32]("http://sourceforge.net/projects/bootinfoscript/")
Once downloaded to desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on your desktop. paste the entire contents of that file back here. Once pasted here highlight all text pasted and click the # sign on the toolbar to place code tags around the text. This will give us way more infoabout your set up & boot process than individual commands.

---

### Post by PooAvenger on 2009-08-02
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeb02f3de

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   201,920,984   201,920,922  83 Linux
/dev/sda2         300,479,760   312,576,704    12,096,945   5 Extended
/dev/sda5         300,479,823   312,576,704    12,096,882  82 Linux swap / Solaris
/dev/sda3         201,920,985   300,479,759    98,558,775   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ffc810

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   625,121,279   625,121,217   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="e6e6c703-6039-4208-a9de-12955f01ce38" TYPE="ext3" 
/dev/sda3: UUID="57C09EAC16D48B60" TYPE="ntfs" 
/dev/sda5: UUID="fa81b8b6-0ad0-47d4-864c-cd5152afd77f" TYPE="swap" 
/dev/sdc1: LABEL="My Book" UUID="3495-3602" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-14-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ben/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ben)
/dev/sdc1 on /media/My Book type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sda3 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=e6e6c703-6039-4208-a9de-12955f01ce38 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=e6e6c703-6039-4208-a9de-12955f01ce38 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=e6e6c703-6039-4208-a9de-12955f01ce38 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e6e6c703-6039-4208-a9de-12955f01ce38 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e6e6c703-6039-4208-a9de-12955f01ce38 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e6e6c703-6039-4208-a9de-12955f01ce38 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e6e6c703-6039-4208-a9de-12955f01ce38 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=e6e6c703-6039-4208-a9de-12955f01ce38 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=e6e6c703-6039-4208-a9de-12955f01ce38 ro  single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e6e6c703-6039-4208-a9de-12955f01ce38 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=fa81b8b6-0ad0-47d4-864c-cd5152afd77f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   5.1GB: boot/grub/menu.lst
   8.8GB: boot/grub/stage2
   8.8GB: boot/initrd.img-2.6.24-22-generic
   8.8GB: boot/initrd.img-2.6.24-22-generic.bak
   8.8GB: boot/initrd.img-2.6.27-11-generic
  86.7GB: boot/initrd.img-2.6.27-14-generic
   8.8GB: boot/initrd.img-2.6.27-9-generic
   8.8GB: boot/vmlinuz-2.6.24-22-generic
   8.8GB: boot/vmlinuz-2.6.27-11-generic
  85.6GB: boot/vmlinuz-2.6.27-14-generic
   8.8GB: boot/vmlinuz-2.6.27-9-generic
  86.7GB: initrd.img
   8.8GB: initrd.img.old
  85.6GB: vmlinuz
   8.8GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by merlinus on 2009-08-02
Try adding this to the end of menu.lst

title Vista
rootnoverify (hd0,2)
makeactive
chainloader +1

and restart.

---

### Post by presence1960 on 2009-08-02
everything looks in order except maybe one thing. Did you format sda3? It says windows vista. I am wondering how it knows which windows is on your machine if you haven't got windows installed. I don't have any unallocated space or unused partition I can format as NTFS to see how it would look plus I have windows 7 which would show as vista.

I know this is probably obvious and I shouldn't even ask, but did you click apply (green check mark) in gparted after choosing to format the partition?

Is the windows install disk an original or a burned copy. Test it in another machine to see if it boots.

Did you try deleting sda3 and leaving it as unallocated space when installing windows?

I am at a loss here.

I just noticed something, which may mean nothing. I was comparing my boot info script output to yours. My data NTFS & my win 7 partition are unmounted in mine, but yours is mounted for some reason. Did you mount it prior to running the boot info script? Just a thought there.

---

### Post by merlinus on 2009-08-02
I also noticed that sda3 was listed as vista, which is why I suggested adding that stanza to menu.lst to see if it could be booted into.  It just may be that windows is indeed installed there.

Sorry if I interrupted the thread.

---

### Post by presence1960 on 2009-08-02
> **merlinus said:**
> I also noticed that sda3 was listed as vista, which is why I suggested adding that stanza to menu.lst to see if it could be booted into.  It just may be that windows is indeed installed there.

Sorry if I interrupted the thread.

I thought that also until I reread that he couldn't get the installer to do it's thing. Maybe if mounts that in ubuntu and looks to see if an OS structure is installed. He is missing boot files, but can restore them if the rest of the OS is installed.

What is weird is he is trying to install XP though. I just went back & reread the entire thread. Why the partition type says vista is really weird to me.

---

### Post by PooAvenger on 2009-08-02
Vista was installed on this laptop before I put Ubuntu on it but that was like 4 partitions of this hdd ago and like a year in actual time. The partition is mounted on my desktop but I didn't mount it, I didn't really do anything to it except format it. I did try just leaving it unformatted space and still no dice, the xp disk is a burn but it works on other computers as well as a virtual machine I have installed. How do I add the command to Menu.lst? I figure I'll try that and see what comes up.

Any other ideas? I need this computer for college so I don't want to have to wipe the hdd without being absolutely sure that it is unworkable that's why I'm trying to be thourough here.

Thanks again!

---

### Post by merlinus on 2009-08-02
```
gksudo gedit /boot/grub/menu.lst
```I don't expect adding this will actually boot vista, but perhaps will give some useful error messages.

Also, change this

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR=Red]hiddenmenu[/COLOR]

to this

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR=Red]# hiddenmenu

[COLOR=Black]so the grub menu will appear.[/COLOR]
[/COLOR]

---

### Post by PooAvenger on 2009-08-02
Ok no dice, the boot loader comes up but when I hit the Vista one it just says BOOTMGR is missing. So I'm guessing I formatted it correctly but XP still is being a skank and won't see it when I load everything for set up. Any guesses?

---

### Post by merlinus on 2009-08-02
Try to mount the partition.

```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/sda3 /media/windows
```

---

### Post by PooAvenger on 2009-08-02
I think it was mounted automatically but I typed in those commands anyway. So it's mounted, now I'll try windows again for ***** and giggles.

---

### Post by merlinus on 2009-08-02
Out of curiosity, navigate to that directory with nautilus -- /media/windows -- and see what is in there.

If you restarted, however, then mount it again using

```
sudo mount - t ntfs /dev/sda3 /media/windows
```before taking a look.

---

### Post by PooAvenger on 2009-08-02
Nothing's there, it's an empty directory. Also Windows still can't see nothing :*(

---

### Post by merlinus on 2009-08-02
Just to be sure -- you manually mounted sda3, and the directory was empty?

Even so, at least we know the partition is formatted correctly.  My best guess is that xp will not see it unless it is the first partition on the hdd.

---

### Post by PooAvenger on 2009-08-02
Yeah I manually mounted it and still nada.

I've never heard that about Windows but with M$ it doesn't surprise me considering everything that's been up until now. Well at least I have a couple days off to think about what to do now :/

What do you guys recommend? Wipe the disk, start with Windows and then try dual booting Ubuntu? Go back to Windows entirely? Consider it a lost cause lol? Anyway, thanks for your help so far.

---

### Post by merlinus on 2009-08-02
Not quite ready to give up, if you're not.  It may be because your partitions are not in correct numerical order.

So give this a go.

```
sudo fdisk /dev/sda
x
f
w
```and then post results of

```
sudo fdisk -l
```

---

### Post by PooAvenger on 2009-08-02
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb02f3de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12569   100960461   83  Linux
/dev/sda2   *       12570       18704    49279387+   7  HPFS/NTFS
/dev/sda3           18705       19457     6048472+   5  Extended
/dev/sda5           18705       19457     6048441   82  Linux swap / Solaris

---

### Post by robert shearer on 2009-08-02
You look to be in good hands with merlinus.

If all else fails here is a possible suggestion...

1) move all your personal data from your Ubuntu install to an external drive.
2) download and run Remastersys to make a live cd of your current Ubuntu install and its installed **configuration and apps.**
3) use the Official Ubuntu live cd to reformat your drive and create new partitions with the first being the ntfs target for your XP install.
4)install XP 
5) Use the **Remastersys cd** you made to install Ubuntu. This should give you your current system but on the new partition/s you have made.
6) Copy back your data from the external drive to your Ubuntu home folder.


You need to have the data moved to an external drive (and  the drive disconnected) so that Remastersys does not include it in the live cd- it will fail if it becomes too big.  So move all those audio/video/etc big files off first.
Also good to backup your apt-cache( can be a **big **file), try using 'aptoncd' (from the repos) to make a cd of your apps then do a ```
sudo apt-get clean
``` before making the remastersys cd 


[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

[http://en.wikipedia.org/wiki/Remastersys](http://en.wikipedia.org/wiki/Remastersys)

[http://www.geekconnection.org/remastersys/forums/index.php](http://www.geekconnection.org/remastersys/forums/index.php)

---

### Post by merlinus on 2009-08-02
Looks like fdisk fixed the partition order.  Now try to install xp into what is sda2.  Of course xp will not see it as such, but as an ntfs partition.  Give it a try anyway.  Nothing to lose...

Robert also seems to offer an alternative, should this not work.  I am not at all familiar with remastersys, so if you go that route, hopefully he can help.

---

### Post by PooAvenger on 2009-08-02
Ok I'm trying again with XP now. Lets hope this works.

---

### Post by PooAvenger on 2009-08-02
Ok still nothing coming up.

---

### Post by merlinus on 2009-08-02
Meaning the xp install disk is not seeing the ntfs partition?

Just to be sure, can you try the disk on a different computer to see if it works? I don't mean you should do the actual install!

---

### Post by PooAvenger on 2009-08-02
Yeah it can see other computers as well as my external hdd when I plug it into this laptop.

---

### Post by merlinus on 2009-08-02
At this point, I am fresh out of ideas.  If you can backup data, it might be best to format the first primary as ntfs and see if that makes any difference.

If you need xp, that is!

---

### Post by PooAvenger on 2009-08-02
Yeah I need to get it on here for school stuff (since some of the programs/sites I'm gonna need only work on Windows) so I guess we gotta format now.

I'll post results here, here's hoping!

---

### Post by merlinus on 2009-08-02
You might wind up having to format the entire hdd as one ntfs partition, if doing only the first one will still not work.

Good luck!

---

### Post by ronparent on 2009-08-02
melinus may be right, however, once the win XP install issue is settled you will probably be able to use gpatted to repartition the drive how you please.

---

### Post by PooAvenger on 2009-08-03
FUUUUUUUUU-


I formatted the entire disk (without making a backup remastersys disk since for some reason no matter what I did it just kept telling me the iso was too large, but I backed up all my files so thats all good at least and I know what programs were installed so that's all good) and windows still refuses to see it. I really hate Microsoft right now. I have no idea why this is still happening but I'm starting to think it was engineered this way to prevent users from downgrading to XP from Vista (maybe thats the paranoia from being up at 6AM screwing around all night with computers but hey, you never know).I'm gonna download the Windows 7 iso and burn it to a dvd and see if I get the same crap.

I swear to god I'm gonna end up destroying something one of these days...I gotta find another line of work lol.

---

### Post by merlinus on 2009-08-03
Are you installing xp from a downloaded .iso or legitimate installation cds?  If the latter, then at this point I would use dban to completely wipe everything from your hdd.

If the former, then it is almost certainly illegal, and could well be corrupted and contain all sorts of vermin, thereby creating the problems you have been experiencing.

[http://www.dban.org/](http://www.dban.org/)

---

### Post by Syron4 on 2009-08-03
You forgot the cardinal rule. XP doesn't have native SATA-HD support. It had nothing to do with your partitioning whatsoever. It just had to do with the fact that XP install couldn't support the HD. In the bios you can set the AHCI for IDE mode. That should allow XP to see the hard drive. Otherwise you will need to go to to the manufacturer of the laptop's website and check their drivers. There will be a hard drive driver that you can put on a floppy disk and use during the XP install. Otherwise you can create an XP install disc that will have the drivers preloaded in it. The software you will need for that is called NLite.
 
Here is a link that will walk you through using Nlite to create a XP install disc that will work for you: [http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml](http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml)

---

### Post by ronparent on 2009-08-03
The problem with xp recognizing a gparted formatted disk probably has little to do with Microsoft. Partition magic, now a Nortton owned partitioning program has the same problem. It may not recognize any disk partitioned by gparted or Vista as having any valid partitions, ntfs, fat32 or outherwise! We know that Vista introduces some quirks in its partitioning process that may make the partition invalid with either xp based partitioners or gparted. Likewise, I have myself experienced loss of drives to both XP and Vista after partitioning with gparted. I had hoped that by following this thread I would gain some insight on the problems. It looks like we will all be left thrashing around and left to our own meager resources to work around the problem.

In regards to XP installarion, it appears that MS is currently not rigorusly enforcing it activation requiredments. I have recently reinstalled two XPs to complete rebuilds without any on-line activation complaint (where formally it would have required activation by phone with satisfactory explanation). I did use the my original XP install cd's (which I know are free of 'vermin'. In one case I also had to slipstream XP's SP 1 and SP 3 (MS distributions). In both instances the installation were activated as soon as I went online. Do use the original MS distributed software and key though, even if you aren't too fussy whare they came from.

---

### Post by PooAvenger on 2009-08-03
Yeah my disk is totally legit student copy of Windows XP sp2.

> 
You forgot the cardinal rule. XP doesn't have native SATA-HD support. It had nothing to do with your partitioning whatsoever. It just had to do with the fact that XP install couldn't support the HD. In the bios you can set the AHCI for IDE mode. That should allow XP to see the hard drive. Otherwise you will need to go to to the manufacturer of the laptop's website and check their drivers. There will be a hard drive driver that you can put on a floppy disk and use during the XP install. Otherwise you can create an XP install disc that will have the drivers preloaded in it. The software you will need for that is called NLite.


After I get done dl'ing the Windows 7 ISO and burning that to a disk I'll try this. Also, explain how to do this (I'm pretty good at monkeying around in the bios just not actually good at making changes that help...lol) pretty please :).

If it is that, I swear to god...

I'll be a happy man. Again, here's hoping.

EDIT: Also, when I try to boot up GRUB still comes up just gives me an error 22 message. Should it still come up after wiping everything?

---

### Post by merlinus on 2009-08-03
grub is installed in the mbr of the hdd, so until you install the new os (xp or 7, which will overwrite it), you will continue to see it.

The only way to get rid of it otherwise is to use dban to completely wipe your hdd.

BTW, I mentioned pirated .isos of windows because that issue crops up here now and again, and almost always causes problems for the user.

---

### Post by ronparent on 2009-08-03
Grub is coming up because that is what is still on the MBR. That will get wiped out by installing windows - windows, any flavor, will rewrite the MBR. I installed win XP before win 7, only because win 7 creates its own small boot partition if installed first. That gets incorporated in the win XP partition when installed following and requires one less primary partition. Remember, your primary partition count (including the extended partition) can't exceed four. Ubuntu requires a minimum of two partitions which can both be within the extended partition. This bring your primary partition count up to three - leaving you room for one more primary partition if the need arises.

My Win XP's occupy less than 10 Gb of a 30 Gb partition at this point. The Win 7 has however already occupied 25 Gb of a 30 Gb partition and I am now wishing I had made that partition at least 10 Gb larger. All my data is on ntfs partitions within the extended area and is accessible by all the OS's. Everything should go smoothly at this point. Good luck.

---

### Post by PooAvenger on 2009-08-03
> **Syron4 said:**
> You forgot the cardinal rule. XP doesn't have native SATA-HD support. It had nothing to do with your partitioning whatsoever. It just had to do with the fact that XP install couldn't support the HD. In the bios you can set the AHCI for IDE mode. That should allow XP to see the hard drive. Otherwise you will need to go to to the manufacturer of the laptop's website and check their drivers. There will be a hard drive driver that you can put on a floppy disk and use during the XP install. Otherwise you can create an XP install disc that will have the drivers preloaded in it. The software you will need for that is called NLite.
 
Here is a link that will walk you through using Nlite to create a XP install disc that will work for you: [http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml](http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml)

I love you man :D

Setting the hdd from AHCI to Compatability mode in the bios let the xp disk recognize the hdd. It still says there is an unknown disk though but idk what to do about that. Formatting the space it did see (which is about all the hard drive) and then I'll try and get Ubuntu back up again and dual boot the usual way.

After all that it was just one ****ing setting. I swear on my deathbed the one thing I will spout to my progeny will be "Now remember kids, XP doesn't natively support SATA hard drives!" Because of this.

Lolzor.

---

### Post by Syron4 on 2009-08-03
My only regret is that I wish I had joined the forum and posted my two cents before you had wiped your drive! In any case, it looked like you had backed up your stuff, so it shouldn't be the end of the world.
 
I own a computer repair company, so I come across this issue lots. The only thing that made me think about it though was that your computer originally had vista on it. Thats when I realized it was a SATA hd and XP no likey.
 
Enjoy reinstalling Ubuntu/XP!

---

