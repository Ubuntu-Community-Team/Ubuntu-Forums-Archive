---
title: "Mounting LVM devices"
date: 2008-08-28
forum: General Help
---

### Post by compu73rg33k on 2008-08-28
First let me explain my set up. I have 1 encrypted partition that is then managed with LVM. The volume group name is ubuntu and then I have 4 logical volumes - root, usr, home, swap. 

Mysteriously one day that I started my laptop, and although it could open the device (with luksOpen) the LVM failed to start. It said "trying to find root partition" and then after a while gave me this message:

I booted from CD and unlocked the encryption. Then I ran vgchange -ay which told me that "4 logical volume(s) in volume group ubuntu now active"

I tried to mount a volume with mount /dev/ubuntu/home /mnt/ubuntu/home but it told me I "must specify the filesystem type" Never a good sign *sigh*

So I tried again, this time specifying [HTML]ext3 mount -t ext3 /dev/ubuntu/home /mnt/ubuntu/home[/HTML] and it gave me the infamous message: ```
mount: wrong fs type, bad option, bad superblock on /dev/mapper/ubuntu-root missing codepage or helper program or other error - try dmesg|tail or so
```

So I did. The only thing it gave was ```
683.587529 VFS: Can't find ext3 filesystem on dev dm-4.
713.235983 VFS: Can't find ext3 filesystem on dev dm-1.
```

So I'm expecting the worst thinking there's a corrupted block somewhere. I guess this would be the unfortunate downfall of putting the whole install on one partition :\ The shitty part was I was planning on doing a backup and reinstall THE NEXT DAY. I have some really valuable information that I need to get some files off this hard drive!

I had an experience before where there was a bad block on a (Maxtor) hard drive. This hard drive is Samsung from a notebook only 1 year old, so I don't think it's a hardware problem per se, probably just a corrupted block? Would I be able to at least copy the drive image with dd and then maybe access it, after rebuilding the file system? That's what allowed me to access my data before when I had a bad block with the Maxtor. If so, if someone could help me out with commands on rebuilding the ext3 file system, I'd really appreciate it.

I have Windows on another partition, and it boots up fine.

---

### Post by iaculallad on 2008-08-28
You could try reading this [page]("http://www.linux-sxs.org/storage/fedora2ubuntu.html") on Fedora LVM mounting.

---

### Post by compu73rg33k on 2008-08-28
> **iaculallad said:**
> You could try reading this [page]("http://www.linux-sxs.org/storage/fedora2ubuntu.html") on Fedora LVM mounting.

Did you even read my post? I tried the things listed there, the problem is the volumes won't mount (giving the wrong fs type message). I guess I should have titled the post better. Can anyone else help me or give their opinion on my situation?


Problem solved. I ran ```
fsck -t ext3 -a /dev/ubuntu/home
``` and it fixed it!

---

