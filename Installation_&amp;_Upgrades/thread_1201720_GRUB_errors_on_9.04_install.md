---
title: "GRUB errors on 9.04 install"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by Perey on 2009-07-01
Hi folks,

I'm doing a clean install of Kubuntu 9.04 AMD64 on a brand new computer, and it's turning into a bit of a saga.

Pertinent hardware info
```
Core 2 Duo E7400 CPU
2GB DDR3 RAM
500GB SATA hard drive
```

What I *think* the problem is right now: GRUB tries to boot /dev/sda1, when the root is on /dev/sda3.

Live CD boots fine, though it doesn't recognise my USB keyboard at the boot menu; I've used a PS2 keyboard to select different options there, namely the disk and memory scans, which check out fine.

At first, I just let the installer run with the default partitioning. That got me an "Error 18" on next boot; a bit of research shows this is caused by the boot loader not being in the first 1023 cylinders.

So I reinstalled, manually partitioning as follows:
```
/dev/sda1: ext3, /boot, ~128MB
/dev/sda5: swap, ~4GB
/dev/sda6: ext3, /, all remaining space (~490GB)
```
(Note that sda5 and sda6 are now sda2 and sda3 for reasons explained below; also, sda1 is now ext2. Just so nobody gets confused.)

My recollection gets a bit fuzzy here; I think next I started getting "Error 16", and tweaking some BIOS settings fixed that. (fsck -f -y reports everything is fine on both / and /boot.)

Anyway, it went through a few different errors and lots more BIOS tweaking and poking around on my part, plus a couple more reinstalls from scratch. Where it's at now is that, sometimes, GRUB gives me an "Error 25" at stage 1.5; most of the information I can find on this error relates to dual boot and/or multiple disk and/or upgrade scenarios. But that's okay, because most of the time, it hits stage 1.5, sits there for some time, then the screen clears and it tells me:
```
Boot from (hd0,0) ext2 788523f6-b5ad-46bc-a9ea-9f4ad092cec8
```

This seems odd, because doesn't (hd0,0) mean /dev/sda1, i.e. /boot? And shouldn't it be trying to boot from the root partition, namely /dev/sda3 or (hd0,2)? That's all I've been able to guess at, anyway. I have no idea how to change this. (menu.lst? Can't find any mention of (hd0,0) in there. Maybe it's done by UUID?)

Various things I've tried, at varying levels of craziness and desperation:
[list]
[*]Poking around in menu.lst
[*]Under "Advanced..." in the installer, changed boot location from /dev/sda to /dev/sda1
[*]Moving logical partitions to physical partitions (i.e. sda5,6 to sda2,3)
[*]Making /boot ext2 instead of ext3
[*]Enabling AHCI
[*]Disabling NX
[/list]

Various crazy ideas I *haven't* tried yet:
[list]
[*]Using i386 instead of amd64
[*]Using Ubuntu instead of Kubuntu
[*]Splitting up the big partition, putting root on a smaller one
[/list]

The following may be of use:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 blocks
Disk identifier: 0x00049156

   Device Boot     Start        End      Blocks   Id  System
/dev/sda1   *          1         16      128488+  83  Linux
/dev/sda2             17        514     4000185   82  Linux swap / Solaris
/dev/sda3            515      60801   484255327+  83  Linux

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="788523f6-b5ad-46bc-a9ea-9f4ad092cec8" TYPE="ext2"
/dev/sda2: TYPE="swap" UUID="7767743d-04bb-4c35-8906-5b97d984feca"
/dev/sda3: UUID="ea4c9f51-ca46-41cc-a9ad-e02fcab69e79" TYPE="ext3"
```

I've attached menu.lst.

---

### Post by lindsay7 on 2009-07-01
Try this,

>  Originally Posted by lindsay7  View Post
Do this,

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.


Thanks to Presence1960 for the write up

---

### Post by Perey on 2009-07-02
Thanks Lindsay, trying now... it's sitting there for ages... and it's working! (Gosh I hope it doesn't take that long on every boot.)

(For the benefit of anybody else who has this problem, note that I had to use "find /grub/stage1" instead of "find /boot/grub/stage1" -- because /boot is its own partition, and find searches relative to the root of each partition.)

Okay, spoke too soon. Now, after having the graphical Kubuntu startup screen for a few seconds, it's dumped me to a screen full of (what appears to me as) garbage:
```
Enter 'help' for a list of built-in commands.

