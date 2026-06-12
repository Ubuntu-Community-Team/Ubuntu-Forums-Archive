---
title: "[SOLVED] second hard drive wont mount"
date: 2008-07-30
forum: Hardware
---

### Post by stompy11 on 2008-07-30
it says Cannot mount volume
invalid mount option when attempting to mount the volume

---

### Post by stompy11 on 2008-07-30
come on some ones got to help me

---

### Post by stompy11 on 2008-07-30
really need some help

---

### Post by vanadium on 2008-07-30
One problem is you do not provide information.
```
it says Cannot mount volume
```
What is "it"? What did you do when the message appeared? Did it work before?

What kind of a drive is it? Internal or external?

To provide detailed information, connect the drive if it is an external one, then open a terminal, copy/paste following commands and copy the entire output back here:

```

mount
sudo fdisk -l
cat /etc/fstab

```

This will at least show us what drives your system "sees', and which ones are mounted and not.

---

### Post by stompy11 on 2008-07-30
Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x816c816c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17495   140528556   83  Linux
/dev/sda2           17496       18241     5992245    5  Extended
/dev/sda5           17496       18241     5992213+  82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x81797ca2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   42  SFS
syn-text@syn-text-mainframe:~$ 
syn-text@syn-text-mainframe:~$ 



"it" is an internal seagate 750 gb hdd.
"it" worked until someone on here had me change a line in fstab to get my flash drive working. the flash drive works now. I tried asking about "it" then but got no answer so i started a new thread.

---

### Post by stompy11 on 2008-07-30
oh and I got the message when I tried to mount the volume.

---

### Post by vanadium on 2008-07-30
You changed /etc/fstab, but you do not want to post the contents of /etc/fstab? (see my previous post)

---

### Post by stompy11 on 2008-07-30
sorry i will when i get back to my comp.

---

### Post by stompy11 on 2008-07-31
syn-text@syn-text-mainframe:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5fdc9443-6905-4eda-8de4-6403ceec046a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d6e7d9bc-8170-4e6f-a08c-cbd91414dcb6 none            swap    sw              0       0
# /dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
syn-text@syn-text-mainframe:~$ 


hope this helps.

---

### Post by stompy11 on 2008-07-31
I read a post that it might be that the computer is picking it up as a CD rom is this a possibility?

---

### Post by stompy11 on 2008-07-31
I still need help guys.

---

