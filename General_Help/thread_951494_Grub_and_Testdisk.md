---
title: "Grub and Testdisk"
date: 2008-10-18
forum: General Help
---

### Post by nextbgates95 on 2008-10-18
Got myself into a bit of a pickle.  I sperated my Windows Vista partion and a documents partition, because I didn't want to lose my documents if Windows failed.  I went to install Ubuntu, and out of nowhere, my home partition was deleted.  I used testdisk (in Windows) to recover that partiton, but now, GRUB won't boot, and is giving me error 17.  I tried reinstall GRUB using the console, but that wasn't working.  I thought I would try and reinstall Ubuntu, but Gparted shows my entire drive as unallocated.

I cannot download test disk to Ubuntu, I am on a different computer, which only has 56/k.  It says the archive is corrupted, becuase it ends unexpectedly.

Suggestions?

---

### Post by EcthelionGenesis on 2008-10-18
Hmm... Your description is a bit confusing!

> **nextbgates95 said:**
> Got myself into a bit of a pickle.  I sperated my Windows Vista partion and a documents partition, because I didn't want to lose my documents if Windows failed.

Right, Ok. That far I can understand.

> **nextbgates95 said:**
> I went to install Ubuntu, and out of nowhere, my home partition was deleted.

So, you created a partition in Windows, which you want to mount as /home? Well, to begin with, ***FAT and NTFS filesystems are unsuitable for use as /home*** because they *don't preserve proper *nix permissions*. As far as I know, if you want to mount a separate partition as /home, it needs to be an ext3 formatted filesystem. 

So, for your purposes, having a separate /home partition is unnecessary, because ext3 isn't accessible under Windows anyway! Personally, I have a FAT32 data partition which I mount as /docs, and I put a link to that within /home/username.

> **nextbgates95 said:**
> I used testdisk (in Windows) to recover that partiton, but now, GRUB won't boot, and is giving me error 17.  I tried reinstall GRUB using the console, but that wasn't working.

Right, so you recovered the partition you wanted to mount as /home, right? And windows hasn't killed the actual Ubuntu partition? Only reason I ask is...

**Error 17** claims that the partition that you're attempting to boot is of a format that GRUB does not recognize. The GRUB documentation classes it as:

[B]17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. [/B]

> **nextbgates95 said:**
> I thought I would try and reinstall Ubuntu, but Gparted shows my entire drive as unallocated.

Nice. Sounds to me like TestDisk (read: *windows* :P) has really screwed things up. Where are you running GParted from? I assume the Ubuntu LiveCD?

> **nextbgates95 said:**
> I cannot download test disk to Ubuntu, I am on a different computer, which only has 56/k.  It says the archive is corrupted, becuase it ends unexpectedly.

Suggestions?

Well, if you can't boot into Ubuntu to install it, there's not much point getting TestDisk, right?

It's definitely a partition problem, but we need more information than this! 

Open a terminal window (Applications -> Accessories -> Terminal) when you're booted into the Ubuntu LiveCD, and type:

```
sudo fdisk -l
```

Could you copy that information and post it here, please?

---

