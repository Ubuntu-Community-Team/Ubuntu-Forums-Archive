---
title: "Borked grub. Error on boot."
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by dougleduck on 2009-03-10
I have several partitions, including windows partition, partition for media files...

Tried to re-install ubuntu including seperate /, /home and /boot/grub partition. However on boot I get this error 15 File Not Found.

Using the ubuntu live CD  using grub to find /boot/grub/stage1 or /grub/stage1 I found the /boot/grub partition was empty. I copied over the files from /usr/lib/grub but to no avail.

Think I need to install grub to this partition still but the grub installer seems to be complaining about the boot partition not being on same device as grub partition.

How do I get grub fixed? :S

---

### Post by dougleduck on 2009-03-11
*bump*

If someone can walk me through installing grub thatd be great. I've tried reading around but there's often not a lot of explanation of what's being done so can't work out what to do. :S

---

### Post by mhgsys on 2009-03-11
ok, 
Bootup a live cd, open a terminal and do the following.

sudo grub
This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:
find /boot/grub/stage1
This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:
root (hd?,?)
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:
setup (hd0)
Finally exit the grub shell
Code:
quit

Hope this helps for you
mhgsys

---

### Post by dougleduck on 2009-03-11
So this doesn't work. This is without mounting any partitions. As entered into bash shell and error messages.

```
grub

grub> find /boot/grub/stage1

Error 15: File not found
grub> find /grub/stage1

Error 15: File not found
```

I would like to install grub onto a seperate /boot/grub partition really btw, but without live CD I have a bricked laptop any setup would be good.

For extra info heres details of my current partitions with what they are intended for, or already are, just to clarify.

/dev/sda1    125MB    fat16    //MBR i believe???:S
/dev/sda2    10GB     ntfs      //vista recovery
/dev/sda3    35GB     ntfs     //vista
/dev/sda4    -        extended //logical partition?
/dev/sda8    290MB    ext3     //where I want "/boot/grub"
/dev/sda9    14BG     ext3     "/home"
/dev/sda10   21GB     ext3     "/" for ubuntu 8.10 (main distro)
/dev/sda5    5GB      ext3     ubuntu 64 "/"
/dev/sda7    200GB    ext3     "/media/storage" large file storage
/dev/sda6    2GB      ext3      swap

---

### Post by meierfra. on 2009-03-11
In order to get a clearer picture of your setup, I suggest to boot from your Ubuntu Live CD (the Ubuntu install CD), download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Neo_The_User on 2009-03-11
I thought GRUB error 21 meant file not found. ...hmm

---

### Post by mhgsys on 2009-03-11
@dougleduck.

Try mounting /dev/sda1 
and try

find /boot/grub/stage1

again.

---

### Post by dougleduck on 2009-03-11
Ok so results of the script first. I hadn't mounted any partitions at this point.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     Grub0.97 in the file /stage1 looks at sector 1 of the 
                       same hard drive for the stage2 file. A stage2 file is 
                       at this location on /dev/sda. Stage2 looks on the same 
                       partition for /boot/grub/stage2.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x98000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       257,039       256,977  de Dell Utility
/dev/sda2             258,048    21,229,567    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,237,930    93,691,079    72,453,150   7 HPFS/NTFS
/dev/sda4          93,691,080   625,137,344   531,446,265   5 Extended
/dev/sda5         167,702,598   178,192,979    10,490,382  83 Linux
/dev/sda6         620,944,443   625,137,344     4,192,902  82 Linux swap / Solaris
/dev/sda7         178,193,043   620,944,379   442,751,337  83 Linux
/dev/sda8          93,691,206    94,285,484       594,279  83 Linux
/dev/sda9          94,285,548   123,588,044    29,302,497  83 Linux
/dev/sda10        123,588,108   167,702,534    44,114,427  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D9-0204" TYPE="vfat" 
/dev/sda2: UUID="BAEC98ADEC986603" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="E0D69B96D69B6B92" LABEL="OS" TYPE="ntfs" 
/dev/sda5: UUID="6f9e07ec-252b-412d-ae09-725aac8f227e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="aadda235-9cc5-461c-a33d-9ae821176a21" TYPE="swap" 
/dev/sda7: UUID="362faf1d-9237-4ae5-b3b2-21a83e12a4fc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="05c5c03a-18b1-40e2-9b57-602f0fa238d7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="e4572268-9dbc-476f-afdc-2ff1c53cdbb2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda10: UUID="775ab177-c728-4a26-8de9-46d4e2285e91" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=6f9e07ec-252b-412d-ae09-725aac8f227e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=45ad75ab-c298-4017-8d75-850e50403f00 /boot/grub      ext3    relatime        0       2
# /dev/sda6
UUID=7e9ffe2a-4866-4405-975f-ea63ecadec09 /home           ext3    relatime        0       2
# /dev/sda12
UUID=aadda235-9cc5-461c-a33d-9ae821176a21 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  90.8GB: boot/initrd.img-2.6.27-11-generic
  90.8GB: boot/initrd.img-2.6.27-7-generic
  90.7GB: boot/vmlinuz-2.6.27-11-generic
  90.7GB: boot/vmlinuz-2.6.27-7-generic
  90.8GB: initrd.img
  90.8GB: initrd.img.old
  90.7GB: vmlinuz
  90.7GB: vmlinuz.old

