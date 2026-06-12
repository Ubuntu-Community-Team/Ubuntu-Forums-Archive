---
title: "[post-wubi] [hibernation] [newbie] &quot;PM: Cannot find swap device, try swapon -a.&quot;"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by tlroche on 2009-08-01
**summary:** my ThinkPad Z61t hibernates and suspends in winxp, successfully wubi-ed xubuntu-9.04, and suspended from wubi. After its battery died I migrated from wubi to partitions (using lvpm) to enable hibernation, but it now fails to hibernate with

```
PM: Cannot find swap device: try swapon -a.
```

**details:**

In a [previous thread]("http://ubuntuforums.org/showthread.php?p=7679431") I learned, after my battery died while wubi-ed, that wubi was unable to hibernate. Accordingly I made ext3 and swap partitions and migrated my wubi install to them using the [lvpm instructions]("http://lubi.sourceforge.net/lvpm.html"). After fixing some GRUB and fstab problems, my xubuntu-9.04

+ is working in partitions

```
tlroche@tlrZ61t:~$ sudo fdisk -l
> Disk /dev/sda: 100.0 GB, 100030242816 bytes
> 240 heads, 63 sectors/track, 12921 cylinders
> Units = cylinders of 15120 * 512 = 7741440 bytes
...
>    Device Boot   Start     End    Blocks   Id  System
> /dev/sda1   *        1    2814  21273808+   7  HPFS/NTFS
> /dev/sda2        12297   12921   4725000   12  Compaq diagnostics
> /dev/sda3         2815   12296  71683920    f  W95 Ext'd (LBA)
> /dev/sda5         2815    9522  50712448+   7  HPFS/NTFS
> /dev/sda6         9523   12018  18869728+  83  Linux
> /dev/sda7        12019   12296   2101648+  82  Linux swap / Solaris
> Partition table entries are not in disk order

tlroche@tlrZ61t:~$ sudo swapon -sv
> Filename   Type          Size    Used    Priority
> /dev/sda7  partition  2101640       0       -1

```
+ can still suspend (with AC, of course--battery is still dead)

- but still can't hibernate:

0 When I hit the Action Buttons icon in upper right of panel and choose Hibernate, my screen goes black (first dark then backlit), a cursor blinks in upper left of screen for many seconds, eventually I get an error like

```
PM: Cannot find swap device, try swapon -a.
```

  which also persists for several seconds before my X session restores.

1 When I goto tty1 (via C-A-F1), login and run

```
$ sudo pm-hibernate
```

  my screen goes black, a cursor blinks in upper left of screen for a few seconds, and I get the same error

```
PM: Cannot find swap device, try swapon -a.

```
  before I am returned to the commandline.

But swap sure seems to be on, since I can do

```
tlroche@tlrZ61t:~$ sudo swapon -a
tlroche@tlrZ61t:~$ sudo swapoff -a
tlroche@tlrZ61t:~$ sudo swapon -a
tlroche@tlrZ61t:~$ sudo swapon -sv
> Filename                              Type            Size    Used    Priority
> /dev/sda7                             partition       2101640 0       -1
```

(Am I missing something?) Furthermore

2 hibernation still works in winxp. 

3 When I run the [Sleep Quirk Debugger]("http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-debug.html") I get

```
tlroche@tlrZ61t:~$ ./bin/quirk-checker.sh
> -e Checking your system...
> Suspend should work!
```

How to fix?

your assistance is appreciated, Tom Roche <Tom_Roche@pobox.com>

---

### Post by tlroche on 2009-08-02
I tried two more things, but still, no fix (not even a change in the error behavior):

[LIST=1]
[*]I remembered that I had hibernated winxp and thought that might somehow conflict. So I booted winxp, shut it down, restarted xubuntu, and tried to hibernate ... but it still says

```
PM: Cannot find swap device: try swapon -a.
```

[*]I looked @ my /etc/fstab and noticed that it still had "loop" in the line for the swap partition, so I edited

```
-/dev/sda7                    none           swap     loop,sw                         0      0
+/dev/sda7                    none           swap     sw                              0      0

```
restarted xubuntu, and tried to hibernate ... no change.
[/LIST]

Any more ideas? TIA, Tom Roche <Tom_Roche@pobox.com>

---

### Post by robber on 2009-08-06
I have the same problem you have, any resolution?  My system is Ubuntu 9.04 installed on Thinkpad X61s, moved from wubi by LVPM.

---

### Post by tlroche on 2009-08-07
> **robber said:**
> I have the same problem you have, any resolution?
Alas no. I got some more ideas on [a LUG list]("http://www.trilug.org/pipermail/trilug/Week-of-Mon-20090727/059151.html"), but no fix there either. I'm thinking something must be bad about my swap partition, plus I may need another partition for OpenAFS, so I may try just backing/whacking my existing xubuntu and creating new partitions.

---

### Post by rienesl on 2009-08-17
Hi,
I have a X300 and had the same problem, after changing a few things in the partition table. I solved the problem by checking:
1) /etc/fstab
2) /etc/initramfs-tools/conf.d/resume
If the UUID is correct, then Hibernate should work again.
Greetings,
Martin

---

### Post by brzeti on 2009-09-25
For me worked:
```
sudo apt-get install --reinstall initramfs-tools
```

---

