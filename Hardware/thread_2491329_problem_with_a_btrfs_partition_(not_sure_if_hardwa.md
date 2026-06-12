---
title: "problem with a btrfs partition (not sure if hardware or soiftware)"
date: 2023-10-04
forum: Hardware
---

### Post by jduns on 2023-10-04
A short premise: I have KDE Neon (latest release) and today, after an update (via terminal), I didn't manage to get the graphical desktop. After doing a chroot with Kubuntu (in another partition of the same PC) I noticed that the problem was /dev/sdc2 (a btrfs partition on a sata disk 500 Gb added to my PC, where I have some backups not very important, at least so I believe :) ). Modifying etc/fstab in KDE Neon (so that /dev/sdc2 is no more "auto", but "noauto" mounted) I managed to have a normal graphical desktop in KDE Neon.

But I didn't manage to rescue that partition, following the instruction of several websites.
1. It was impossible to mount /dev/sdc2, because ```
can't read superblock on /dev/sdc2
```, while the other partition of that hd sata, that is /dev/sdc1 was correctly mounted.
2. Via gparted it was impossible to fix the problem. I tried several terminal commands such as 
[LIST]
[*]```
sudo mount -o recovery /dev/sdc2 /mnt/added
```, and then 
[*]```
sudo btrfs check --repair /dev/sdc2
```, 
[*]```
btrfs scrub /mnt/added
``` 
[*]```
sudo btrfs rescue zero-log /dev/sdc2
``` 
[*]```
mount -t btrfs -o ro,usebackuproot /dev/sda2 /mnt/added
``` 
[/LIST]

I.g. with this command [FONT=monospace][COLOR=#000000] sudo ```
btrfs rescue super-recover /dev/sdc2 
```[/COLOR]
I get this answer: ```
All supers are valid, no need to recover 
```[/FONT]

3. It seems that the problem was: 
```
[FONT=monospace][COLOR=#000000]parent transid verify failed on 64356352 wanted 5141 found 5136[/COLOR][/FONT]
```

Indeed:

```
[FONT=monospace][COLOR=#000000]sudo btrfs check /dev/sdc2 [/COLOR]
Opening filesystem to check... 
parent transid verify failed on 64356352 wanted 5141 found 5136 
parent transid verify failed on 64356352 wanted 5141 found 5136 
parent transid verify failed on 64356352 wanted 5141 found 5136 
Ignoring transid failure 
ERROR: root [5 0] level 0 does not match 2 

ERROR: cannot open file system
[/FONT]
```

This is an hardware or a software problem?
And therefore what should I do?
Thank you!

---

### Post by #&amp;thj^% on 2023-10-04
It's a btrfs issue, Try this, and no promise's:
```
btrfsck --init-extent-tree
```
If you don't have a backup you might be up the creek.
Note:
```
Check structural integrity of a filesystem (unmounted).

    Check structural integrity of an unmounted filesystem. Verify internal
    trees' consistency and item connectivity. In the repair mode try to
    fix the problems found. 
    WARNING: the repair mode is considered dangerous and should not be used
             without prior analysis of problems found on the filesystem.

```

---

### Post by jduns on 2023-10-04
Thank you. I will try it.

---

### Post by jduns on 2023-10-05
Unfortunately this didn't work:
```

[FONT=monospace][COLOR=#000000] sudo btrfsck --init-extent-tree /dev/sdc2 [/COLOR]
WARNING: 

        Do not use --repair unless you are advised to do so by a developer 
        or an experienced user, and then only after having accepted that no 
        fsck can successfully repair all types of filesystem corruption. Eg. 
        some software or hardware bugs can fatally damage a volume. 
        The operation will start in 10 seconds. 
        Use Ctrl-C to stop it. 
10 9 8 7 6 5 4 3 2 1 
Starting repair. 
Opening filesystem to check... 
parent transid verify failed on 64356352 wanted 5141 found 5136 
parent transid verify failed on 64356352 wanted 5141 found 5136 
parent transid verify failed on 64356352 wanted 5141 found 5136 
Ignoring transid failure 
ERROR: root [5 0] level 0 does not match 2 

ERROR: cannot open file system 
```
[/FONT]

---

### Post by jduns on 2023-10-05
At the end I decided to delete that partition and to create a new one (losing all data, I know). Now the new partition seems ok.

---

