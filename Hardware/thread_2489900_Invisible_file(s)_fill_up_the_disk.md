---
title: "Invisible file(s) fill up the disk"
date: 2023-08-14
forum: Hardware
---

### Post by trenien2 on 2023-08-14
I've just reinstalled my computer which has multiple HDD. For various reasons, I couldn't check which partition was the original /home, so I chose one (brtfs) and used it without reformating it (I didn't want to risk deleting files that could be important). So far, no particular problem.

Except... Now that I've rebooted, I find myself with a 400G partition that's 100% filled up with nothing : my user partition takes up around 30M, but I can see no file filing up the rest.

df -h tells me the /dev/sdb4 /home is 100% filled
du -h says the files present are that of the brand new account (around 30M)
That stays true even doing it as root.

So I don't know what to do

---

### Post by Rubi1200 on 2023-08-14
Please post the output of this command:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```

When replying, use Go Advanced and wrap with # tags for us to read and interpret more easily.

---

### Post by trenien2 on 2023-08-14
I've modified my fstab to move the home partition on a different disk. No change on the original one, it still is filled up with nothing apparent.

here is the result :

```

Filesystem       Type    Size    Used  Avail  Use% Mounted on
/dev/sda1        vfat    285M    6,1M  279M     3% /boot/efi
/dev/sda2        btrfs    39G    5,5G   33G    15% /
/dev/sda4        ext4    878G    449G  384G    54% /home
/dev/sdb2        btrfs    28G    3,9M   28G     1% /media/Sys-Alt1-sdb2
/dev/sdb3        btrfs    28G    3,6M   28G     1% /media/Sys-Alt2-sdb3
/dev/sdb4        btrfs   405G    403G  404K   100% /media/Archive-sdb4

```

---

### Post by #&amp;thj^% on 2023-08-14
Something foul has happened, and i have no clue how you ended up in this current state.
I'm not sure I can help, and are you sure nothing resides In "sdb4"?
```
ls /media/Archive-sdb4
```
I'm guessing this could be back-ups from Apt changes....(From BTRFS)
Ahh this:
> and used it without reformating it (I didn't want to risk deleting files that could be important). So far, no particular problem.
Dang now you have my mind in overdrive this is one of the most unusual layouts I've seen.
See if shows with the below ON "sdb4"
```
sudo btrfs subvolume list /home
[sudo] password for me: 
ID 264 gen 9827 top level 5 path @
ID 320 gen 9783 top level 5 path timeshift-btrfs/snapshots/2023-08-08_08-14-41/@
ID 321 gen 9783 top level 5 path timeshift-btrfs/snapshots/2023-08-08_09-38-05/@
ID 322 gen 9783 top level 5 path timeshift-btrfs/snapshots/2023-08-08_09-43-23/@
ID 323 gen 9783 top level 5 path timeshift-btrfs/snapshots/2023-08-08_09-49-35/@
ID 324 gen 9783 top level 5 path timeshift-btrfs/snapshots/2023-08-08_10-07-30/@
ID 325 gen 9783 top level 5 path timeshift-btrfs/snapshots/2023-08-08_12-34-05/@
ID 326 gen 9787 top level 5 path timeshift-btrfs/snapshots/2023-08-14_10-09-36/@

```

---

### Post by Holger_Gehrke on 2023-08-14
btrfs is **very** different from other filesystems used on Linux.'df' can't make heads or tails of it. Use 'btrfs filesystem df' instead.

Holger

---

### Post by Rubi1200 on 2023-08-15
> **Holger_Gehrke said:**
> btrfs is **very** different from other filesystems used on Linux.'df' can't make heads or tails of it. Use 'btrfs filesystem df' instead.

Holger
Thank you, Holger, for this very useful tip. Noted and added to my long list of tips and tricks :-)

---

### Post by #&amp;thj^% on 2023-08-15
> **Holger_Gehrke said:**
> btrfs is **very** different from other filesystems used on Linux.'df' can't make heads or tails of it. Use 'btrfs filesystem df' instead.

Holger
I was hoping the OP would confirm my guess or not, but yes you are right this works so much nicer on BTRFS
```
btrfs filesystem df -h /run/media/me/KaisenLinux/
Data, single: total=93.01GiB, used=64.27GiB
System, DUP: total=8.00MiB, used=16.00KiB
Metadata, DUP: total=2.00GiB, used=1.06GiB
GlobalReserve, single: total=138.33MiB, used=0.00B


```

---

