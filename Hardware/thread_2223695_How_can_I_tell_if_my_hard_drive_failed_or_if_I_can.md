---
title: "How can I tell if my hard drive failed or if I can fix my disk with fsck?"
date: 2014-05-12
forum: Hardware
---

### Post by stupidusernamerestriction on 2014-05-12
So something went wrong with my 12.04 system when I was running Spotify. My system went into read-only mode. Obviously there's some problem, but I can't tell what is the underlying cause for it. Here is an output of dmesg with hopefully the relevant parts: 

[526855.795744] EXT4-fs error (device sda1): ext4_mb_generate_buddy:742: group 113, 6926 clusters in bitmap, 6927 in gd
[526855.795758] Aborting journal on device sda1-8.
[526855.795963] EXT4-fs (sda1): Remounting filesystem read-only
[526855.796065] EXT4-fs error (device sda1) in ext4_free_blocks:4737: Journal has aborted
[526855.796328] EXT4-fs (sda1): ext4_da_writepages: jbd2_start: 997 pages, ino 917796; err -30
[526862.869586] init: anacron main process (13942) terminated with status 1

Can I tell from this if I need a new harddrive? 

Since it's finals week, I kind of need my computer. Would it be possible for me to move my important files to a usb, and then try remounting the disk?

---

### Post by Bashing-om on 2014-05-12
stupidusernamerestriction; Hi ! Welcome to the forum .

Wow, what a nick name ! .. 

To the issue at hand, the indication is that there is a file system issue on device sda1.
See what results:
Boot the liveDVD:
#From liveCD so everything is unmounted, swap off if necessary  - check from the GParted utility.
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
```

sudo e2fsck -C0 -p -f -v /dev/sda1

```
#if errors: -y auto answers yes for fixes needing response; your attention is invited to the manual; terminal code:
```

man e2fsck

```
```

sudo e2fsck -f -y -v /dev/sda1

```

If 'e2fsck' repairs the file system, or says it is clean; then ->
Boot into the install and see what the condition the package manager is in:
```

sudo apt-get update
sudo apt-get upgrade

```

Perhaps all now is good, depending on these results is what we do next.

[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

