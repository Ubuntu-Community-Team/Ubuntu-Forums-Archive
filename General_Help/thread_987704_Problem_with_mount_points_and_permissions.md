---
title: "Problem with mount points and permissions"
date: 2008-11-19
forum: General Help
---

### Post by thilmegil on 2008-11-19
I am new to linux and have multiple physical drives with a few drives having multiple partitions. I have several drives that i can unmount but can not remount. Also since i installed ubuntu i had to pull out a couple of drives and put them back in, now the dev name is different so the mount points are no good so i think i need to fix my fstab file but im too new to want to risk doing this without help. Here are some specs:

Ubuntu 8.04 64bit
4 gigs of ram
AMD Athlon 64 X2 6400+
MSI K9A2 Platinum motherboard

and my fdisk -l output:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00085dcb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44034402

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2               1       36482   293041633+   5  Extended
/dev/sdc5            6375       36482   241842478+  83  Linux
/dev/sdc6               1         249     1999998   83  Linux
/dev/sdc7             250        6374    49199031   83  Linux

Partition table entries are not in disk order

Disk /dev/sdd: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06a506a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       14946   120053713+  83  Linux

Disk /dev/sde: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19a500bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       30515   245111706   83  Linux

Disk /dev/sdf: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbd6cbd6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       14946   120053713+  83  Linux

Disk /dev/sdg: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2111ac4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1        1992    16000708+  83  Linux
/dev/sdg2            1993        3984    16000740   83  Linux
/dev/sdg3            3985        4867     7092697+  82  Linux swap / Solaris
/dev/sdg4            4868       14593    78124095   83  Linux


and my fstab:

proc /proc proc defaults 0 0
# Entry for /dev/sdg1 :
UUID=356f4584-ad35-4877-b32b-ebb6d71006c8 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdg2 :
UUID=376fc118-4918-45a2-97ea-aaab3ff9b5fc /home ext3 relatime 0 2
# Entry for /dev/sdc6 :
UUID=620e5b69-48b8-4f86-9cd1-9a0ae21363ee /media ext3 relatime 0 2
# Entry for /dev/sda1 :
UUID=bcfa727a-905b-4f39-a01d-9e448c62c794 /media/anime ext3 relatime 0 2
# Entry for /dev/sdf1 :
UUID=ccf96b2e-a729-44da-a881-22c437515d9a /media/extras ext3 relatime 0 2
# Entry for /dev/sde1 :
UUID=c5626e59-e4ed-4a1e-a99b-43965f3912ff /media/moviediscs ext2 relatime 0 2
# Entry for /dev/sdd1 :
UUID=e9596eae-9f0a-44a3-94a8-9e2e4cd9228d /media/moviefiles reiserfs relatime 0 2
# Entry for /dev/sdc5 :
UUID=0CCC7B41CC7B245C /media/moviefolders ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sdg4 :
UUID=eaa5832d-0da4-45c1-ac20-6332e206c403 /media/music ext3 relatime 0 2
# Entry for /dev/sdb1 :
UUID=f0e81d6c-9db3-4330-afb4-f1614eb8297b /media/tvshows ext3 relatime 0 2
# Entry for /dev/sdg3 :
UUID=47b71bd5-38d7-45f2-a0f3-4bad2579d264 none swap sw 0 0
/dev/sdg1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/hdb /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

Any help would be greatly appreciated.

---

### Post by drs305 on 2008-11-19
First the good news: The fstab entries are (mostly) in UUID format, meaning they won't change if you swap drives around (they will change only if you reformat the partitions). The comment lines above each entry, however, may not be accurate and can be a cause of either confusion or worse if you rely on incorrect/outdated information in the comments. So I would recommend you run "sudo blkid" and make sure the UUIDs match the /dev designation.

To be able to mount the drives, you can add "users" to the options, for example:
```

UUID=eaa5832d-0da4-45c1-ac20-6332e206c403 /media/music ext3 **users**,relatime 0 2
```

Next, depending on your computer situation, you can make yourself the owner of the mountpoints. If you are the only user of the computer or just want to take ownership and set the permissions of all the extra partitions, run:
```

sudo chown -R *yourusername:yourusername* /media
chmod -R 750 */media*

```
For individual partitions only, instead of "/media" use "/media/*specific-mountpoint*"

