---
title: "Hard Drive Failure"
date: 2008-05-27
forum: Hardware
---

### Post by deleonjavier on 2008-05-27
So my Ubuntu 8.04 lts server has been working pretty good for several weeks, I have a ide 100 gb as my master and a 400 gb as my master for file storage. I use the 400 for mainly music and video storage. The 400 gb is a sata drive and is mounted on as /storage on the 100 gb. Everything had been working fine until suddenly I wasn't able to access the folder from samba or from the computer itself. It was hanging up completely. When unmounted it and tried to access it from the computer:/// screen it would give me this error 

"Cannot Mount Drive"
error org.freedesktop.DBus.Error.AccessDenied.

I've tried putting it through fsck with different parameters. it keeps showing certain outputs like

error reading block ###### (attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. ignore error?



This shows up multiple times I type yes. then it contines to a screen  
"Checking for bad blocks (read only test):



What do I do? is it hopeless?

---

### Post by deleonjavier on 2008-05-28
So I ran ubuntu livecd and ran the fsck disk from gparted and got the following as the details. 

```

Check and repair filesystem (ext3) on /dev/sdb1  08:12:17    ( ERROR )
     	
calibrate /dev/sdb1  00:00    ( SUCCES )
     	
path: /dev/sdb1
start: 63
end: 781417664
size: 781417602 (372.61 GiB)
check filesystem on /dev/sdb1 for errors and (if possible) fix them  08:12:16    ( SUCCES )
     	
e2fsck -f -y -v /dev/sdb1
     	
Pass 1: Checking inodes, blocks, and sizes
Group 2's block bitmap (65536) is bad. Relocate? yes

Group 2's inode bitmap (65537) is bad. Relocate? yes

Programming error? block #99320 claimed for no reason in process_bad_block.
Group 3's block bitmap (99353) is bad. Relocate? yes

Group 3's inode bitmap (99354) is bad. Relocate? yes

Group 11's block bitmap (360448) is bad. Relocate? yes

Group 11's inode bitmap (360449) is bad. Relocate? yes

Group 21's block bitmap (688128) is bad. Relocate? yes

Group 21's inode bitmap (688129) is bad. Relocate? yes

Group 29's block bitmap (950272) is bad. Relocate? yes

Group 29's inode bitmap (950273) is bad. Relocate? yes

Group 37's block bitmap (1212416) is bad. Relocate? yes

Group 37's inode bitmap (1212417) is bad. Relocate? yes

Group 45's block bitmap (1474560) is bad. Relocate? yes

Group 45's inode bitmap (1474561) is bad. Relocate? yes

Group 46's block bitmap (1507328) is bad. Relocate? yes

Group 46's inode bitmap (1507329) is bad. Relocate? yes

Group 54's block bitmap (1769472) is bad. Relocate? yes

Group 54's inode bitmap (1769473) is bad. Relocate? yes

Group 62's block bitmap (2031616) is bad. Relocate? yes

Group 62's inode bitmap (2031617) is bad. Relocate? yes

Group 70's block bitmap (2293760) is bad. Relocate? yes

Group 70's inode bitmap (2293761) is bad. Relocate? yes

Group 79's block bitmap (2588672) is bad. Relocate? yes

Group 79's inode bitmap (2588673) is bad. Relocate? yes

Group 87's block bitmap (2850816) is bad. Relocate? yes

Group 87's inode bitmap (2850817) is bad. Relocate? yes

Group 95's block bitmap (3112960) is bad. Relocate? yes

Group 95's inode bitmap (3112961) is bad. Relocate? yes

Group 103's block bitmap (3375104) is bad. Relocate? yes

Group 103's inode bitmap (3375105) is bad. Relocate? yes

Group 111's block bitmap (3637248) is bad. Relocate? yes

Group 111's inode bitmap (3637249) is bad. Relocate? yes

Group 120's block bitmap (3932160) is bad. Relocate? yes

Group 120's inode bitmap (3932161) is bad. Relocate? yes

Group 128's block bitmap (4194304) is bad. Relocate? yes

Group 128's inode bitmap (4194305) is bad. Relocate? yes

Group 751's block bitmap (24609282) is bad. Relocate? yes

Group 1758's block bitmap (57606144) is bad. Relocate? yes

Group 2512's block bitmap (82313216) is bad. Relocate? yes

Group 2528's block bitmap (82837504) is bad. Relocate? yes

Error reading block 95387650 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 95387651 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 95387652 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 95387653 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 95387654 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 95387655 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 95387656 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 95387657 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error? yes

Force rewrite? yes

Error reading block 97241615 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 48480361. Ignore error? yes

Force rewrite? yes

Error reading block 97219656 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 48480383. Ignore error? yes

Force rewrite? yes

Error reading block 97241616 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 48480389. Ignore error? yes

Force rewrite? yes

Error reading block 97196968 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 48480332. Ignore error? yes

Force rewrite? yes

Error reading block 97108958 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 48480332. Ignore error? yes

Force rewrite? yes

Error reading block 97043018 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 48480332. Ignore error? yes

Force rewrite? yes

Error reading block 97263297 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 48480392. Ignore error? yes

Force rewrite? yes

Error reading block 97218448 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 48480395. Ignore error? yes

Force rewrite? yes

Error reading block 97174092 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 48480395. Ignore error? yes

Force rewrite? yes

Error reading block 97174406 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 48480395. Ignore error? yes

Force rewrite? yes

Error reading block 97241767 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 48480395. Ignore error? yes

Force rewrite? yes

Error reading block 97307557 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 48480393. Ignore error? yes

Force rewrite? yes

Error reading block 97307688 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 48480393. Ignore error? yes

Force rewrite? yes

Error reading block 97329863 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 48480393. Ignore error? yes

Force rewrite? yes

Error reading block 97174320 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 48480394. Ignore error? yes

Force rewrite? yes

Error reading block 97219984 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 48480394. Ignore error? yes

Force rewrite? yes

Error reading block 97264264 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 48480394. Ignore error? yes

Force rewrite? yes

Relocating group 2's block bitmap from 65536 to 66050...
Error reading block 65536 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 2's inode bitmap from 65537 to 66051...
Error reading block 65537 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 3's block bitmap from 99353 to 99867...
Error reading block 99353 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 3's inode bitmap from 99354 to 99868...
Error reading block 99354 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 11's block bitmap from 360448 to 360962...
Error reading block 360448 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 11's inode bitmap from 360449 to 360963...
Error reading block 360449 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 21's block bitmap from 688128 to 688642...
Error reading block 688128 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 21's inode bitmap from 688129 to 688643...
Error reading block 688129 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 29's block bitmap from 950272 to 950786...
Error reading block 950272 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 29's inode bitmap from 950273 to 950787...
Error reading block 950273 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 37's block bitmap from 1212416 to 1212930...
Error reading block 1212416 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 37's inode bitmap from 1212417 to 1212931...
Error reading block 1212417 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 45's block bitmap from 1474560 to 1475074...
Error reading block 1474560 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 45's inode bitmap from 1474561 to 1475075...
Error reading block 1474561 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 46's block bitmap from 1507328 to 1507842...
Error reading block 1507328 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 46's inode bitmap from 1507329 to 1507843...
Error reading block 1507329 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 54's block bitmap from 1769472 to 1769986...
Error reading block 1769472 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 54's inode bitmap from 1769473 to 1769987...
Error reading block 1769473 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 62's block bitmap from 2031616 to 2032130...
Error reading block 2031616 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 62's inode bitmap from 2031617 to 2032131...
Error reading block 2031617 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 70's block bitmap from 2293760 to 2294274...
Error reading block 2293760 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 70's inode bitmap from 2293761 to 2294275...
Error reading block 2293761 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 79's block bitmap from 2588672 to 2589186...
Error reading block 2588672 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 79's inode bitmap from 2588673 to 2589187...
Error reading block 2588673 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 87's block bitmap from 2850816 to 2851330...
Error reading block 2850816 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 87's inode bitmap from 2850817 to 2851331...
Error reading block 2850817 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 95's block bitmap from 3112960 to 3113474...
Error reading block 3112960 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 95's inode bitmap from 3112961 to 3113475...
Error reading block 3112961 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 103's block bitmap from 3375104 to 3375618...
Error reading block 3375104 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 103's inode bitmap from 3375105 to 3375619...
Error reading block 3375105 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 111's block bitmap from 3637248 to 3637762...
Error reading block 3637248 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 111's inode bitmap from 3637249 to 3637763...
Error reading block 3637249 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 120's block bitmap from 3932160 to 3932674...
Error reading block 3932160 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 120's inode bitmap from 3932161 to 3932675...
Error reading block 3932161 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 128's block bitmap from 4194304 to 4194818...
Error reading block 4194304 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 128's inode bitmap from 4194305 to 4194819...
Error reading block 4194305 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 751's block bitmap from 24609282 to 24608768...
Error reading block 24609282 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Relocating group 1758's block bitmap from 57606144 to 57606658...
Relocating group 2512's block bitmap from 82313216 to 82323861...
Relocating group 2528's block bitmap from 82837504 to 82847400...

Running additional passes to resolve blocks claimed by more than one inode...
Pass 1B: Rescanning for multiply-claimed blocks
Multiply-claimed block(s) in inode 31670359: 90557760 90557820 90558072 90558085 90579456 90579464 90581056
Multiply-claimed block(s) in inode 31670361: 90941432 90941440 90941688 90941705 90941876 90942000 90942047 90942217 90942388 90942640 90942653 90942824 90942944 90942994 90943120 90943165 90943335 90943576 90943601 90943771 90943942 90944072 90944112 90965352 90965415 90965586 90965712 90965756 90966136 90966192 90966312 90966363 90966533 90966704 90966824 90966875 90989840 90989902 90991760 90991797
Multiply-claimed block(s) in inode 31670362: 91013744 91013783 91013953 91014520 91014560 91014680 91014730 91014856 91014901 91015071 91015242 91015496 91015507 91015678 91016000 91016019 91016190 91016448 91016455 91016625 91038056 91038099 91038269 91038440 91038560 91038611 91038781 91039032 91039046 91039176 91039217 91039388 91039704 91039729 91039976 91039994 91040120 91040165 91040335 91040506 91040632 91040677 91040928 91040942 91062128 91062150 91062888 91062927 91063098 91063224 91063268 91063392 91063439 91063680 91063704 91063824 91063875 91064045 91064216 91064336
Error reading block 95387650 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 95387651 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 95387652 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 95387653 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 95387654 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 95387655 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 95387656 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 95387657 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 97196968 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 97108958 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 97043018 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 97241615 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 97219656 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 97241616 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 97263297 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 97307557 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 97307688 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 97329863 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 97174320 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 97219984 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 97264264 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 97218448 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 97174092 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 97174406 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 97241767 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Pass 1C: Scanning directories for inodes with multiply-claimed blocks
Pass 1D: Reconciling multiply-claimed blocks
Error reading block 66050 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 66051 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 99867 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 99868 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 360962 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 360963 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 688642 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 688643 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 950786 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 950787 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 1212930 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 1212931 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 1507842 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 1507843 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 1769986 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 1769987 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 2032130 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 2032131 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 2294274 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 2294275 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 2589186 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 2589187 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 2851330 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 2851331 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 3113474 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 3113475 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 3375618 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 3375619 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 3637762 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 3637763 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 3932674 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 3932675 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 4194818 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 4194819 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 24608768 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

Error reading block 57606658 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps. Ignore error? yes

Force rewrite? yes

(There are 3 inodes containing multiply-claimed blocks.)

File /Movies/House.avi (inode #31670359, mod time Mon Apr 21 01:06:31 2008)
has 7 multiply-claimed block(s), shared with 1 file(s):
<The bad blocks inode> (inode #1, mod time Tue May 27 08:00:26 2008)
Clone multiply-claimed blocks? yes

Error reading block 90557820 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90558085 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90579464 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

File /Movies/Inside Man.avi (inode #31670361, mod time Mon Apr 21 01:08:01 2008)
has 40 multiply-claimed block(s), shared with 1 file(s):
<The bad blocks inode> (inode #1, mod time Tue May 27 08:00:26 2008)
Clone multiply-claimed blocks? yes

Error reading block 90941440 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90941705 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90941876 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90942047 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90942217 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90942388 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90942653 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90942824 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90942994 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90943165 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90943335 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90943601 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90943771 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90943942 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90944112 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90965415 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90965586 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90965756 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90966192 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90966363 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90966533 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90966704 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90966875 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90989902 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 90991797 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

File /Movies/I Think I Love My Wife.avi (inode #31670362, mod time Mon Apr 21 01:09:15 2008)
has 60 multiply-claimed block(s), shared with 1 file(s):
<The bad blocks inode> (inode #1, mod time Tue May 27 08:00:26 2008)
Clone multiply-claimed blocks? yes

Error reading block 91014560 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91014901 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91015071 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91015678 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91016019 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91016190 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91016455 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91038269 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91038611 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91038781 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91039046 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91039217 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91039388 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91039729 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91039994 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91040165 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91040335 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91040677 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91040942 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91062150 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91062927 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91063098 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91063268 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91063439 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91063704 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91063875 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91064045 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Error reading block 91064216 (Attempt to read block from filesystem resulted in short read). Ignore error? yes

Force rewrite? yes

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Inode 31670273 ref count is 22, should be 19. Fix? yes

Pass 5: Checking group summary information
Block bitmap differences: +(65536--66051) +(98304--99868) +360408 +(360448--360963) +688120 +(688128--688643) +950264 +(950272--950787) +1212408 +(1212416--1212931) +1474552 +(1474560--1475075) +1507320 +(1507328--1507843) +1769464 +(1769472--1769987) +2031608 +(2031616--2032131) +(2062336--2062826) +(2062835--2062837) +(2062853--2062855) +2293752 +(2293760--2294275) +2588664 +(2588672--2589187) +2850808 +(2850816--2851331) +3112952 +(3112960--3113475) +3375096 +(3375104--3375619) +3637240 +(3637248--3637763) +3932152 +(3932160--3932675) +4194296 +(4194304--4194819) +24608760 +(24608768--24609282) -(24642050--24655871) -(24656189--24656378) -(24656410--24656437) -(24656443--24657009) -(24657016--24657026) -(24657032--24657285) -(24657288--24657347) -(24657352--24658115) -(24658120--24658176) -(24658184--24658241) -(24658248--24658354) -(24658360--24658433) -(24658436--24658495) -(24658500--24659483) -(24659503--24662086) -(24662088--24662094) -(24662096--24662165) -(24662168--24662170) -(24662176--24662179) -(24662184--24662187) -(24662192--24662193) -(24662209--24662849) -(24662856--24662975) -(24662987--24664759) -(24664810--24674139) -(24674144--24674177) -(24674180--24674280) -(24674285--24674299) -(24674818--24675745) -(24675748--24677675) -(24677680--24677691) -(24677696--24677698) -(24677704--24677706) -(24677716--24677761) -(24677766--24677771) -(24677776--24677779) -(24677784--24677787) -(24677792--24677795) -(24677800--24677803) -(24677808--24677810) -(24677820--24677826) -(24677832--24677835) -(24677837--24677868) -(24677872--24678918) -(24678920--24678923) -(24678928--24678958) -(24678960--24678962) -(24678968--24678970) -(24678979--24678990) -(24678992--24679044) -(24679048--24679051) -(24679056--24679059) -(24679062--24679722) -(24679728--24679730) -(24679736--24679746) -(24679752--24679755) -(24679764--24679776) -(24679778--24681378) -(24681417--24681421) -(24681425--24681459) -(24681488--24681515) -(24681539--24681611) -(24681614--24681637) -(24681640--24681665) -(24681670--24681707) -(24681712--24681714) -(24681720--24681724) -(24681728--24681730) -(24681736--24681738) -(24681744--24681746) -(24681751--24681763) -(24681768--24681770) -(24681776--24681779) -(24681784--24681790) -(24681792--24681795) -(24681800--24681802) -(24681812--24681818) -(24681824--24681826) -(24681832--24681834) -(24681840--24681843) -(24681870--24681878) -(24681885--24681995) -(24682002--24682038) -(24682044--24691634) -(24691660--24693052) -(24693069--24693228) -(24693232--24693234) -(24693237--24695146) -(24695148--24696322) -(24696328--24696357) -(24696360--24696362) -(24696368--24696370) -(24696376--24696431) -(24696465--24696844) -(24696846--24698633) -(24698643--24698665) -(24698668--24698990) -(24698995--24699271) -(24699275--24699278) -(24699280--24699286) -(24699288--24699315) -(24699373--24700035) -(24700040--24700097) -(24700104--24700106) -(24700112--24700508) -(24700512--24700515) -(24700520--24700522) -(24700528--24700530) -(24700536--24700542) -(24700544--24700546) -(24700552--24700556) -(24700564--24700604) -(24700608--24700619) -(24700627--24700690) -(24700751--24701187) -(24701192--24701194) -(24701200--24701245) -(24701264--24701966) -(24701968--24702478) -(24702480--24702805) -(24702808--24702810) -(24702816--24702818) -(24702824--24702827) -(24702832--24702834) -(24702840--24702842) -(24702848--24702850) -(24702856--24702858) -(24702864--24702866) -(24702872--24702883) -(24702888--24702890) -(24702896--24702907) -(24702912--24702915) -(24702920--24702930) -(24702936--24702938) -(24702944--24702947) -(24702952--24702954) -(24702960--24702962) -(24702968--24702970) -(24702976--24702978) -(24702984--24702990) -(24702992--24703003) -(24703008--24703019) -(24703024--24703027) -(24703032--24703034) -(24703040--24703042) -(24703048--24703050) -(24703056--24703058) -(24703064--24703066) -(24703072--24703074) -(24703080--24703082) -(24703088--24703090) -(24703096--24703106) -(24703112--24703122) -(24703128--24703130) -(24703133--24703142) -(24703144--24703146) -(24703152--24703154) -(24703160--24703163) -(24703168--24703172) -(24703176--24703189) -(24703192--24703194) -(24703269--24703272) -(24703385--24703391) -(24703525--24703553) -(24703560--24703562) -(24703568--24703570) -(24703576--24703587) -(24703592--24703594) -(24703600--24703603) -(24703608--24703611) -(24703618--24703820) -(24703897--24704040) -(24704063--24704070) -(24704095--24704097) -(24704123--24704130) -(24704136--24704173) -(24704203--24704205) -(24704409--24704451) -(24704484--24704491) -(24704498--24704504) -(24704549--24704551) -(24704665--24704671) -(24704702--24704725) -24704728 -(24704815--24704821) -(24704921--24704936) -(24704941--24704947) -(24704972--24704974) -(24704996--24704998) -(24705010--24705020) -(24705433--24705462) -(24705508--24705511) -(24705522--24705524) -(24705742--24705744) -(24705949--24705951) -(24706034--24706040) -(24706457--24706460) -(24706532--24706534) -(24707592--24707594) +(57606144--57606658) -(57639426--57671679) -(57672194--57704447) -(57704962--57715770) -(57715776--57715779) -(57715784--57715787) -(57715792--57715795) -(57715800--57715802) -(57715808--57715810) -(57715819--57715842) -(57715848--57715850) -(57715856--57715882) -(57715888--57715891) -(57715894--57716716) -(57716720--57716722) -(57716728--57716730) -(57716736--57716738) -(57716744--57716746) -(57716752--57716754) -(57716760--57716762) -(57716768--57716770) -(57716776--57716778) -(57716784--57716786) -(57716792--57716794) -(57716800--57716802) -(57716808--57716810) -(57716816--57716818) -(57716918--57717762) -(57718037--57718060) -(57718083--57718088) -(57718118--57718120) -(57718170--57718172) -(57718245--57718253) -(82323862--82345983) -(82346504--82378751) -(82379272--82411519) -(82412040--82444287) -(82444808--82456763) -(82847401--82870271) -(82870786--82903039) -(82903554--82935807) -(82936322--82968575) -(82969090--83001343) -(83001858--83034111) -(83034626--83066879) -(83067394--83099647) -(83100162--83132415) -(83132930--83165183) -(83165698--83197951) -(83198466--83230719) -(83231234--83263487) -(83264002--83296255) -(83296770--83329023) -(83329538--83361791) -(83362306--83394559) -(83395074--83427327) -(83427842--83460095) -(83460610--83492863) -(83493378--83525631) -(83526146--83558399) -(83558914--83591167) -(83591688--83623935) -(83624456--83656703) -(83657224--83667980) -(95403717--95403719) -(95403724--95403729) -(95412224--95420415) -(95420930--95453183) -(95453698--95485951) -(95486466--95491210) -(95491216--95491218) -(95491224--95491511) -(95491660--95492999) -(95493452--95495555) -(95495560--95495563) -(95495568--95495570) -(95495576--95495608) -(95495616--95495895) -(95496021--95496068) -(95496072--95496129) -(95496136--95496138) -(95496144--95496374) -(95496376--95496438) -(95496440--95496448) -(95496456--95496462) -(95496464--95496510) -(95496512--95496637) -(95496640--95497023) -(95497045--95498691) -(95498696--95499335) -(95499349--95499392) -(95499400--95499421) -(95499424--95499426) -(95499432--95499478) -(95499480--95499614) -(95499616--95499678) -(95499680--95500199) -(95500373--95502869) -(95502872--95503367) -(95503451--95503654) -(95503656--95503746) -(95503752--95503786) -(95503792--95503854) -(95503856--95503918) -(95503920--95503930) -(95503936--95503983) -(95504475--95505743) -(95505755--95505919) -(95506011--95506167) -(95506267--95506375) -(95506779--95506903) -(95507803--95507999) -(95508827--95508903) -(95509339--95509431) -(95509851--95509983) -(95510875--95510955) -(95510960--95511009) -(95511016--95511078) -(95511080--95511098) -(95511104--95511151) -(95511387--95511535) -(95511899--95512055) -(95512411--95512631) -(95512923--95512991) -(95513947--95514095) -(95514459--95514559) -(95514971--95515047) -(95515227--95515239) -(95515739--95515741) -(95584770--95584775) -(95590036--95592447) -(95592480--95596543) -(95596552--95617023) -(95617544--95649791) -(95650312--95679855) -(97043019--97043024) -(97072633--97072648) -(97073373--97073375) -(97073389--97073404) -(97075486--97075508) -(97108959--97109002) -(97110904--97110923) -(97174093--97174156) -(97174321--97174354) -(97174407--97174470) -(97196969--97197019) -(97207768--97207780) -(97210564--97210578) -(97218449--97218479) -(97218504--97218511) -(97219657--97219662) -(97219691--97219712) -(97219720--97219723) -(97219985--97220008) -(97224099--97224123) -(97227616--97227631) -97227743 -(97227944--97227998) -(97235136--97235151) -(97235164--97235188) -97237055 -(97237064--97237086) -(97238913--97238914) -(97238922--97238927) -(97241235--97241282) -(97241287--97241294) -(97241299--97241307) -(97241476--97241486) -(97241617--97241631) -(97241646--97241647) -(97241773--97241775) -(97241780--97241783) -(97243681--97243689) -(97243811--97243836) -(97247096--97247105) -(97247150--97247151) -(97247208--97247271) -(97250364--97250368) -(97250437--97250567) -(97251080--97251097) -(97253922--97253925) -(97253934--97253935) -(97253939--97253943) -97253947 -(97257543--97257599) -(97257690--97257692) -(97259590--97259591) -(97259716--97259719) -(97259777--97259783) -(97259787--97259791) -(97259796--97259799) -(97259803--97259804) -(97260567--97260569) -(97262596--97262599) -(97262601--97262607) -(97262872--97262882) -(97263214--97263218) -(97263223--97263226) -(97263283--97263296) -(97263298--97263303) -(97263305--97263320) -(97263384--97263388) -(97263640--97263642) -(97264265--97264329) -(97267151--97267155) -(97267919--97267922) -(97273689--97273693) -(97274096--97274160) -97274975 -(97275011--97275015) -(97275140--97275143) -(97275833--97275836) -(97275912--97275954) -(97275959--97275980) -(97276061--97276112) -(97276596--97276599) -(97278910--97278925) -(97278963--97278970) -(97280750--97280753) -(97280776--97280791) -(97284020--97284025) -(97284040--97284097) -(97284597--97284600) -(97284712--97284740) -(97284931--97284935) -(97285000--97285043) -(97292375--97292397) -(97292910--97292930) -(97297255--97297263) -(97300726--97300727) -(97300738--97300743) -(97300749--97300751) -(97300755--97300758) -(97302597--97302599) -(97302605--97302607) -(97302611--97302615) -(97302619--97302623) -(97302628--97302631) -(97302636--97302639) -(97302644--97302647) -97302655 -(97302660--97302663) -(97302668--97302671) -(97302675--97302679) -(97302683--97302687) -(97302691--97302695) -(97302700--97302703) -(97306486--97306558) -(97307558--97307615) -(97307689--97307753) -(97307760--97307767) -(97307984--97308047) -(97308899--97308903) -(97308907--97308911) -(97308915--97308919) -(97308921--97308937) -(97310643--97310646) -97310943 -(97310947--97310951) -(97310957--97310959) -(97310963--97310966) -97313919 -(97313928--97313963) -(97313977--97314004) -(97314896--97314946) -(97316512--97316575) -(97317792--97317803) -(97317872--97317879) -(97317886--97317929) -(97318264--97318303) -(97320473--97320479) -(97320672--97320728) -(97320870--97320871) -(97321491--97321523) -(97321729--97321735) -(97321795--97321799) -(97321977--97321983) -(97322100--97322103) -(97323451--97323470) -(97323810--97323833) -(97323880--97323882) -(97323888--97323891) -(97323896--97323909) -(97324166--97324169) -(97324320--97324384) -(97324841--97324847) -(97324852--97324872) -(97324939--97324942) -(97325062--97325065) -(97325552--97325563) -(97325936--97325957) -(97326024--97326028) -(97326470--97326493) -(97326509--97326513) -(97326667--97326671) -(97326681--97326684) -(97326800--97326811) -(97328138--97328161) -(97328262--97328325) -(97329173--97329175) -(97329264--97329273) -(97329399--97329417) -(97329929--97329935) -(97330001--97330071) -(97330584--97330611) -(97332361--97332402) -(97332472--97332535) -(97333129--97333132) -(97333769--97333819) -(97334016--97334080) -(97334275--97334280) -(97334327--97334353) -(97334730--97334735) -(97334804--97334807) -(97334873--97334879) -(97335320--97335384) -(97336600--97336663) -(97336824--97336928) -(97337185--97337214) -(97337298--97337312) -(97337390--97337410) -(97337509--97337556) -(97338682--97338729) -(97338912--97338976) -(97339208--97339223) -(97339227--97339240) -(97340416--97340424) -(97340478--97340542) -(97340701--97340722) -(97341640--97341656) -(97342195--97342263) -(97342521--97342527) -(97342664--97342670) -(97343535--97343536) -(97343541--97343557) -97343744 -97343935 -(97344030--97344033) -(97344040--97344054) -(97344189--97344196) -(97344838--97344849) -(97344966--97344969) -(97345253--97345316) -(97345494--97345557) -(97345949--97345951) -(97345995--97345996) -(97346064--97346076) -(97346080--97346112) -(97346184--97346247) -(97346630--97346639) -(97346705--97346711) -97346757 -(97346792--97346821) -(97347032--97347092) -(97347666--97347670) -(97347819--97347856) -(97348422--97348433) -(97348685--97348748) -(97349408--97349471) -(97349642--97349679) -(97349697--97349704) -(97351344--97351356) -(97351587--97351591) -(97351648--97351665) -(97351688--97351695) -(97351769--97351784) -97351793 -(97351830--97351831) -(97351848--97351879) -(97351935--97351999) -(97352022--97352023) -97352049 -(97352734--97352738) -(97352745--97352792) -(97352864--97352870) -(97353561--97353592) -(97353635--97353666) -(97354641--97354653) -(97355340--97355343) -(97355350--97355351) -(97355366--97355391) -(97355400--97355408) -(97355784--97355806) -(97356054--97356117) -(97358693--97358695) -(97358708--97358743) -(97358756--97358759) -(97358769--97358775) -(97358789--97358791) -(97358928--97358963) -(97358988--97358991) -(97360568--97360632) -(97361797--97361847) -(97361865--97361924) -(97362264--97362331) -(97362706--97362769) -(97362810--97362813) -(97362824--97362827) -(97362830--97362837) -(97363081--97363111) -(97363143--97363166) -(97363282--97363287) -(97363299--97363309) -(97363323--97363326) -(97363336--97363339) -(97363343--97363350) -(97365276--97365279) -(97365412--97365423) -(97365449--97365507) -(97365540--97365603) -(97365928--97366024) -97366280 -(97366489--97366520) -(97366608--97366633) -(97366838--97366870) -(97366872--97366903) -(97366960--97366984) -(97367564--97367595) -(97368332--97368350) -(97368367--97368387) -(97368392--97368519) -(97368784--97368843) -(97369108--97369111) -(97369144--97369162) -(97369685--97369799) -(97369804--97369807) -(97369872--97369880) -(97369966--97369997) -(97370600--97370663) -(97370728--97370766) -(97371376--97371403) -(97371416--97371419) -(97371664--97371727) -(97371791--97371794) -(97371880--97371892) -(97371894--97371901) -(97371912--97371922) -(97372016--97372046) -(97372512--97372543) -(97372792--97372839) -(97372896--97372936) -(97373128--97373191) -(97373356--97373386) -(97373465--97373524) -(97373899--97373902) -97374031 -(97374034--97374036) -97374231 -(97374464--97374478) -(97374515--97374534) -(97375175--97375238) -(97375250--97375317) -(97375525--97375552) -(97375762--97375872) -(97377020--97377043) -(97377046--97377047) -97377111 -(97377592--97377655) -(97377747--97377875) -(97378000--97378002) -(97379455--97379476) -(97379528--97379568) -(97379989--97380041) -(97380580--97380631) -(97381072--97381079) -(97381089--97381104) -(97381109--97381115) -(97381480--97381500) -(97381657--97381660) -(97381759--97381822) -(97381824--97381886) -97381896 -(97382175--97382239) -(97382496--97382503) -(97382506--97382513) -(97382616--97382619) -(97383957--97383964)
Fix? yes

Free blocks count wrong for group #0 (2, counted=0).
Fix? yes

Free blocks count wrong for group #1 (29602, counted=29497).
Fix? yes

Free blocks count wrong for group #2 (32254, counted=32252).
Fix? yes

Free blocks count wrong for group #3 (31205, counted=31203).
Fix? yes

Free blocks count wrong for group #10 (32254, counted=32253).
Fix? yes

Free blocks count wrong for group #11 (32254, counted=32252).
Fix? yes

Free blocks count wrong for group #20 (32254, counted=32253).
Fix? yes

Free blocks count wrong for group #21 (32254, counted=32252).
Fix? yes

Free blocks count wrong for group #28 (32254, counted=32253).
Fix? yes

Free blocks count wrong for group #29 (32254, counted=32252).
Fix? yes

Free blocks count wrong for group #36 (32254, counted=32253).
Fix? yes

Free blocks count wrong for group #37 (32254, counted=32252).
Fix? yes

Free blocks count wrong for group #44 (32254, counted=32253).
Fix? yes

Free blocks count wrong for group #45 (32254, counted=32251).
Fix? yes

Free blocks count wrong for group #46 (32254, counted=32252).
Fix? yes

Free blocks count wrong for group #53 (31766, counted=31765).
Fix? yes

Free blocks count wrong for group #54 (32254, counted=32252).
Fix? yes

Free blocks count wrong for group #61 (32250, counted=32249).
Fix? yes

Free blocks count wrong for group #62 (31757, counted=31755).
Fix? yes

Free blocks count wrong for group #69 (32254, counted=32253).
Fix? yes

Free blocks count wrong for group #70 (32254, counted=32252).
Fix? yes

Free blocks count wrong for group #78 (32243, counted=32242).
Fix? yes

Free blocks count wrong for group #79 (32254, counted=32252).
Fix? yes

Free blocks count wrong for group #86 (32254, counted=32253).
Fix? yes

Free blocks count wrong for group #87 (32254, counted=32252).
Fix? yes

Free blocks count wrong for group #94 (32254, counted=32253).
Fix? yes

Free blocks count wrong for group #95 (32254, counted=32252).
Fix? yes

Free blocks count wrong for group #102 (32254, counted=32253).
Fix? yes

Free blocks count wrong for group #103 (32254, counted=32252).
Fix? yes

Free blocks count wrong for group #110 (32254, counted=32253).
Fix? yes

Free blocks count wrong for group #111 (32254, counted=32252).
Fix? yes

Free blocks count wrong for group #119 (32254, counted=32253).
Fix? yes

Free blocks count wrong for group #120 (32254, counted=32252).
Fix? yes

Free blocks count wrong for group #127 (32254, counted=32253).
Fix? yes

Free blocks count wrong for group #128 (32254, counted=32252).
Fix? yes

Free blocks count wrong for group #750 (32254, counted=32253).
Fix? yes

Free blocks count wrong for group #1758 (32254, counted=32253).
Fix? yes

Free blocks count wrong for group #2512 (22123, counted=22122).
Fix? yes

Free blocks count wrong for group #2528 (22872, counted=22871).
Fix? yes

Free blocks count wrong (61476457, counted=61476294).
Fix? yes

Inode bitmap differences: +(49153--49312) +(49345--49376) +1015809 +(12304397--12304640) +(12320705--12320736) +(28803082--28803328) +(41156611--41156640) +(41418773--41418784) +(45531329--45531360) +(45532641--45532672) -(47693825--47693856)
Fix? yes

Free inodes count wrong for group #3 (16384, counted=16192).
Fix? yes

Free inodes count wrong for group #751 (15456, counted=16096).
Fix? yes

Free inodes count wrong for group #1758 (16384, counted=16128).
Fix? yes

Free inodes count wrong for group #2512 (16384, counted=16352).
Fix? yes

Free inodes count wrong for group #2528 (16384, counted=16352).
Fix? yes

Free inodes count wrong for group #2779 (16384, counted=16320).
Fix? yes

Free inodes count wrong (48838446, counted=48838510).
Fix? yes


/dev/sdb1: ***** FILE SYSTEM WAS MODIFIED *****

2194 inodes used (0.00%)
653 non-contiguous inodes (29.8%)
# of inodes with ind/dind/tind blocks: 923/904/0
36200906 blocks used (37.06%)
192 bad blocks
1 large file

1173 regular files
148 directories
0 character device files
0 block device files
0 fifos
0 links
0 symbolic links (0 fast symbolic links)
0 sockets
--------
1321 files
e2fsck 1.40.8 (13-Mar-2008)
grow filesystem to fill the partition  00:01    ( ERROR )
     	
resize2fs /dev/sdb1
     	
Couldn't find valid filesystem superblock.
resize2fs 1.40.8 (13-Mar-2008)
resize2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1 


```



