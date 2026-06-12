---
title: "[SOLVED] Help! crypted sda5 will not boot"
date: 2008-10-28
forum: General Help
---

### Post by Valir on 2008-10-28
Hi, 

Urgent help needed! Please help

my hardy studio rt kernel will not boot. Can anyone help me fix the specific problem, or alternatively tell me how I can salvage my data from my home folder before doing a clean install?

I have a hardy installation with a crypted hard drive. Been working fine (with some hickups on shutdown, a problem related to networkmanager, but it was solved, and I am not sure if has anything to do with this)

Now, my computer stalled and after a forced restart the system will not boot. 

It might have happened after an upgrade, but I have restarted a few times since last.

_____This is what happens if I boot in recovery mode_____

Enter LUKS passphrase: (I enter password)

then later: [15.874579] padlock: VIA PadLock Hash Engine not detected.
modprobe: WARNING: Error inserting padlock_sha (/lib/modules/2.6.24-21-rt/kernel/drivers/crypto/padlock-sha.ko): No such device

key slot 0 unlocked
command successful.
cryptsetup: failed to setup lvm device.
Done.
Begin: waiting for root file system .... ...
Done.
                Check root= bootarg cat /proc/cmdline
                or missing modules, devices: cat /proc/modules ls /dev
Reading all physical volumes. This may take a while...
Found volume group "ubuntu" using metadata type lvm2
ALERT! /dev/mapper/ubuntu-root does not exist. Dropping to a shell!


..................................

Ok, here comes BusyBox
(initramfs)

But if I can´t cd to anything, and dir gives me /bin/sh and dir: not found.

.................

What is happening?


Help would be greatly appreciated.

p.s. My battery is not working, so the computer has sometimes been abruptly turned off, maybe this has done some damage to the filesystem?

---

### Post by Valir on 2008-10-28
No takers?

I tried to access the hard disk by booting ubuntu from a cd, but on the computer it only finds a 256 mb grub partition. My other 30 gb nowhere to be found?

---

### Post by jerome1232 on 2008-10-28
Can you boot into a live cd and post the output of this command?
```
sudo fdisk -l
```


Since we will be dealing with encrypted LVM you are going to need a few tools, this will install them and make them active. I'm assuming you are using luks for encryption, correct me if that assumption is wrong.

```
sudo apt-get install lvm2 cryptsetup
sudo modprobe dm-crypt
sudo modprobe dm-mod
```

---

### Post by Valir on 2008-10-28
Hi Jerome, 

thank you for your reply.

I am booting into a live cd (A Gutsy cd, I hope thats alright, the version on the hard drive is hardy studio rt, but I cant find the dvd)

I think it is LUKS to, at least when I tried to access in recovery mode. 

I installed the tools.

And this is what shows on sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00078552

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32        7296    58356112+   5  Extended
/dev/sda5              32        7296    58356081   83  Linux
ubuntu@ubuntu:~$

---

### Post by jerome1232 on 2008-10-28
Okay I'm assuming sda5 is the crypto partition, with those tools isntalled and modprobe'd. Try this and see what happens post relevant outputs if you run into problems.

You can change the name 'work' just keep it consistant

and be sure to NOT run fsck on a mounted file system. This is bad to do.

```
sudo crytpsetup luksOpen /dev/sda5 work
sudo vgscan
# in the next step if you omit the name it will try and make all volume groups active
sudo vgchange -a y *nameofvolumegrouphere*
sudo lvscan
# should list out your logical volumes
# try and mount them one at a time like so
sudo mount /dev/mapper/*VGNAME*-*LVNAME* /mnt
# to unmount
sudo umount /dev/mapper/*VGNAME-[I]LVNAME*[/I]
# if any fail to mount try and run fsck on them
sudo fsck -p /dev/*VGNAME-[I]LVNAME*[/I]
```

---

### Post by Valir on 2008-10-28
I get this:

ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda5 work
Enter LUKS passphrase: 
Failed to setup dm-crypt key mapping.
Check kernel for support for the aes-cbc-essiv:sha256 cipher spec and verify that /dev/sda5 contains at least 258 sectors.
Failed to read from key storage
Command failed: No key available with this passphrase.

---