(initramfs) [   35.804037] ata1.00: exception Emask 0x0 SAct 0xf SErr 0x400001 a
ction 0x6 frozen
[   35.804078] ata1: SError: { RecovData Handshk }
[   35.804116] ata1.00: cmd 60/01:00:3f:eb:03/00:00:00:00:00/40 tag 0 ncq 512 in
[   35.804118]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeo
ut)
[   35.804196] ata1.00: status { DRDY }
```
And then it repeats the "cmd"/"res"/"status" lines another three times, with some different numbers after cmd, tag and ncq.

Help?

(Incidentally, you reminded me of one other thing I'd tried: at the end of the installer, under "Advanced...", I'd tried changing the boot location from /dev/sda to /dev/sda1. I think that might have made the difference between "Error 25" and simply hanging, but I'm not positive.)

EDIT: Google points me right here to the [Ubuntu forums](http://ubuntuforums.org/showthread.php?p=5691406), which seem to be telling me that my disk is bad. True? Overreaction? The disk check at the live CD menu didn't find any problems... (That thread lists a workaround, but the bug it refers to appears to have been fixed well before Jaunty. I'll try it anyway.)

EDIT AGAIN: No luck. Same issue, although this time, the errors didn't come all together, so I got to see the text that got scrolled off the screen last time. Alas, it still scrolled away before I could copy it down, but it did have something *like* the following:
```
/dev/by-uuid/<UUID here, I think it was the ...cec8 one> not found
```

---

### Post by Perey on 2009-07-02
Okay, scratch all three of the remaining crazy ideas: tried i386 instead of amd64, tried Ubuntu instead of Kubuntu, tried cutting root down to 80GB and putting the balance into a separate /home partition. Every clean install gets me back to Error 16 (inconsistent file system).

*sigh*

---

### Post by Perey on 2009-07-11
Okay, after a week away from all computers, I've come back with a clear head and managed to resolve the issue. Sort of.

I was suspecting that the issue actually lay with the BIOS, so I went in and hit "Load Fail-safe Defaults", just on the off chance that it might work (expecting it to fail, and burning the alternate install disk at the same time). Lo and behold, Kubuntu starts just fine.

I'm not sure what kind of wacky setup I'd last tried; I'm about to find out now, I guess. (I know it's Kubuntu, but is it amd64 or i386? How did I partition it? etc.) Whatever it is, I might be too scared to change it. ;)

I will however go back into the BIOS and see if I can find out what caused the problem. I'll report back here if and when I find out.

---

### Post by Perey on 2009-07-12
Looks like the problem's come back, or more accurately, it comes and goes. Sometimes it won't boot; Error 16, like before. The rest of the time, it boots, but very slowly, and with screens full of incomprehensible error-like messages: "DRDY"s and "ICRC"s and "/dev/sda2 has errors, check forced".

I've looked through /var/log/ for a record of these messages, but while some of the log files have similar stuff, none have exactly what I saw. Here's a sample from /var/log/syslog:

```
Jul 12 18:42:12 dux kernel: [ 1312.317920] ata1.00: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x6
Jul 12 18:42:12 dux kernel: [ 1312.317924] ata1.00: BMDMA stat 0x26
Jul 12 18:42:12 dux kernel: [ 1312.317927] ata1.00: SError: { UnrecovData Handshk }
Jul 12 18:42:12 dux kernel: [ 1312.317933] ata1.00: cmd 35/00:00:62:84:0e/00:04:37:00:00/e0 tag 0 dma 524288 out
Jul 12 18:42:12 dux kernel: [ 1312.317934]          res 51/84:75:ed:84:0e/84:03:37:00:00/e0 Emask 0x30 (host bus error)
Jul 12 18:42:12 dux kernel: [ 1312.317937] ata1.00: status: { DRDY ERR }
Jul 12 18:42:12 dux kernel: [ 1312.317939] ata1.00: error: { ICRC ABRT }
Jul 12 18:42:12 dux kernel: [ 1312.317946] ata1.00: hard resetting link
Jul 12 18:42:13 dux kernel: [ 1312.636034] ata1.01: hard resetting link
Jul 12 18:42:13 dux kernel: [ 1313.112077] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jul 12 18:42:13 dux kernel: [ 1313.112088] ata1.01: SATA link down (SStatus 0 SControl 300)
Jul 12 18:42:13 dux kernel: [ 1313.137127] ata1.00: configured for UDMA/133
Jul 12 18:42:13 dux kernel: [ 1313.137136] ata1: EH complete
Jul 12 18:42:13 dux kernel: [ 1313.161056] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465GiB)
Jul 12 18:42:13 dux kernel: [ 1313.170495] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 18:42:13 dux kernel: [ 1313.170498] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 12 18:42:13 dux kernel: [ 1313.174793] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

Is my hard drive toast? There's no SMART errors...

---

