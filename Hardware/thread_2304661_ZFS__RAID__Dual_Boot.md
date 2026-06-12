---
title: "ZFS / RAID / Dual Boot"
date: 2015-11-28
forum: Hardware
---

### Post by HuaiDan on 2015-11-28
( Ubuntu 15.04  x86_64,  openSUSE 13.2)
Hello all,
Is anyone here an expert on ZFS? I've been experimenting with it, as I want to take advantage of its scalability and reliability.
So far, I've been pretty successful. I've managed to build a zpool on a mdadm RAID1 array (/dev/md0) over 2 3TB hdd's (/dev/sdc and /dev/sdd) . Nothing too difficult there.

I've  been using SUSE for  some time now.   Ubuntu hasn't worked for me  on my combination of hardware since 13,  until now.  sda3 is my system partition for openSUSE, and sda4 is my system partition for Ubuntu, on a dual-boot system. I do not want to use the zpool as a system partition, but only as a backup/storage device for both Ubuntu and openSUSE.

What I though I could do was build the zpool in Ubuntu,   reboot into SUSE,  build the zpool there and mount it, and just use the zpool whenever I booted into either OS. However, after I created the zpool in SUSE, put some test data on it, and rebooted back into  Ubuntu, not only was the test data gone, but the zpool was missing as well.

I tried a bit with the zfs import and export option, but I haven't been too successful with that yet, and it seems a bit brutish to do what I want to do. Is there a way to preserve a zpool across two systems over a reboot?

---

### Post by lukeiamyourfather on 2015-12-08
> **HuaiDan said:**
> I've managed to build a zpool on a mdadm RAID1 array (/dev/md0) over 2 3TB hdd's (/dev/sdc and /dev/sdd) . Nothing too difficult there.

ZFS is both a file system and a volume manager so there's no need to use mdadm for anything, do the mirroring with ZFS otherwise you're missing most of the benefits of ZFS.

> **HuaiDan said:**
> 
What I though I could do was build the zpool in Ubuntu,   reboot into SUSE,  build the zpool there and mount it, and just use the zpool whenever I booted into either OS. However, after I created the zpool in SUSE, put some test data on it, and rebooted back into  Ubuntu, not only was the test data gone, but the zpool was missing as well.

ZFS pools typically are used by only one host. There's a unique host ID that ZFS looks for when starting. If the unique host ID doesn't match what the pool has then ZFS won't mount it because it's assumed to be foreign. You'll need to either set the host ID the same for each operating system so ZFS doesn't think the pool is foreign or you'll need to force ZFS to mount the pool regardless of the host ID matching or not.

> **HuaiDan said:**
> I tried a bit with the zfs import and export option, but I haven't been too successful with that yet, and it seems a bit brutish to do what I want to do.

Can you post output of what you're getting? Does it give errors or something? Also don't use ZFS unless you have ECC memory (unrelated to your post but just throwing it out there).

---