### Post by jerome1232 on 2008-10-28
Just making sure you did do this before you tried to open it correct?

```
sudo apt-get install cryptsetup lvm2
sudo modprobe dm-crypt
sudo modprobe dm-mod
```

If so I don't know how to procede from here, if you can't unlock the encryption there is no way to get the data off of it.

---

### Post by Valir on 2008-10-28
Yes!!! command succesful

keyslot 0 unlocked

I will proceed with next steps

---

### Post by Valir on 2008-10-28
Sorry, maybe I am not getting how to fill this out correctly?

ubuntu@ubuntu:~$ sudo vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "ubuntu" using metadata type lvm2
ubuntu@ubuntu:~$ sudo vgchange -a y ubuntu
  2 logical volume(s) in volume group "ubuntu" now active
ubuntu@ubuntu:~$ sudo lvscan
  ACTIVE            '/dev/ubuntu/root' [53.46 GB] inherit
  ACTIVE            '/dev/ubuntu/swap_1' [2.19 GB] inherit
ubuntu@ubuntu:~$ sudo mount /dev/mapper/ubuntu-ubuntu /mnt
mount: special device /dev/mapper/ubuntu-ubuntu does not exist
ubuntu@ubuntu:~$ sudo mount /dev/mapper/ubuntu-root /mnt
mount: you must specify the filesystem type

And further

ubuntu@ubuntu:~$ sudo mount /dev/mapper/ubuntu-root /mnt -t ext3
mount: wrong fs type, bad option, bad superblock on /dev/mapper/ubuntu-root,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo mount /dev/mapper/ubuntu-root /dev/ubuntu/root -t ext3
mount: wrong fs type, bad option, bad superblock on /dev/mapper/ubuntu-root,
       ...

ubuntu@ubuntu:~$ dmesg | tail 
[ 2905.708000] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
[ 4089.440000] VFS: Can't find ext3 filesystem on dev dm-1.
[ 4111.252000] VFS: Can't find ext3 filesystem on dev dm-1.

---

### Post by jerome1232 on 2008-10-28
Okay awesome the encryption unlocks :)

Try doing this to see what filesystem and such it is
```
sudo lvdisplay
```

---

### Post by Valir on 2008-10-28
:) I am glad the encryption is gone, but I don't seem to get this righ, i would think this should be ext3

ubuntu@ubuntu:~$ sudo lvdisplay
  --- Logical volume ---
  LV Name                /dev/ubuntu/root
  VG Name                ubuntu
  LV UUID                pavkkp-EOsz-fP73-Ajpb-e8hv-Dc0t-vLnKCt
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                53.46 GB
  Current LE             13686
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:1
   
  --- Logical volume ---
  LV Name                /dev/ubuntu/swap_1
  VG Name                ubuntu
  LV UUID                hTLx3j-isAz-Ers0-iXWS-F3rN-SGl4-PZP4yr
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                2.19 GB
  Current LE             560
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:2

---

### Post by jerome1232 on 2008-10-28
Yeah I thought it would say the file system in there well try mounting as  ext3 then:

btw it makes your output more readable if you wrap it in [noparse]```
code tags
```[/noparse]
I think the file system is corrupt really we shouldn't have to specify the file system.
```
sudo mount -t ext3 /dev/mapper/ubuntu-root /mnt
```

---

