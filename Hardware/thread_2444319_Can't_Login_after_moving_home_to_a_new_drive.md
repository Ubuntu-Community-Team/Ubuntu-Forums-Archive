---
title: "Can't Login after moving /home to a new drive"
date: 2020-05-28
forum: Hardware
---

### Post by triwave on 2020-05-28
Hello,

I was reading another thread on similar subject and was encouraged to post a new thread ... so here goes.

I read here: [https://ubuntuforums.org/showthread.php?t=2435021]("https://ubuntuforums.org/showthread.php?t=2435021") on there general process recommended by @jimmyrus 

> **jimmyrus said:**
> Depends on what your doing. If you're just running out of space on your home, you could just format the new drive, copy your home folders over to it and reboot into single user mode. Change your fstab to mount the new drive as /home, and that's all. Could also just move stuff to it, and symlink things like /var to the new drive and you won't have to mess with lvm at all.

I was doing as suggested and ran into some trouble - looking for some advice where to look to debug and fix.

My 18.04 system was all on a single drive with a separate partition for / and /home

I added a new drive I want to use as /home - so I made an EXT4 partition and copied the user directory to that drive using rsync (actually Grsync GUI) with preserve options for date, permissions, owner ... 

I can mount that drive while still running original system and everything seems intact.

Now I modified fstab to set new drive for /home , reboot , and get stuck at login screen. I am presented with login box and enter password ... then it flashes and goes back to login screen.  I looked at journal log in terminal recovery mode and see an error that goes something like this:

```
mount: /home : wrong fs type, bad option, bad superblock on /dev/sdc1, missing codepage or helper program, or other error
kernel: EXT4-fs (sdc1) : VFS: Can't find ext4 filesystem
Then few more lines all indicating mount process failed and exited with code status=32
```

Since I mount it manually and gparted shows it as EXT4 I guess it's something else? What did I do wrong? Maybe didn't format correctly or superblock issue?

Appreciate any pointers in the right direction ... I'm sure it's something small I overlooked.

Thanks so much

---

### Post by TheFu on 2020-05-28
Please post some facts.
[LIST]
[*]The fstab
[*]Can you manually mount the disk using a "Try Ubuntu" flash drive?
[*]Can you run fsck on the specific partition/LV where you created the ext4 file system?
[*]If you moved stuff with grsync, it is easily possible the permissions and owner were not maintained. Only root/sudo can do that and using sudo with GUI programs is problematic.
[/LIST]

Have you reviewed the Ubuntu Wiki/Help for moving /home to a different partition? Google should find it.

---

### Post by triwave on 2020-05-28
Here are some more details:

fstab: ( I have tried both UUID and sdc1 as devices - no difference ; if I switch back to original SSD no problem )

```
# <file system> <mount point> <type> <options> <dump> <pass>

UUID=bc03a0e0-c093-4916-9a49-745f8daf18b1	/	ext4	errors=remount-ro	0	1
UUID=D4AB-EA98	/boot/efi	vfat	umask=0077	0	1
# This was original entry for home on the SSD
# UUID=7dd38d6d-e1a2-407d-938e-ff11900f9703	/home	ext4	defaults	0	2
UUID=d803bddb-a8b7-4ffd-af2e-6c5c1a3b5df6	none	swap	sw	0	0
# This is moving home to the 1GB harddrive
/dev/sdc1	/home	ext4	defaults	0	0
# UUID=0fe39153-cb1a-4992-967a-ca2e8410bd9f	/home	ext4	defaults	0	2
```

> Can you manually mount the disk using a "Try Ubuntu" flash drive?

I have booted with a live USB and manually mounted the drives to get this information

> Can you run fsck on the specific partition/LV where you created the ext4 file system?

Yes, when running the live USB the partition is sdd1

```
elementary@elementary:/mnt/mysystem/etc$ sudo fsck /dev/sdd1
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
Homedrive2: clean, 80605/61054976 files, 10956704/244190000 blocks
```

I tried to select the correct settings with grsync - I have review quite a few articles and there are many ways to move the data - using Backup, timesync, cp, rsync, dd , etc so I didn't see a lot of specificity there other than preserving the permissions and owner. This seems a possible suspect though so I'll dig on the permissions a bit more...

Thanks

---

### Post by bilkay on 2020-05-28
You may not be trying to mount what you think you're mounting. Mount it, cd to it and do `df .`. Find the UUID: `sudo blkid {whatever device df shows}` and substitute "UUID={block ID} for "/dev/sdc1" in /etc/fstab.

---

### Post by TheFu on 2020-05-28
Well, the fstab lines are commented out and there are 2 different lines for /home.
I wouldn't assume sdc1 or sdd1 is the correct device to be used for manual mounts.  Devices change order from boot-to-boot. You'd need to check that every time. I'd use **dmesg** output or **sudo parted -lm** and check the specific partition sizes.

Can you show the permissions for the mounted directory?  After you do a manual mount, **ls -al /home/**

As for copying all the files over correctly, the new storage should be temporarily mounted somewhere while using single-user mode or a "Try Ubuntu" boot.  Then mount the original and the target storage.  Say ... the original is in /mnt/home and the new storage gets mounted to /mnt/1, then the rsync command to use would be
```
$ sudo rsync -av /mnt/home/ /mnt/1/
```
or without sudo, running as root
```
# rsync -av /mnt/home/ /mnt/1/
```

If rsync isn't already installed, just install it into the Try Ubuntu environment. While you are there, edit the fstab to use a LABEL= or UUID= for the /home mount.  Or you can use the symbolic links from any of the directories created by the boot discovery processes ... doesn't really matter which you use, but they are under /dev/disk/by-*  Just make certain that the current link is pointing to the correct sdc1 or sdd1 or sde1 or sdX1 where the new storage is.
```
$ ls -F /dev/disk/by-*
by-id/       by-label/    by-partuuid/ by-path/     by-uuid/
```
Or use the blkid command, if you like.  These links are guaranteed to be correct at boot, so it doesn't matter which you use. In the fstab, the 
/dev/disk/by-uuid/XXXX-xxxx-twerwe-wsdfasdfw-ddfdsd    works.  Just make certain the symlink points at the correct partition device at the time.

---

### Post by triwave on 2020-05-28
> Well, the fstab lines are commented out and there are 2 different lines for /home.
I wouldn't assume sdc1 or sdd1 is the correct device to be used for manual mounts. Devices change order from boot-to-boot. You'd need to check that every time. I'd use dmesg output or sudo parted -lm and check the specific partition sizes.

Well fstab is in /etc so that isn't changing ... I commented out lines so I can switch between the original (working) /home and the new (not working) /home

I doubled checked the new drive mapping , but you can see the line above is by UUID which id for the new drive but it didn't make any difference. 

I found the ubuntu wicki for moving /home and I've followed it except for manually using rysnc and instead using grsync   ...   sighh ... maybe i have to do my backup all over again :(

---

### Post by triwave on 2020-05-28
> **bilkay said:**
> You may not be trying to mount what you think you're mounting. Mount it, cd to it and do `df .`. Find the UUID: `sudo blkid {whatever device df shows}` and substitute "UUID={block ID} for "/dev/sdc1" in /etc/fstab.

Thanks for the idea - Tried it this way too - get the same UUID I have been using in fstab so no issue there

---

### Post by TheFu on 2020-05-28
So, no **ls -al** coming?
Also, there are multiple ways to use the UUID as the first parameter. Shouldn't matter, but in 20.04 the default seems to use the /dev/disk/by-UUID/...... method.

---

### Post by bilkay on 2020-05-29
Any reason why the sixth parameter on the fstab entry for /dev/sdc1 is 0? According to `man fstab` it should be 2 (as on the UUID= line for /home).

---

### Post by TheFu on 2020-05-29
> **bilkay said:**
> Any reason why the sixth parameter on the fstab entry for /dev/sdc1 is 0? According to `man fstab` it should be 2 (as on the UUID= line for /home).

The fstab manpage says:
```
        The sixth field (fs_passno).
              This field is used by fsck(8) to determine the  order  in  which
              filesystem  checks  are  done at boot time.  [I]The root filesystem
              should be specified with a fs_passno of  1.[/I]   [B]Other  filesystems
              should  have  a fs_passno of 2.[/B]  Filesystems within a drive will
              be checked sequentially, but  filesystems  on  different  drives
              will  be  checked at the same time to utilize parallelism avail&#8208;
              able in the hardware.  Defaults to  zero  (don't  fsck)  if  not
              present.

```

But it doesn't matter for mounting just when to run fsck based on the tune2fs settings for the ext[234] file systems.

---

### Post by triwave on 2020-05-29
Hi all - thanks for the ideas and feedback - I believe I have a working system now :)

I am still testing and verifying but so far all is good ... I believe the secret is in the permissions when copying files as TheFu suggested

> If you moved stuff with grsync, it is easily possible the permissions and owner were not maintained. Only root/sudo can do that and using sudo with GUI programs is problematic.

More and more reading indicates you can do it many ways but it's important to handle the flags and options in  aparticular way so there are permission issues. Seems manually running [COLOR="#008000"]rsync with the -a flag was built for just this purpose[/COLOR].

I reformatted my new drive and used rsync -av to get the old /home directory over there. UUID changed so I updated fstab to mount by the new UUID and presto. New 1TB home directory :D

---

