---
title: "Filesystem error whenever there is heavy hard-drive activity"
date: 2011-10-15
forum: Hardware
---

### Post by 3602 on 2011-10-15
```
DEAR PEOPLE OF THE FUTURE: This is what I have figured out so far.
If this starts to happen after swapping some RAM, trust me it's the RAM, even if Memtest86+ doesn't detect it.
Why do I know this? Because fortunately I still have my stock RAM, so I decided to install those back. Suddenly, dragons.
Really though, it is possible that the RAM bars themselves are fine, but your computer doesn't support them, somehow. This is probably my case, since Memtest86+ detects absolutely jack yet I was struck again and again by these failures.
Also, I changed my distro. So it might be that, too.
```OK first, this started a *long* while ago.

I am using the 64-bit Ubuntu Maverick (10.10). The computer is a portable, HP dv7-4104ca.

The symptoms are always the same. The mouse moves, then it doesn't. Sometimes the Caps Lock light blinks (indicating a kernel panic), sometimes it doesn't.

Sometimes, a Magic SysRq can reboot the system. Other times only by holding down the power button can I shut it down.

Upon reboot, the message is always as so:
```
Aug 26 22:27:28 linux kernel: [    3.673595] EXT4-fs (sda1): orphan cleanup on readonly fs
Aug 26 22:27:28 linux kernel: [    3.673691] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 23069122
Aug 26 22:27:28 linux kernel: [    3.673763] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 23073767
Aug 26 22:27:28 linux kernel: [    3.673775] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 23073779
Aug 26 22:27:28 linux kernel: [    3.673786] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 23073772
Aug 26 22:27:28 linux kernel: [    3.673798] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 13239415
Aug 26 22:27:28 linux kernel: [    3.673810] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 13239294
Aug 26 22:27:28 linux kernel: [    3.673821] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 13239278
Aug 26 22:27:28 linux kernel: [    3.673832] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 13239121
Aug 26 22:27:28 linux kernel: [    3.673843] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 23073771
Aug 26 22:27:28 linux kernel: [    3.768304] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 23069269
```The above was fetched from /var/log/syslog. The number of inodes do vary. The max I've seen is 70, perhaps.

So apparently the filesystem is suddenly getting remounted as read-only.

Now, when I say "heavy hard-disk activity", it's because it happens mostly when I'm downloading something big, either on Transmission or Vuze (Azureus). But sometimes it just happens while browing and not doing anything else.

Steps I have taken to date:

* At first I thought some components of my computer are going bad. I have replaced the RAM modules (and ran numerous Memtest86+ on them with ZERO errors) and my hard drive (original one was Seagate - current one is WD).
* I have downgraded my kernel from 2.6.35-30 to 2.6.35-25, which I am using right now.
* All my packages are stable, i.e. no Proposed, no Backports.
* I have even removed my USB mouse. 
* I have tried other distros. This happens too, on: Ubuntu Natty, Fedora 14, The newest OpenSUSE, and Mandriva 2008 (all 64-bit). Oh, and during the installation of these distros, many files will not copy (always telling me to Retry, Abort or Ignore).
* I have no obvious temperature problems as "sensors" return 42°C most of the time.

And even after all the above (replacing the hardware spent me two-thirds on what I spent on the computer itself), this problem still occurs.

What the heck is going on? ACPI? Drivers?

Thank you all very much.

EDIT: I've also thought about an alignment problem since this particular WD drive has EARS on it (4096kib physical sizes), but hdparm returns correct values so it cannot be alignment.

---

### Post by 3602 on 2011-10-16
OK I'm in a Live Session right now.
```
ubuntu@ubuntu:~$ sudo fsck -f /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 215490/45096960 files (0.6% non-contiguous), 25661773/180364544 blocks

```

I'll run ```
sudo badblocks -n /dev/sda
``` and see what happens.

---

### Post by 3602 on 2011-10-18
Note to self: NEVER NEVER NEVER modify manually your *fstab*! Good thing that Live Session-fu fixes things.
Now. Back to our problem.

---

### Post by lussier on 2011-10-22
Hi,

I have the exact same problem. I first thought it was RAM, tested it with a memtest86+ and everything seems fine. I am now suspecting that my SSD drive (on which Ubuntu 11.10 is installed) causes this problem. 

When running Windows, I sometimes get frozen and get a blue screen with no indication of what happened. When I open my log file on Ubuntu I see a bunch of:

```

[    3.760239] EXT4-fs (sdc5): orphan cleanup on readonly fs
[    3.760244] EXT4-fs (sdc5): ext4_orphan_cleanup: deleting unreferenced inode 138343
[    3.760277] EXT4-fs (sdc5): ext4_orphan_cleanup: deleting unreferenced inode 138342
[    3.760284] EXT4-fs (sdc5): ext4_orphan_cleanup: deleting unreferenced inode 138341
[    3.760289] EXT4-fs (sdc5): ext4_orphan_cleanup: deleting unreferenced inode 138340
[    3.760295] EXT4-fs (sdc5): ext4_orphan_cleanup: deleting unreferenced inode 138339
[    3.760301] EXT4-fs (sdc5): ext4_orphan_cleanup: deleting unreferenced inode 138338
[    3.760307] EXT4-fs (sdc5): ext4_orphan_cleanup: deleting unreferenced inode 138337

```

My hardware:

Motherboard: ASUS Maximus III Extreme
CPU: Intel Core i7 2600K
Memory: Corsair Vengeance Low Profile 16GB 4X4GB DDR3-1600 9-9-9-24 Dual Channel Memory Kit
Hard Drive: OCZ Vertex III 120 GB
Second and third hard drives: WD Caviar Black 1TB

Please let me know if you find anything. I will do the same.

Greg

---

### Post by 3602 on 2011-10-22
Yeah this all seems very random, last night Window XP suddenly restarted and told me that I have a RAM problem... **In VirtualBox**.

Yet Memtest after Memtest reveal nothing.

The thing is, at one time I did have *actual* (as in not in VirtualBox) Windows XP installed, and I was able to finish C&C3, Half-Life 1 and 2 with the episodes, Portal 1 and 2 on it without encountering a single error.

---

### Post by Nirgo on 2012-06-16
Hi there.

So, i got the same problem on Ubuntu 12.04 LTS running on DELL Latitude E6420 with Core I5 2520-M, 4GB Ram powered by DELL, 500 GB typical HDD (7200/min).

If you know what solves the problem please tell me.

Thank you.

Greetings,
Nirgo

---