=================== sda8: Location of files loaded by Grub: ===================


  47.9GB: stage2

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=e4572268-9dbc-476f-afdc-2ff1c53cdbb2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=05c5c03a-18b1-40e2-9b57-602f0fa238d7 /boot/grub      ext3    relatime        0       2
# /dev/sda10
UUID=775ab177-c728-4a26-8de9-46d4e2285e91 /home           ext3    relatime        0       2
# /dev/sda6
UUID=aadda235-9cc5-461c-a33d-9ae821176a21 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda9: Location of files loaded by Grub: ===================


  56.6GB: boot/vmlinuz-2.6.27-7-generic
  56.6GB: vmlinuz
```

And result after mounting sda1. Wasn't sure where to mount this, so made directory to mount to /mnt/danger.

```
mount /dev/sda1 /mnt/danger
 sudo grub

grub> find /boot/grub/stage1

Error 15: File not found

grub> find /grub/stage1

Error 15: File not found
```

---

### Post by mhgsys on 2009-03-11
try making /media/disk

---

### Post by dougleduck on 2009-03-11
Think this is what you meant. Again no luck

```
sudo mkdir /media/disk
sudo mount /dev/sda1 /media/disk/
sudo grub
grub> find /boot/grub/stage1 

Error 15: File not found

grub> find /grub/stage1

Error 15: File not found

```

---

### Post by mhgsys on 2009-03-11
try the same thing  on sda8


sda8: according to your post _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     Grub0.97 in the file /stage1 looks at sector 1 of the 
                       same hard drive for the stage2 file. A stage2 file is 
                       at this location on /dev/sda. Stage2 looks on the same 
                       partition for /boot/grub/stage2.
    Operating System:  
    Boot files/dirs:

---

### Post by meierfra. on 2009-03-11
To locate  the stage1 file try:

```
sudo grub
find /stage1
```

But the file "menu.lst" is  be missing. Also your Ubuntu / partition seems to be /dev/sda9 ( and not /dev/sda10).  And your Ubuntu / partition is missing the "initrd.img" file. 

So I suggested to reinstall Ubuntu  one more time. 
But do not try to make a separate grub partition.  Just use a "/" and "/home" partition. After you successfully installed Ubuntu, follow this tutorial to create a dedicated grub partition:

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_")

---

### Post by dougleduck on 2009-03-11
I'll have a go at re-installing without seperate grub partition though. 

```
sudo mkdir /media/disk 
sudo mount /dev/sda8 /media/disk/
sudo grub
grub> find /boot/grub/stage1

Error 15: File not found
find /grub/stage1

Error 15: File not found

grub> find /stage1
 (hd0,7)