### Post by Valir on 2008-10-28
```
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/mapper/ubuntu-root /mnt
mount: wrong fs type, bad option, bad superblock on /dev/mapper/ubuntu-root,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Would this mean the filesystem is corrupt? Or could this be some error after upgrade? I alse searched the error message and got this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206129](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206129)

but couldn't get my head around it, there people at least seemed to be able to boot up.

---

### Post by jerome1232 on 2008-10-28
Yes I think either a) the filesystem isn't ext3, or b) there is file system corruption

> **Valir said:**
> I alse searched the error message and got this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206129](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206129)

but couldn't get my head around it, there people at least seemed to be able to boot up.

I believe that bug is why your getting errors during boot about the encryption, but it get's unlocked so that's not what is causing you to fail to boot. The problem  we are having is it can't get mounted, possibly due to some filesystem coruption. 

I think someone more experienced with e2fsck needs to help you from here. 

From that error message I think you need this from e2fsck. 
```
       -b superblock
              Instead of using  the  normal  superblock,  use  an  alternative
              superblock  specified  by  superblock.   This option is normally
              used when the primary superblock has been corrupted.  The  loca&#8208;
              tion  of  the backup superblock is dependent on the filesystem’s
              blocksize.   For  filesystems  with  1k  blocksizes,  a   backup
              superblock  can  be found at block 8193; for filesystems with 2k
              blocksizes, at block 16384; and  for  4k  blocksizes,  at  block
              32768.

              Additional  backup  superblocks  can  be determined by using the
              mke2fs program using the  -n  option  to  print  out  where  the
              superblocks were created.   The -b option to mke2fs, which spec&#8208;
              ifies blocksize of the filesystem must be specified in order for
              the superblock locations that are printed out to be accurate.

              If  an alternative superblock is specified and the filesystem is
              not opened read-only, e2fsck will make  sure  that  the  primary
              superblock  is  updated  appropriately  upon  completion  of the
              filesystem check.
```

edit: From testing on my own little drive I think you need to do this

But please wait on confirmation that this is all correct I don't want to do more damage or something here.

```
:~$ sudo mke2fs -n /dev/sdb1  # change that to /dev/mapper/ubuntu-root for you
mke2fs 1.41.3 (12-Oct-2008)
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
122880 inodes, 489948 blocks
24497 blocks (5.00%) reserved for the super user
First data block=1
Maximum filesystem blocks=67633152
60 block groups
8192 blocks per group, 8192 fragments per group
2048 inodes per group
Superblock backups stored on blocks: 
	8193, 24577, 40961, 57345, 73729, 204801, 221185, 401409
# see how it shows spots where there are alternate super blocks try running fsck specifying one of them, yours will probably differ
:~$ sudo e2fsck -b 8193 /dev/sb1   # once again change it to /dev/mapper/ubuntu-root
e2fsck 1.41.3 (12-Oct-2008)
/dev/sdb1 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sdb1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sdb1: 11/122880 files (0.0% non-contiguous), 26051/489948 blocks
```

---

### Post by Valir on 2008-10-28
Ok, so you mean I should wait for confirmation from someone else that uses e2fsch a lot? Do I do that in this thread or signal that help is needed for e2fsch somewhere else? Would I run the risk of destroying data if I would just go ahead as you just did?

I hope I can fix this, I have a lot of work that I didn't backup. But you have been a tremendous help and I've learned a lot in the process :)

---

### Post by jerome1232 on 2008-10-28
Yes I think you *might* run the risk of losing data using the method up above.

Though this one would be safe to run maybe it'll get the job done, it does safe repairs only and it's supposed to report if anything wasn't fixable using just that option.

```
sudo e2fsck -p /dev/mapper/ubuntu-root
```

---

### Post by Valir on 2008-10-28
```
ubuntu@ubuntu:~$ sudo e2fsck -p /dev/mapper/ubuntu-root
e2fsck: Bad magic number in super-block while trying to open /dev/mapper/ubuntu-root
/dev/mapper/ubuntu-root: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device> 
```

ALAS! I get this. So maybe the only options is chaning these superblocks? However, it said ext2, while my might be ext3

---

### Post by jerome1232 on 2008-10-28
Well ext3 is ext2 with a journal added on so don't worry about that, but since that seems to suggest exactly what I was thinking I feel better about trying. It didn't damage anything when I ran it on my test disk.

Do you happen to have an external drive that's large enough to hold an image of this drive? That way you can run filesystem checks and such on the image without worrying about damaging any data.

---

### Post by Valir on 2008-10-28
Bingo! As you described

```
 sudo mke2fs -n /dev/mapper/ubuntu-root 
```

There I picked the first superblock.

```
 sudo e2fsck -b [#superblocknumber] /dev/mapper/ubuntu-root 
```

A lot of fixes and then I rebooted without a problem, the system works as normal. 

Thank you very much for your help, Jerome :)

best of luck!

 

And now, I just have to figure out why my filesystem got so corrupted. I have to see what kind of maintenance work I should have been doing in order to avoid this, or if it was that bug.

---