For the ntfs partitions, things are a bit different, so the entry can be a bit more complicated. The following would set yourself (if uid=1000) as the owner, would automount, and set the owner, group and other permissions:
```

UUID=0CCC7B41CC7B245C /media/moviefolders ntfs-3g defaults,*uid=1000,users,umask=027*,locale=en_US.UTF-8 0 0

```
Also note I changed the last digit to a "0". This digit effects when an fsck check is performed, and these checks are not accomplished on ntfs partitions (hence the "O").

---

### Post by thilmegil on 2008-11-19
Ok i did this:

sudo chown -R yourusername:yourusername /media

but the chmod didn't work. i got this:

chmod -R 750 yourusername

chmod: cannot access yourusername: No such file or directory

I still can't remount the unmounted drive.
Also the NTFS partition is no more, its an ext3 partition now.
Also  one of the drives that is mounting as cdrom is not a cdrom. its actually the OS drive.

---

### Post by drs305 on 2008-11-19
Sorry, it should be:

Once you have changed ownership:
```

chmod -R 750 /media/mountpoint
*or for all /media mountpoints:*
chmod -R 750 /media

```


Which one won't mount?

---

### Post by thilmegil on 2008-11-19
Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2               1       36482   293041633+   5  Extended
/dev/sdc5            6375       36482   241842478+  83  Linux
/dev/sdc6               1         249     1999998   83  Linux
/dev/sdc7             250        6374    49199031   83  Linux

Partition table entries are not in disk order
-----------------------------------------------------------------
trying to mount sdc7 and sdc5

I want to be able to have all my partitions mounted under /media
I'm guessing i am going to have to go edit fstab to make this happen but i dont really know enough yet to do that solo.

---

### Post by drs305 on 2008-11-19
> **thilmegil said:**
> Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2               1       36482   293041633+   5  Extended
/dev/sdc5            6375       36482   241842478+  83  Linux
/dev/sdc6               1         249     1999998   83  Linux
/dev/sdc7             250        6374    49199031   83  Linux

Partition table entries are not in disk order
-----------------------------------------------------------------
trying to mount sdc7 and sdc5

I want to be able to have all my partitions mounted under /media
I'm guessing i am going to have to go edit fstab to make this happen but i dont really know enough yet to do that solo.

Hey, we can help.

I'll do sdc5, you can repeat for sdc7.

Make a mount point for sdc5 (Name it what you wish) Bold requires user input if you name it something other than sdc5:
Make the mountpoint:
```
sudo mkdir /media/**sdc5**
```
Example: sudo mkdir /media/myfiles

Change ownership of mountpoint to yourself and set permissions. Replace *username* with your logon name:
```
sudo chown -R *username:* /media/**sdc5**
chmod -R 750 /media/**sdc5**

```

Backup fstab and open for editing (example uses gedit but you can use any text editor):
```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```

Add this line:
```

/dev/sdc5 /media/**sdc5** ext3 defaults,users 0 2 

```
Save fstab (but keep it open to repeat for /dev/sdc7)
Example: /dev/sdc5 /media/myfiles ext3 defaults,users 0 2 

Mount the new partition:
```

sudo mount /dev/**sdc5**

```
When you run this command, after entering the password, nothing should happen on the command line. This means it mounted successfully.

Repeat for /dev/sdc7.

Note: Using a UUID has advantages over using "/dev/sdXX". If you wish to use the UUID: To get the UUID, run "sudo blkid". Substititue "UUID=" and the number for "/dev/sdXX" in fstab. You can look at the other entries for UUID partitions to see how it's done.

I have to leave but if you have any questions there will be others that will be glad to answer them.

---

### Post by thilmegil on 2008-11-19
Ok, i'm doing that now.

Another question.

How do i get the /cdrom0 and /cdrom1 removed? I dont like the folders being there and not actually being linked to something

# Entry for /dev/sdg3 :
UUID=47b71bd5-38d7-45f2-a0f3-4bad2579d264 none swap sw 0 0
/dev/sdg1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/hdb /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

---