```

---

### Post by mhgsys on 2009-03-11
eeeehmz, 

reading your post.

grub> find /stage1
 (hd0,7)


Seems you've found it.

---

### Post by dougleduck on 2009-03-11
I assumed meierfra was suggesting that even if I'd found it would need to re-install.

Still get Error 15 on boot. Mounting sda10 where my / partition is there is no grub folder in /

Still getting the Error 15 using grub from bash after mounting sda10 with

find /boot/grub/stage1, /grub/stage1 and /stage1.

I made a grub folder and moved files from /usr/lib/grub. 

@find /stage1@ returns

(hd0,9)
Will I then be able to install grub?

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     Grub0.97 in the file /stage1 looks at sector 1 of the 
                       same hard drive for the stage2 file. A stage2 file is 
                       at this location on /dev/sda. Stage2 looks on the same 
                       partition for /boot/grub/stage2.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x98000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       257,039       256,977  de Dell Utility
/dev/sda2             258,048    21,229,567    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,237,930    93,691,079    72,453,150   7 HPFS/NTFS
/dev/sda4          93,691,080   625,137,344   531,446,265   5 Extended
/dev/sda5         167,702,598   178,192,979    10,490,382  83 Linux
/dev/sda6         620,944,443   625,137,344     4,192,902  82 Linux swap / Solaris
/dev/sda7         178,193,043   620,944,379   442,751,337  83 Linux
/dev/sda8          93,691,206    94,285,484       594,279  83 Linux
/dev/sda9          94,285,548   123,588,044    29,302,497  83 Linux
/dev/sda10        123,588,108   167,702,534    44,114,427  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D9-0204" TYPE="vfat" 
/dev/sda2: UUID="BAEC98ADEC986603" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="E0D69B96D69B6B92" LABEL="OS" TYPE="ntfs" 
/dev/sda5: UUID="6f9e07ec-252b-412d-ae09-725aac8f227e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="aadda235-9cc5-461c-a33d-9ae821176a21" TYPE="swap" 
/dev/sda7: UUID="362faf1d-9237-4ae5-b3b2-21a83e12a4fc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="05c5c03a-18b1-40e2-9b57-602f0fa238d7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="e4572268-9dbc-476f-afdc-2ff1c53cdbb2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda10: UUID="775ab177-c728-4a26-8de9-46d4e2285e91" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=6f9e07ec-252b-412d-ae09-725aac8f227e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=45ad75ab-c298-4017-8d75-850e50403f00 /boot/grub      ext3    relatime        0       2
# /dev/sda6
UUID=7e9ffe2a-4866-4405-975f-ea63ecadec09 /home           ext3    relatime        0       2
# /dev/sda12
UUID=aadda235-9cc5-461c-a33d-9ae821176a21 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  90.8GB: boot/initrd.img-2.6.27-11-generic
  90.8GB: boot/initrd.img-2.6.27-7-generic
  90.7GB: boot/vmlinuz-2.6.27-11-generic
  90.7GB: boot/vmlinuz-2.6.27-7-generic
  90.8GB: initrd.img
  90.8GB: initrd.img.old
  90.7GB: vmlinuz
  90.7GB: vmlinuz.old

=================== sda8: Location of files loaded by Grub: ===================


  47.9GB: stage2

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=e4572268-9dbc-476f-afdc-2ff1c53cdbb2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=05c5c03a-18b1-40e2-9b57-602f0fa238d7 /boot/grub      ext3    relatime        0       2
# /dev/sda10
UUID=775ab177-c728-4a26-8de9-46d4e2285e91 /home           ext3    relatime        0       2
# /dev/sda6
UUID=aadda235-9cc5-461c-a33d-9ae821176a21 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda9: Location of files loaded by Grub: ===================


  56.6GB: boot/vmlinuz-2.6.27-7-generic
  56.6GB: vmlinuz
```

---

### Post by meierfra. on 2009-03-11
> I assumed meierfra was suggesting that even if I'd found it would need to re-install.

Yes I was. Your are missing two essential files (menu.lst and initrd.img).  If you want, I can  tell you how to generate those  files manually.  But I'm not sure that those are the only files missing.  So  reinstalling  seems to be easiest solution.

---

### Post by dougleduck on 2009-03-11
I have re-installed, above comments apply after re-installation. Sorry, should have made that clearer/.

---

### Post by mhgsys on 2009-03-11
Maybe meierfra is right, 
I'm not sure though, but thats only because this has always worked for me

Anyway, 
If you want to give it a last try before installing another ubuntu you can proceed with the info grub gave you

in a terminal: 
grub

root > (hd0,9)


Next enter the command to install grub to the mbr

Code:
setup (hd0)
Finally exit the grub shell
Code:
quit

---

### Post by mhgsys on 2009-03-11
EDIT: You allready re-Installed. 
I was typing this before I red your update

---

### Post by meierfra. on 2009-03-11
> I have re-installed, above comments apply after re-installation.

Are you able to boot into  the new Ubuntu? 

 The "RESULTS.txt" seems to be the same as the previous one (that's why I thought you hadn't reinstalled)
