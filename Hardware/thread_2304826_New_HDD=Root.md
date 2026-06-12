---
title: "New HDD=Root?"
date: 2015-11-30
forum: Hardware
---

### Post by echotech2 on 2015-11-30
I installed a new HDD (sdd) to contain my ever-expanding collection of "moldy-oldie" music which is currently on a USB drive (Seagate Backup+.  

  I formatted sdd as one partition (ssd1, 250Mb) with GParted within Unity, not from a LiveCD.

  The problem I have is that ssd is now owned by root (because GParted was run as root?) and I can't copy anything to it as a normal user.  How do I change the permissions of ssd to normal user?

  PS: I may not be back for 24 hours or so.  This life thing you know.

---

### Post by brian-mccumber on 2015-11-30
Here is an article from askubuntu that should help you - [http://askubuntu.com/questions/43570/change-owner-of-internal-hard-drive-partition-from-root-to-user](http://askubuntu.com/questions/43570/change-owner-of-internal-hard-drive-partition-from-root-to-user)

---

### Post by oldfred on 2015-11-30
You may want both chmod & chown.

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data
[http://askubuntu.com/questions/324705/first-full-backup-on-usb-permission-denied/324942#324942](http://askubuntu.com/questions/324705/first-full-backup-on-usb-permission-denied/324942#324942)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

If drive is now an internal drive you probably want to also make it a permanent mount with fstab so you do not have to manually mount each time you reboot.

 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to. 

And then link folder(s) into /home so easy to get to. If just music you can directly mount in /home, just cannot use Music unless you delete the default folder in /home. If you delete it, make sure it is empty  and/or well backed up or copied to new drive.

---

### Post by echotech2 on 2015-12-01
Thanks for all the information brian-mccumber and oldfred (What do you consider "old"? I'm 70 (and a half)).

  What I did... "sudo nautilus" to change disk owner, group and set access... used "Disks" to set to "Automount".  Seems to have worked.

---

### Post by oldfred on 2015-12-01
I think I meant to use olefred. especially since you are about a yr older than me.

Not sure if default settings that Disks use are the best. You may want to compare your entry in fstab that it created to mount with the suggested one in link using the template. You could just update parameters.

---

### Post by echotech2 on 2015-12-02
This is what "blkid" for the disk shows.

```
LABEL="sdd" UUID="96f6a154-2ed4-4b96-8cc1-bf6d4b5cbecb" TYPE="ext4" PARTUUID="d209820e-01
```

  In "fstab" there is this entry. I'm not sure what it is.  The only other entries in "fstab" are "/", "/home" and "swap"

```
/dev/disk/by-id/wwn-0x2423227717994565632x-part1 /mnt/wwn-0x2423227717994565632x-part1 auto nosuid,nodev,nofail 0 0
```

---

### Post by oldfred on 2015-12-02
I always label partitions either when I use gparted to create them or when I forget use Disks to add the label.
You can mount a partition with device like /dev/sda1, but they stopped using that since device numbers can change. So the normally now use UUID. You can also use the label. I guess you also can use the by-id also.

I have lots of partitions, so I am only showing some, never have understood, by the disk/by-id has double entry, one is clearly the brand/model of drive, but other is the wmn- some long identifier. 
It also did not use what I have seen as typical mount paramaters, either those suggested in thread above or just my own simple relatime entry.
But using labels or creating your own mount points and using that mount makes info more understandable. Your fstab is incomprehensible without listings like I show below to allow cross reference, but it works.
```
 fred@trusy-ar:~$ ls -l /dev/disk/by-id
lrwxrwxrwx 1 root root 10 Dec  2 09:21 ata-WDC_WD10EZEX-00BN5A0_WD-WCC3FHUDFTHP-part5 -> ../../sdb5
lrwxrwxrwx 1 root root 10 Dec  2 09:21 wwn-0x50014ee2b5652750-part5 -> ../../sdb5

   fred@trusy-ar:~$ sudo blkid -c /dev/null -o list
[sudo] password for fred: 
device              fs_type   label      mount point             UUID
-----------------------------------------------------------------------------------------------------
/dev/sdb5           ext4      backup     /mnt/backup             084de40f-8ffd-4af1-97b1-8a60cdd9aab4
/dev/sdb6           ext4      iso_hdd    (not mounted)           7f360ddc-d9fb-4a40-b17a-f2d5af6b61ed

   fred@trusy-ar:~$ cat /etc/fstab
# /etc/fstab: static file system information.
....
# Entry for /dev/sdc4 :
UUID=a0c1c99f-0f09-4787-a7cc-9e15bb3b4aa5 /mnt/data ext4 relatime 0 2
# Entry for /dev/sdb5 :
UUID=084de40f-8ffd-4af1-97b1-8a60cdd9aab4 /mnt/backup ext4 relatime 0 2


```

---

### Post by echotech2 on 2015-12-03
Thanks for all the info.  I'll digest more of it later.  

  I plugged in the command in your example.  The result....

```
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /              d4a3dd22-6757-4d0b-906a-f5ac49b0fad5
/dev/sda3  ext4             /home          4c6dd994-9f17-42bd-918d-eacf00d0f294
/dev/sda5  swap             [SWAP]         bdb527f0-2635-487d-ae61-868e16212737
/dev/sdb1  ext4    data     (not mounted)  2cc15ef2-164e-464a-8fb8-d4af8087b7ad
/dev/sdc1  ext4    media-usb /media/dave/media-usb ee94a57b-777c-4b55-b0bd-336783121283
/dev/sdd1  ext4    sdd      (not mounted)  96f6a154-2ed4-4b96-8cc1-bf6d4b5cbecb

```

  sda is an SSD
  sdb1 - data and miscellaneous junk
  sdc1 is a 1tb USB flash drive containing my media.
  sdd1 is where I want to transfer the media to and is the new drive I just added.  Even though it shows as "not mounted" I successfully copied everything sdc1>sdd1 and everything works.  I guess it gets mounted when you access it?
 
  The same with sdb1, "not mounted" but no problems.  One of these days I'll figure everything out, lol.

---

