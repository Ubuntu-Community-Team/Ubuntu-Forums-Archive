---
title: "The permissions of (drive) could not be determined"
date: 2009-05-04
forum: Hardware
---

### Post by Ozdemon on 2009-05-04
I have just installed a 1TB drive on my old machine.  I followed the instructions here [https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive")

That included the command 
sudo chown -R USERNAME:USERNAME /media/datadrive

Now the drive - named 1000.2 GB media -  sits on the desktop like a usb drive (it is an internal sata).  If I right click and go to permissions I get a message "The permissions of "datadrive" could not be determined'

I cannot rename the drive.  I do not understand why the drive does not just form part of the filesystem.

My fstab is as follows:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=592ac30f-b65d-4759-85d6-c2dd80eecd0f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b243497a-e16c-4f39-8b6c-2b1351e25e21 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1    /media/datadrive   ext3    defaults     0        2


Have I missed something?

---

### Post by taurus on 2009-05-04
Did you replace the USERNAME with your actual login name?  What are the outputs of these commands from a terminal?

```
sudo fdisk -l
ls -la /media
id
```

---

### Post by Ozdemon on 2009-05-04
> **taurus said:**
> Did you replace the USERNAME with your actual login name?  What are the outputs of these commands from a terminal?

```
sudo fdisk -l
ls -la /media
id
```

Tks for the quick reply.  I used my correct user-name.  The output of the commands you specified are:

tpb@tpb-htpc:~$ sudo fdisk -l
[sudo] password for tpb: 

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29162915

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9591    77039676   83  Linux
/dev/sda2            9592        9964     2996122+   5  Extended
/dev/sda5            9592        9964     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x0003a04d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1     1938021   976762552+  83  Linux
tpb@tpb-htpc:~$ 

===================================================================
tpb@tpb-htpc:~$ ls -la /media
total 24
drwxr-xr-x  6 root root 4096 2009-05-05 09:22 .
drwxr-xr-x 21 root root 4096 2009-05-04 20:40 ..
lrwxrwxrwx  1 root root    6 2009-05-04 20:30 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2009-05-04 20:30 cdrom0
drwxr-xr-x  2 root root 4096 2009-05-04 20:30 cdrom1
drwxr-xr-x  7 tpb  tpb  4096 2009-05-05 07:46 datadrive
lrwxrwxrwx  1 root root    7 2009-05-04 20:30 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2009-05-04 20:30 floppy0
-rw-r--r--  1 root root    0 2009-05-05 09:22 .hal-mtab
=================================================================
tpb@tpb-htpc:~$ id
uid=1000(tpb) gid=1000(tpb) groups=4(adm),20(dialout),24(cdrom),46(plugdev),106(lpadmin),121(admin),122(sambashare),1000(tpb)
tpb@tpb-htpc:~$ 
================================================================

Hope this helps.

---

### Post by taurus on 2009-05-04
Any error message when you run this command from a terminal?

```
touch /media/datadrive/testing
```

---

### Post by Ozdemon on 2009-05-04
> **taurus said:**
> Any error message when you run this command from a terminal?

```
touch /media/datadrive/testing
```

No, it just goes back to the $ prompt

---

### Post by taurus on 2009-05-04
Then it means you are able to write to that directory.

```
ls -la /media/datadrive
```
You should see a file called testing and you can remove it with

```
rm /media/datadrive/testing
ls -la /media/datadrive
```

---

### Post by pastalavista on 2009-05-04
Open Synaptic and install 'pysdm' which is a "Storage Device Manager". Shows up in System>>Administration menu.

---

### Post by Ozdemon on 2009-05-04
> **taurus said:**
> Then it means you are able to write to that directory.

```
ls -la /media/datadrive
```
You should see a file called testing and you can remove it with

```
rm /media/datadrive/testing
ls -la /media/datadrive
```

Yes, all correct.  However, I still have the permissions error message, and I can't change the name of the drive.  Also, (and it's not a big deal) I do not understand why this drive sits as an icon on my desktop as if it is an external drive.

I should be grateful it works at all. I initially connected it with xp in the c drive - xp instantly died.  So I ditched xp and installed Ubuntu 9.04 which worked out of the box and the speed improvement on this old PC is just amazing.

---

### Post by taurus on 2009-05-04
The name of the drive?  Are you talking about the volume label?

If you want to change the volume label of the drive, use tune2fs.

```

       tune2fs - adjust tunable filesystem parameters on ext2/ext3 filesystems

       -L volume-label
              Set  the volume label of the filesystem.  Ext2 filesystem labels
              can be at most 16 characters long;  if  volume-label  is  longer
              than  16  characters, tune2fs will truncate it and print a warn&#8208;
              ing.  The volume label can be used  by  mount(8),  fsck(8),  and
              /etc/fstab(5)  (and  possibly  others)  by specifying LABEL=vol&#8208;
              ume_label instead of a block special device name like /dev/hda5.

```

And if you don't want an icon on your desktop, either mount it to somewhere else like /mnt (/mnt/datadrive) instead of /media or "turn" off that option in nautilus.

---

### Post by Ozdemon on 2009-05-04
> **taurus said:**
> The name of the drive?  Are you talking about the volume label?

If you want to change the volume label of the drive, use tune2fs.

```

       tune2fs - adjust tunable filesystem parameters on ext2/ext3 filesystems

       -L volume-label
              Set  the volume label of the filesystem.  Ext2 filesystem labels
              can be at most 16 characters long;  if  volume-label  is  longer
              than  16  characters, tune2fs will truncate it and print a warn&#8208;
              ing.  The volume label can be used  by  mount(8),  fsck(8),  and
              /etc/fstab(5)  (and  possibly  others)  by specifying LABEL=vol&#8208;
              ume_label instead of a block special device name like /dev/hda5.

```

Okay, will try that.  Many thanks for your help.  :)

---