If you still had  the old "RESULT.txt" on the Desktop when you run the boot info script, the new file will be called "RESULTS1.txt.

---

### Post by dougleduck on 2009-03-11
The new install doesn't work. Get Error 15 on boot.

I think I posted the wrong tab, so here it is. Subtlely different. Should be able make menu.lst, have a backup from before things got messed up I know how to edit. But the initrd.img,  no idea how to do this.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

sda11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x98000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       257,039       256,977  de Dell Utility
/dev/sda2             258,048    21,229,567    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,237,930    93,691,079    72,453,150   7 HPFS/NTFS
/dev/sda4          93,691,080   625,137,344   531,446,265   5 Extended
/dev/sda5         167,702,598   178,192,979    10,490,382  83 Linux
/dev/sda6         620,944,443   625,137,344     4,192,902  82 Linux swap / Solaris
/dev/sda7         178,193,043   620,944,379   442,751,337  83 Linux
/dev/sda8          93,691,206    94,076,639       385,434  83 Linux
/dev/sda9          94,076,703   124,069,994    29,993,292  83 Linux
/dev/sda10        124,070,058   160,071,659    36,001,602  83 Linux
/dev/sda11        160,071,723   167,702,534     7,630,812  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D9-0204" TYPE="vfat" 
/dev/sda2: UUID="BAEC98ADEC986603" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="E0D69B96D69B6B92" LABEL="OS" TYPE="ntfs" 
/dev/sda5: UUID="6f9e07ec-252b-412d-ae09-725aac8f227e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="aadda235-9cc5-461c-a33d-9ae821176a21" TYPE="swap" 
/dev/sda7: UUID="362faf1d-9237-4ae5-b3b2-21a83e12a4fc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="1a4f30a8-cad3-437b-8796-568941f13354" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="2180d717-fe3b-424f-ad38-a0b71672c471" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda10: UUID="8f915c09-d440-41ef-807f-029d8f62e861" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: UUID="bb7dff9e-23bb-40b9-9360-4e314fa9d235" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=6f9e07ec-252b-412d-ae09-725aac8f227e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=45ad75ab-c298-4017-8d75-850e50403f00 /boot/grub      ext3    relatime        0       2
# /dev/sda6
UUID=7e9ffe2a-4866-4405-975f-ea63ecadec09 /home           ext3    relatime        0       2
# /dev/sda12
UUID=aadda235-9cc5-461c-a33d-9ae821176a21 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  90.8GB: boot/initrd.img-2.6.27-11-generic
  90.8GB: boot/initrd.img-2.6.27-7-generic
  90.7GB: boot/vmlinuz-2.6.27-11-generic
  90.7GB: boot/vmlinuz-2.6.27-7-generic
  90.8GB: initrd.img
  90.8GB: initrd.img.old
  90.7GB: vmlinuz
  90.7GB: vmlinuz.old

=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda10
UUID=8f915c09-d440-41ef-807f-029d8f62e861 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=2180d717-fe3b-424f-ad38-a0b71672c471 /home           ext3    relatime        0       2
# /dev/sda6
UUID=aadda235-9cc5-461c-a33d-9ae821176a21 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda10: Location of files loaded by Grub: ===================


  66.7GB: boot/vmlinuz-2.6.27-7-generic
  66.7GB: vmlinuz
```

---

### Post by mhgsys on 2009-03-11
Seems to me that most of grub is located on sda5
and that you got another one messed up at sda10.

Seems to me that if you put in the sda10 grub info into the menu.1st located in sda5, and then reinstall grub with the menu.1st from sda5 onto sda0 your done.

what a dizzy setup.






=================== sda5: Location of files loaded by Grub: ===================


  90.8GB: boot/initrd.img-2.6.27-11-generic
  90.8GB: boot/initrd.img-2.6.27-7-generic
  90.7GB: boot/vmlinuz-2.6.27-11-generic
  90.7GB: boot/vmlinuz-2.6.27-7-generic
  90.8GB: initrd.img
  90.8GB: initrd.img.old
  90.7GB: vmlinuz
  90.7GB: vmlinuz.old



=================== sda10: Location of files loaded by Grub: ===================


  66.7GB: boot/vmlinuz-2.6.27-7-generic
  66.7GB: vmlinuz

---

### Post by dougleduck on 2009-03-11
sda5 doesn't have grub installed as I had grub installed onto seperate partition. Also that install, which hasn't been touched since things broke, is 64 bit distro, don't know if that would affect things or not.

---

### Post by meierfra. on 2009-03-11
You still don't have a menu.lst and initrd.img. Also grub did not get install in the MBR (you still have the old grub in the MBR pointing to /dev/sda5) 

Did you get any error messages during the installation? Maybe there is something wrong with the Live CD?  Did you check the  CD for errors? At what speed did you burn the CD?

---

### Post by dougleduck on 2009-03-11
Got an error about ubiquity at the end of the install, think I misread that it was just graphical front end to the installer, but re-reading seems this was the installer. :S Don't know what speed was  burned at but I did check the CD after I'd burned it. But that was a few weeks ago so I'll check it again.

---

### Post by meierfra. on 2009-03-11
Yes, ubiquity  is the installer.

But lets  try to fix your problems  manually. Boot from the LiveCD, open a terminal and chroot into /dev/sda10:

```
sudo mount /dev/sda10 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt /bin/bash

