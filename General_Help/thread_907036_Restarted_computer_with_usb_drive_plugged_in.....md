---
title: "Restarted computer with usb drive plugged in...."
date: 2008-09-01
forum: General Help
---

### Post by LugNut71 on 2008-09-01
...and I can no longer mount it, it is Maxtor 1 touch 120GB with a reiserfs on it, it has all my backup data on it that I can longer access, and this is a fresh install of 8.04, so any help would be highly appreciated. Thank you in advance. Below is the last half of my /var/log/messages that shows it, if any more info is required, please let me know.



Aug 31 23:11:35 DSpark kernel: [  127.204531] ReiserFS: sda1: found reiserfs format "3.6" with standard journal
Aug 31 23:11:35 DSpark kernel: [  127.204569] ReiserFS: sda1: using ordered data mode
Aug 31 23:11:35 DSpark kernel: [  127.361194] ReiserFS: sda1: journal params: device sda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
Aug 31 23:11:35 DSpark kernel: [  127.362627] ReiserFS: sda1: checking transaction log (sda1)
Aug 31 23:11:41 DSpark kernel: [  132.566019] ReiserFS: sda1: Using r5 hash to sort names
Aug 31 23:11:41 DSpark kernel: [  132.566041] ReiserFS: sda1: warning: xattrs/ACLs enabled and couldn't find/create .reiserfs_priv. Failing mount.
Aug 31 23:11:54 DSpark kernel: [  145.826033] ReiserFS: sda1: found reiserfs format "3.6" with standard journal
Aug 31 23:11:54 DSpark kernel: [  145.826074] ReiserFS: sda1: using ordered data mode
Aug 31 23:11:54 DSpark kernel: [  145.839025] ReiserFS: sda1: journal params: device sda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
Aug 31 23:11:54 DSpark kernel: [  145.840491] ReiserFS: sda1: checking transaction log (sda1)
Aug 31 23:11:57 DSpark kernel: [  149.407682] ReiserFS: sda1: Using r5 hash to sort names
Aug 31 23:11:57 DSpark kernel: [  149.407704] ReiserFS: sda1: warning: xattrs/ACLs enabled and couldn't find/create .reiserfs_priv. Failing mount.

I did run reiserfsck and it exits with a nearly exact mumble and as above. I have been using reiserfs for about 2.5 years, never had a hitch, it is a great file system, I am unsure as to if this is ubuntu bug or a reiser bug. I will be sure to let all know when I find out though.

---

### Post by LugNut71 on 2008-09-01
I finally did figure this one out, my brainfreeze, My filesystem did get corrupted when I restarted without unmounting it. When I ran reiserfsck the first time I mistyped Yes for yes when reiserfsck asks you if want to check it. It is a case sensitive question.

I repaired this problem by typing:

sudo reiserfsck --check /dev/sda1
Yes
sudo reiserfsck --rebuild-tree /dev/sda1
Yes

It then went into this multi-hour rebuild process that finally ended in my being able to access my data again. Never again will I EVER restart my computer with mounted media again. The funny thing is I never had done this in the past, this one time, I did not unmount, it nearly bit me. Just a suggestion to others, if you ever are told to do something specifically, make sure you do it exactly as prescribed. Thanks very much to all of you have read this post, and thought about it even a little.

---