and I also got info from the syslog, i'll just put a couple of lines that seem important:
```


May 28 05:14:31 ubuntu kernel: [32064.138216] end_request: I/O error, dev fd0, sector 0
May 28 05:14:43 ubuntu kernel: [32076.298308] end_request: I/O error, dev fd0, sector 0
May 28 05:14:56 ubuntu kernel: [32088.454649] end_request: I/O error, dev fd0, sector 0
May 28 05:14:56 ubuntu kernel: [32088.454659] printk: 19 messages suppressed.
May 28 05:14:56 ubuntu kernel: [32088.454664] Buffer I/O error on device fd0, logical block 0
May 28 05:15:08 ubuntu kernel: [32100.606652] end_request: I/O error, dev fd0, sector 0
May 28 05:15:08 ubuntu kernel: [32100.606664] Buffer I/O error on device fd0, logical block 0
May 28 05:15:08 ubuntu kernel: [32100.609610] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
May 28 05:15:08 ubuntu kernel: [32100.609620] end_request: I/O error, dev sdb, sector 0
May 28 05:15:08 ubuntu kernel: [32100.609625] Buffer I/O error on device sdb, logical block 0
May 28 05:15:08 ubuntu kernel: [32100.609634] Buffer I/O error on device sdb, logical block 1
May 28 05:15:08 ubuntu kernel: [32100.609638] Buffer I/O error on device sdb, logical block 2
May 28 05:15:08 ubuntu kernel: [32100.609642] Buffer I/O error on device sdb, logical block 3
May 28 05:15:08 ubuntu kernel: [32100.609743] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
May 28 05:15:08 ubuntu kernel: [32100.609749] end_request: I/O error, dev sdb, sector 0
May 28 05:15:08 ubuntu kernel: [32100.609753] Buffer I/O error on device sdb, logical block 0
May 28 05:15:08 ubuntu NetworkManager: <debug> [1211951708.859583] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_491e5028_b6be_4bd2_b82f_2791131e16d7'). 
May 28 05:15:08 ubuntu NetworkManager: <debug> [1211951708.962942] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_491e5028_b6be_4bd2_b82f_2791131e16d7'). 
May 28 05:16:11 ubuntu kernel: [32164.288845] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
May 28 05:16:11 ubuntu kernel: [32164.288859] end_request: I/O error, dev sdb, sector 65
May 28 05:16:11 ubuntu kernel: [32164.289122] EXT3-fs: unable to read superblock
```

---

