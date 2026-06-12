---
title: "No UUID for my swap?"
date: 2008-08-04
forum: General Help
---

### Post by touchlikefire on 2008-08-04
Apparently my swap partition doesn't have a UUID?  How is this possible, and what can I do to correct it?

```
 sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc202b441

   Device Boot      Start         End      Blocks   Id  System
/dev/sda4            6528        8622    16828087+   5  Extended
/dev/sda5            6528        6540      104391   83  Linux
/dev/sda6            6541        6802     2104483+  82  Linux swap / Solaris
/dev/sda7            6803        7709     7285446   83  Linux
/dev/sda8            7710        8622     7333641   83  Linux

```

and:
```
sudo vol_id /dev/sda6
ID_FS_USAGE=other
ID_FS_TYPE=swap
ID_FS_VERSION=2
ID_FS_UUID=
ID_FS_UUID_ENC=
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

```

also:
```

ls /dev/disk/by-uuid/
cfcabf0f-2eaf-4516-9cd5-daad0738c482  f75471be-c087-4f7c-9a0c-4811c571bab7
dcf2ba3f-bb16-404a-9281-e6b7a5fe47e8

```

This is pretty imperative, to fix the usplash bug according to this thread:
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/205990]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/205990")

thanks in advance,

Preston

---

### Post by Elfy on 2008-08-04
It looks like you could use tune2fs or uuidgen to generate a UUId for the swap, not sure of the syntax though, for tune2fs it could be

```
sudo tune2fs -U random /dev/sdc1
``` for sdc1

BUT I'm not sure I reiteerate :)

the man page for tune2fs gives

> -U UUID
              Set the universally unique identifier (UUID) of  the  filesystem
              to UUID.  The format of the UUID is a series of hex digits sepa&#8208;
              rated          by          hyphens,          like          this:
              "c1b9d5a2-f162-11cf-9ece-0020afc76f16".   The UUID parameter may
              also be one of the following:

                   clear  clear the filesystem UUID

                   random generate a new randomly-generated UUID

                   time   generate a new time-based UUID

---

### Post by Elfy on 2008-08-05
Ok - I ran it on my scratch partition and 

```
sudo tune2fs -U random /dev/sda6
``` appeared to do the job on it.


Edit - after a reboot.

---

### Post by touchlikefire on 2008-08-07
First, your sig had tears in my eyes--I was laughing so hard.

Secondly, thanks so much for the info, looks like we're on to something.  I tried the code, and got:
```
tune2fs 1.40.8 (13-Mar-2008)
tune2fs: Bad magic number in super-block while trying to open /dev/sda6
Couldn't find valid filesystem superblock.
```

I'll see what happens after I reboot, but that might not be for a little bit.

---

### Post by Elfy on 2008-08-07
Ha ha - yea I laughed when he told me lol

Perhaps there is actually something wrong - you could delete the swap and build it again with gparted - you should be able to do that while buntu is booted - turn swap off first. Rebuild it - add it to fstab and remount 

{code]sudo swapoff -a[/code]

---

### Post by Rocket2DMn on 2008-08-07
You can also check with the command
```
sudo blkid
```
If it's not there, then it does seem like the partition is corrupted and should be recreated.  You shouldn't even need a LiveCD for that, just install GParted and go :)

---

### Post by mcduck on 2008-08-07
> **touchlikefire said:**
> First, your sig had tears in my eyes--I was laughing so hard.

Secondly, thanks so much for the info, looks like we're on to something.  I tried the code, and got:
```
tune2fs 1.40.8 (13-Mar-2008)
tune2fs: Bad magic number in super-block while trying to open /dev/sda6
Couldn't find valid filesystem superblock.
```

I'll see what happens after I reboot, but that might not be for a little bit.

Tune2fs, is only for Ext2/Ext3 file systems.

Try the "blkid" command suggested, it might be able to tell the UUID.

Also, I think that the "mkswap" command should create UUID for swap.

---

### Post by Elfy on 2008-08-07
> Tune2fs, is only for Ext2/Ext3 file systems.Thanks I missed the difference between ext3 and swap

Learn a new thing every day - I looked at mkswap and it appears to want you to supply the uuid - how would you do that

> -U uuid - Specify the uuid to use.

---

### Post by mcduck on 2008-08-07
> **forestpixie said:**
> Thanks I missed the difference between ext3 and swap

Learn a new thing every day - I looked at mkswap and it appears to want you to supply the uuid - how would you do that

I don't think you _need_ to specify an UUID. Just run mkswap for the partition and it will recreate the swap, and automatically give it an UUID.

---

### Post by touchlikefire on 2008-08-07
Thanks guys, the issue has been solved.  Here is what I did:

Turn swap off:
```
sudo swapoff -a
```

Then make new swap partition:
```
sudo mkswap /dev/sda6
``` where **/dev/sdax** is the desired swap partition.  Note: this command will destroy all data on the partition.

The output of the above command yields a UUID:
```
Setting up swapspace version 1, size = 2154983 kB
no label, UUID=f436f10e-1a07-4d84-8c2d-c07bd15f0611
```

And thusly, you have a UUID for your swap. :-)

---