```

and then generate "initrd.img",  install grub and generate menu.lst:
```

update-initramfs -k all         (edit: this needs to be update-initramfs -c -k all)  
grub-install --recheck /dev/sda
update-grub
exit

```

Reboot and hope for the best.

---

### Post by dougleduck on 2009-03-11
```
update-initramfs -k all
You must specify at least one of -c, -u, or -d.

Usage: /usr/sbin/update-initramfs [OPTION]...

```
So I did the following as didn't seem to have this file
```
update-initramfs -c -k all
```
Which seemed to work.

```
grub-install --recheck /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
```

Will this work without first mounting sda? Or was that meant to be sda10?

---

### Post by meierfra. on 2009-03-11
> update-initramfs -c -k all

Yup, that's the correct command. My bad.


> grub-install --recheck /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device

Let's try this outside the chroot.

Open a new terminal:

```
sudo  mount /dev/sda10 /mnt 
sudo grub-install --root-directory=/mnt --recheck /dev/sda
```
(the first line is only necessary if you did reboot since the last time you mounted /dev/sda10)

(But the last command from my previous post ( "update-grub")  needs to be run in the chroot)

---

### Post by dougleduck on 2009-03-12
I now have a working computer! Thanks all for your time and advice. I don't quite understand what I've done though. Could somone tell me or point me to simple explanation of whats on the MBR,  where grub is installed, what needs to know where the menu.lst is etc? Thought I'd understood it when set up grub partition before but obviously didn't.

---

### Post by meierfra. on 2009-03-12
> Could someone tell me or point me to simple explanation of whats on the MBR, where grub is installed, what needs to know where the menu.lst is etc?

Grub comes in three stages: stage1 stage1.5 and stage2

The MBR is the first sector of the hard drive.

stage1 is installed in the MBR. The  physical location of stage1.5 is stored in stage1 and the  main purpose of stage1 is to call  stage1.5

stage1.5 is usually installed in the first few sectors after the MBR. stage1.5 is in charge of calling stage2. The hard drive ( say 1), partition (say 3)  and the path ( say /boot/grub/stage2) of stage2 are stored in stage1.5. So  stage1.5 will look for /boot/grub/stage2 on  the partition (hd1,3).

stage2 is installed in a file on the root (or boot or grub) partition.
stage2 is much larger than stage1 and stage1.5 and does the real booting.
The path of "menu.lst" is stored here and stage2  will use the information from menu.lst to create the Grub menu. Once you select a title in the Grub menu, stage2 will  read that item and carry out the instruction. Lets say menu.lst says:

title Ubuntu
uuid  1234...
kernel /boot/vmlinuz root=UUUID=abcd..  ro quiet
initrd  /boot/initrd.img


Then stage2 will  look for the files /boot/vmlinuz and /boot/initrd.img on the partition with the UUID 1234...  and loads the kernel (/boot/vmlinuz) and the initial file system (/boot/initrd.img)  into memory. The other parameters in the kernel line (root=UUUID=abcd..  ro quiet)  are not used by stage2, but are just past to the kernel.

The kernel (with help of the initial file system) will now continue the booting and sets up the root file system contained in the partition with UUID abcd...


I hope this makes some sense and (at least partially) answers your question.

---

### Post by dougleduck on 2009-03-15
Thanks, that was really clear and helpful. Maybe next time I'll work it out myself. (next time??? :S)

---