### Post by mc4man on 2008-07-31
putting aside your hdd (seagate) for a moment your fstab was wrong in terms of your cd/dvd drive (am assuming you have one)
> # /dev/sdc1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
That should be /dev/scd0 or /dev/scd1, not sdc1 
why don't you ```
run sudo lshw -C disk
``` and get that squared away first.

---

### Post by falcon61102 on 2008-07-31
That shouldn't cause a problem.  What interests me is that you have two different Hardware ID's (UUID) for the same drive.  I think that might be your problem.

First, Backup your fstab file.
Guessing that you didn't change the settings for your swap drive, we'll try that info.  Copy the UUID which is: d6e7d9bc-8170-4e6f-a08c-cbd91414dcb6 and paste that where the UUID is for you /dev/sda1 partition, two lines above.  Restart and see what happens.

---

### Post by jocko on 2008-08-01
> **stompy11 said:**
> I read a post that it might be that the computer is picking it up as a CD rom is this a possibility?

No. Your output from fdisk clearly shows it is detected as a 750 Gb hard drive containing one partition (partitioned with a sfs (?) file system).
But you have no  entry in your fstab to tell your computer how to mount it, which may be one of the reasons it fails.
Could you post the output of this:
```
ls -la /dev/disk/by-uuid
```That will give information needed to make a correct entry in fstab.
Why do you have an sfs file system on it, and what is that? (according to google and wikipedia there are several (at least three) different file systems called "sfs" (simple file system, smart file system, security file system).

I also saw a case on [linuxforums.org ]("http://www.linuxforums.org/forum/redhat-fedora-linux-help/122563-help-required-accessing-sfs-filesystem.html")where a windows dynamic disk was detected as an sfs partition. Could that be your problem?
It may be possible to access a windows dynamic disk (according to [this post]("http://ubuntuforums.org/showpost.php?p=5462200&postcount=2")), but I have no idea how.
Apparently windows can't convert a dynamic disk to a basic disk without loosing all data, so the best advice I can give you is to back up all data you have on that drive (you would need windows for that) and format it to a "normal" partition type.




**WARNING: Do not follow the advice of this guy:**
> **falcon61102 said:**
> That shouldn't cause a problem. What interests me is that you have [COLOR=Red]two different Hardware ID's (UUID) for the same drive.[/COLOR] I think that might be your problem.

First, Backup your fstab file.
Guessing that you didn't change the settings for your swap drive, we'll try that info. [COLOR=Red]Copy the UUID which is: d6e7d9bc-8170-4e6f-a08c-cbd91414dcb6 and paste that where the UUID is for you /dev/sda1 partition, two lines above. Restart and see what happens.[/COLOR]
This will **totally** mess your computer up to a non-bootable state. The two different uuid's in the fstab SHOULD be different. They belong to DIFFERENT partitions. A UUID belongs to the partition, not the drive, so it is perfectly fine to have several different uuid's listed for different partitions (I would be worried if I would see several different partitions with the same uuid, though...)

---

### Post by mc4man on 2008-08-01
> it" worked until someone on here had me change a line in fstab to get my flash drive working. the flash drive works now
Here's where the drive stopped being able to be accessed, should be easy to backtrack and solve the problem(s).

[http://ubuntuforums.org/showthread.php?t=874447](http://ubuntuforums.org/showthread.php?t=874447)

another sfs possibility
[http://www.fs.net/sfswww/sfsfaq.html](http://www.fs.net/sfswww/sfsfaq.html)

The default for hardy for internal drives (partitions, ld's) is to require admin authentication for the active console, you should get a prompt for that when you d. click on the icon in places or computer. (at least the first time for drives not mounted at boot). You can also grant yourself, or any other user, Explicit authorization in not surprisingly, system -> authorizations -> storage.
There should no need to mkdir's, chown, fstab entries ect. for partitions that aren't, and you don't want, mounted at boot.

I've got 10 partitions across 2 hdd's of various fs types and it only took granting myself explicit in authorizations to gain rw, mount, unmount on them all. (d.click to mount, r.click to unmount, authentication remembered)

If you do have a cd/dvd drive you really should get it fixed in fstab, if you don't, you don't.

---

### Post by stompy11 on 2008-08-01
still need help guys.

---

### Post by stompy11 on 2008-08-02
syn-text@syn-text-mainframe:~$ ls -la /dev/disk/by-uuid
total 0
drwxr-xr-x 2 root root 120 2008-08-01 18:06 .
drwxr-xr-x 5 root root 100 2008-08-01 18:06 ..
lrwxrwxrwx 1 root root  10 2008-08-01 18:06 107C-091F -> ../../sdc1
lrwxrwxrwx 1 root root  10 2008-08-01 18:06 5fdc9443-6905-4eda-8de4-6403ceec046a -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-08-01 18:06 C020984F20984E72 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-08-01 18:06 d6e7d9bc-8170-4e6f-a08c-cbd91414dcb6 -> ../../sda5
syn-text@syn-text-mainframe:~$ 

now as far as the sds thing it was a dynamic disk in windoze.

---

### Post by stompy11 on 2008-08-02
And as for back tracking i have tried that to no avail (removed the #)

---

### Post by mc4man on 2008-08-02
At some point prior to all this you could actually access your windows drive with no problems ( and apparently no fstab entry) - correct?

Did you edit the /dev/sdc1.... in your fstab or was it always sdc1 
(or is it a typo, ie. your typing instead of copying and pasting into your posts and it's scd1)
any possibility it was /dev/sdb1 ?

clarify this > I got the message when I tried to mount the volume. How are you trying to mount the drive?

humor me and run
 sudo lshw -C disk

---

### Post by stompy11 on 2008-08-02
first: yes I could access it before
second: no I didnt edit it, and I was copying and pasting
third:   *-disk:0                
       description: ATA Disk
       product: WDC WD1500AHFD-0
       vendor: Western Digital
       physical id: 0
       bus info: scsi@4:0.0.0
       logical name: /dev/sda
       version: 21.0
       serial: WD-WMAP41885686
       size: 139GiB (150GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=816c816c
  *-disk:1
       description: ATA Disk
       product: ST3750640AS
       vendor: Seagate
       physical id: 1
       bus info: scsi@5:0.0.0
       logical name: /dev/sdb
       version: 3.AA
       serial: 5QD339ZJ
       size: 698GiB (750GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=81797ca2
  *-disk
       description: SCSI Disk
       product: Cruzer
       vendor: SanDisk
       physical id: 0.0.0
       bus info: scsi@10:0.0.0
       logical name: /dev/sdc
       version: 7.01
       serial: u
       size: 3835MiB (4022MB)
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdc
          size: 3835MiB (4022MB)
          capabilities: partitioned partitioned:dos
syn-text@syn-text-mainframe:~$ 

and fourth: exact message


**Cannot mount volume.**
Invalid mount option when attempting to mount the volume.

---

### Post by vanadium on 2008-08-02
The "SFS" file system is troubling me. Can you also add the output of

```

sudo blkid

