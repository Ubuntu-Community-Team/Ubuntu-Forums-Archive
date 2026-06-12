---
title: "[SOLVED] Mounting a Drive"
date: 2008-08-29
forum: General Help
---

### Post by bpdp on 2008-08-29
Hello everyone,
I followed these instructions to install a new hard drive:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

I copied everything from the old drive onto the new one. everything went smooth but I had major trouble trying to boot from the new drive. so I decided just to start fresh and re-install hardy-server edition on the new drive. 

I have one directory on the old drive that houses all of our work that I need to copy to the new drive.

I created a new directory:
sudo mkdir /media/sam40
when I try to mount:
sudo mount /dev/sdb /media/sam40
I get this error: "mount: you must specify the filesystem type"
I tried a bunch of different types and the only one that doesn't result in an error is:
sudo mount -t tmpfs /dev/sdb /media/sam40/

sudo lshw -C disk says that the drive is mounted:
*-disk:1
       description: ATA Disk
       product: SAMSUNG SV4002H
       physical id: 1
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       logical name: /media/sam40
       version: QP10
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 mount.fstype=tmpfs mount.options=rw,relatime signature=55054103 state=mounted

but when I ls -lah in /media/sam40 there are no files. basically I feel that the old drive is not mounted properly. can anyone help me troubleshoot this? let me know if any other output would be helpful.

---

### Post by Crafty Kisses on 2008-08-29
Hmmm, post the results of the following command:
```
sudo fdisk -l
```

---

### Post by drs305 on 2008-08-29
The command to see what is mounted is.... "mount" !

All we really need to know is the file type, which is why Codename asked you to give us the results of "sudo fdisk -l" (note small L).

Give us that information and we can get your partition mounted correctly. My understanding is that you have your system on a different partition and you are now just trying to access a secondary drive/partition...

---

### Post by bpdp on 2008-08-29
Thanks, below is the output:
```

sudo fdisk -l 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00008d1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19269   154778211   83  Linux
/dev/sda2           19270       19457     1510110    5  Extended
/dev/sda5           19270       19457     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55054103

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4683    37616166   83  Linux
/dev/sdb2            4684        4870     1502077+   5  Extended
/dev/sdb5            4684        4870     1502046   82  Linux swap / Solaris

```

and

```

mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb on /media/sam40 type tmpfs (rw)
/dev/sdb on /media/sam40 type tmpfs (rw)


```

---

### Post by drs305 on 2008-08-29
First, unmount all your non-system drives (you will get a couple of error or unable messages, but that is ok).
```

sudo umount -a

```

It is an ext3 partition so the mount command should simply be:
```

sudo chown -R ***yourusername:*** /media/sam40
chmod -R 755 /media/sam40
sudo mount -t ext3 /dev/sdb1 /media/sam40

```

The first command ensures you own the mountpoint, the second sets permissions.

---

### Post by bpdp on 2008-08-29
I get this error:
```
sudo mount -t ext3 /dev/sbd1 /media/sam40
mount: special device /dev/sbd1 does not exist
```

I think this was the error I got originally.

---

### Post by drs305 on 2008-08-29
> **bpdp said:**
> I get this error:
```
sudo mount -t ext3 /dev/sbd1 /media/sam40
mount: special device /dev/sbd1 does not exist
```

I think this was the error I got originally.

In your first post it appeared you were trying to mount /dev/sdb instead of /dev/sdb1, but obviously there is still a problem. Would you post your fstab?

```
cat /etc/fstab
```

If there are any UUIDs in it, also:
```
sudo blkid
```

---

### Post by scalywag66 on 2008-08-29
hey hey!!!  I kind if have the same problem and just made a thread about it [here]("http://ubuntuforums.org/showthread.php?t=904834").  I'll paste the post here since this thread seems more active.  [IMG]http://www.systemwars.com/forums/images/smilies/icon_smile.gif[/IMG]

.....

I have a slight problem with not being able to mount/view the hard drive that is actually holding the partition that is running Ubuntu.

The PC I'm testing Ubuntu on first before I actually install it on the other pcs, has 80GB of hard drive space, but supposedly has 2 hard drives. I say supposedly 2 hard drives because on a couple times that I had to do System Recovery on this machine, it would ask me before finalizing the recovery process if I wanted to keep:

C: at 30GB & D: at 50GB,

or if I wanted to change the hard drive space between the two drives, which made me think, "shouldn't the memory be dedicated for each drive instead of being interchangeable?".

So anyways, since D drive has more room, I made the Ubuntu partition to be on D drive. On Ubuntu, I am able to explore C drive with no problem, but can't see the rest of the D drive that isn't partitioned, and I have some applications on D: that I would like to test with Wine. 

Any idea on how to mount the rest of D: and why I can't see it?

---

### Post by bpdp on 2008-08-29
> **drs305 said:**
> In your first post it appeared you were trying to mount /dev/sdb instead of /dev/sdb1

Right, I actually tried them both. I do appreciate you patience.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0836161c-c20f-4503-af91-7a5c81fcdb21 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1442cf46-1b7d-436d-9b35-bedfbc7161bd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

and

```
sudo blkid 
/dev/sda1: UUID="0836161c-c20f-4503-af91-7a5c81fcdb21" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="1442cf46-1b7d-436d-9b35-bedfbc7161bd" 
/dev/sdb1: UUID="2bf4b2c1-62ec-4d02-9a82-e275d8748743" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="b9917489-2164-40e9-abe1-2898dcd9c2d5"
```

---

### Post by drs305 on 2008-08-29
bdpd,

Let's try adding sdb1 into fstab. You can substitute your editor for gedit if you wish:

Backup and open for editing:
```

sudo cp /etc/fstab /etc/fstab.old
gksu gedit /etc/fstab
```

Add this line to your fstab:
```

/dev/sdb1 /media/sam40  ext3 defaults,user 0 2 

```

Save, then (you will get some 'busy' errors):
```

sudo umount -a
sudo mount -a
```

Normally the umount/mount commands will reset everything. There is something wrong with the way the system is reading your /dev/sdb1 so if the above doesn't work you might try rebooting to see if that solves things.

---

### Post by bpdp on 2008-08-29
Sweet, it worked! thanks!

I'll have to do some research about what the defaults,user 0 2 mean. But I'm learning a lot here. Thanks again.

---

### Post by drs305 on 2008-08-29
> **bpdp said:**
> Sweet, it worked! thanks!

I'll have to do some research about what the defaults,user 0 2 mean. But I'm learning a lot here. Thanks again.

Glad this is resolved.

[Introduction to Fstab]("https://help.ubuntu.com/community/Fstab")

[Understanding Fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

If you believe this thread is solved please mark it so using the "Thread Tools" link near the top right of the original post.

By the way, welcome to the Ubuntu Forums.

[SIZE=2]
***Official Support Links:***
System > Help and Support
[Ubuntu Wiki - Guides]("http://ubuntuguide.org/wiki/Main_Page")
[Launchpad]("https://launchpad.net/ubuntu/+addquestion")
[Ubuntu IRC]("https://help.ubuntu.com/community/InternetRelayChat")
[Search the Ubuntu Forums]("http://www.google.com/search?hl=en&as_q=+&as_epq=&as_oq=&as_eq=&num=30&lr=&as_filetype=&ft=i&as_sitesearch=ubuntuforums.org&as_qdr=w&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images")
[/SIZE]

---