```

Then, try mounting "manually" because this might reveal a more detailled error message (or just show the disk itself is mountable and OK)

Post commands and output here.
[code]
mkdir test
sudo mount /dev/sd1 test
touch test/This_is_a_test
ls test
rm test/This_is_a_test
sudo umount test
[code]

---

### Post by stompy11 on 2008-08-02
[code]
/dev/sda1: UUID="5fdc9443-6905-4eda-8de4-6403ceec046a" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="d6e7d9bc-8170-4e6f-a08c-cbd91414dcb6" 
/dev/sdb1: UUID="C020984F20984E72" TYPE="ntfs" 
[code]

it says /dev/sd1 does not exist

---

### Post by vanadium on 2008-08-02
I made an error: should have been sdb1 which is the partition that won't mount. blkid says this is an ntfs partition, so there is no secret. A common reason why an ntfs disk does not mount is that it is "unclean", i.e unproperly disconnected from Windows, which might be the case if Windows is hibernated instead of fully shut down. So first try to run the commands again, this time substituting the correct disk name. This will ascertain if that is the issie or not.

In the mean time, I hope you have the line for your cdrom fixed? You can verify wither the entry is to be /dev/scd0 with the command 

ls /dev/scd*

---

### Post by mc4man on 2008-08-02
you probably should run and post from this also (use maximized terminal for readability)

```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

The sandisk thumb drives are seen as a 'cdrom' and a removable disk (_unless you've removed the U3 partition_ ) Consequently they'll usually get  2 entries in 70...rules and be given device 'names' and /dev/links. With 2 hdd then typically s[COLOR="Red"]dc[/COLOR] and s[COLOR="Red"]cd[/COLOR]x 

Ex. 
```
# DVD_DD_DW1640 (pci-0000:00:1f.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:0:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:0:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:0:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"
# DVD_A_DH20A4P (pci-0000:00:1f.1-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
# U3_Cruzer_Micro (pci-0000:00:1d.7-usb-0:8:1.0-scsi-0:0:0:1)
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="SanDisk_U3_Cruzer_Micro_00001779A96170ED-0:1", SYMLINK+="cdrom2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="SanDisk_U3_Cruzer_Micro_00001779A96170ED-0:1", SYMLINK+="cdrw2", ENV{GENERATED}="1"
# U3_Cruzer_Micro (pci-0000:00:1d.7-usb-0:8:1.0-scsi-0:0:0:1)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1d.7-usb-0:8:1.0-scsi-0:0:0:1", SYMLINK+="cdrom3", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1d.7-usb-0:8:1.0-scsi-0:0:0:1", SYMLINK+="cdrw3", ENV{GENERATED}="1"

```

Ex.
```
  *-disk
       description: SCSI Disk
       product: U3 Cruzer Micro
       vendor: SanDisk
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdc
       version: 2.18
       serial: 3
       size: 3913MiB (4103MB)
       capabilities: removable
       configuration: ansiversion=2
     *-medium
          physical id: 0
          logical name: /dev/[COLOR="Red"]sdc[/COLOR]
          size: 3913MiB (4103MB)
          capabilities: partitioned partitioned:dos
  *-cdrom
       description: CD-R writer
       product: U3 Cruzer Micro
       vendor: SanDisk
       physical id: 0.0.1
       bus info: scsi@5:0.0.1
       logical name: /dev/cdrom2
       logical name: /dev/[COLOR="Red"]scd[/COLOR]2
       logical name: /dev/sr2
       version: 2.18
       serial: 3
       capabilities: removable audio cd-r
       configuration: ansiversion=2 status=ready
     *-medium
          physical id: 0
```
   

You don't need or want an fstab entry for the sandisk

_Do you have a cd/dvd drive?_ (nothing showed up in lshw)
If not then delete that line in fstab that you had commented.

Edit:
depending on what's in ..rules and whether you have a cd/dvd drive then it may make sense to delete all the entries in 70...rules, remove the sandisk ,reboot and don't insert the sandisk till things are squared away

---

### Post by jocko on 2008-08-02
> **vanadium said:**
> In the mean time, I hope you have the line for your cdrom fixed? You can verify wither the entry is to be /dev/scd0 with the command 

ls /dev/scd*

There is NOTHING wrong with a disk called sdc0 (or sda, sdb, hda and so on...), as long as it works... 
My dvd's are detected as hda and hdb, while one of my hard drives is hdc and two other hard drives are sda and sdb. It all depends on which hardware they are connected to, and which driver they use.
 
Did he say anywhere that his cdrom doesn't work? If not, don't tell him to change it. If it works the way it is, changing it *will* break it..

---

### Post by mc4man on 2008-08-02
From OP
> # /dev/sdc1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
 cdrom drive or the sandisk , i'd think the sandisk

> logical name: /dev/sdc
the sandisk

> lrwxrwxrwx 1 root root 10 2008-08-01 18:06 107C-091F -> ../../sdc1
appears to be the sandisk  (shouldn't even be there)


> sudo lshw -C disk ......
no cd/dvd drive listed

@stompy11
post ..70...rules and keep that pita sandisk on the shelf for a while

> 
A common reason why an ntfs disk does not mount is that it is "unclean

A possibility why sdb1 won't mount. Do You have windows installed on the seagate?, if so boot to it and run a chkdsk. If not I'm sure someone can tell you how to force or create a mount. (if it's just for storage at some point consider transferring data and re-formatting)
Go ahead and _delete_ that /dev/sdc1 line in fstab

And do confirm, do you have a cd/dvd drive?

edit: it seems like this is 2 separate issues that became 'intertwined' but aren't really (looking at first thread)

---

