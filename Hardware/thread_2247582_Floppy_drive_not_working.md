---
title: "Floppy drive not working"
date: 2014-10-09
forum: Hardware
---

### Post by orbitaldecay on 2014-10-09
I've encountered the first problem on Linux that I haven't been able to Google a solution for :mad:

I've recently installed a new BYTECC BT-145 3.5 inch floppy drive in my computer. If I take a properly formatted disk with a file on it, I am able to mount the floppy drive and read the file correctly. But if I modify the contents of the disk, unmount it, and physically remove the disk from the drive, the entire filesystem becomes corrupted (I've also noticed that the disk light does not turn off when I unmount a disk, which is disturbing). Moreover, fdformat, mkfs.msdos, and all other attempts to write to the disk fail.

When I run
```
mkfs.msdos /dev/fd0
```
I get
```

mkfs.fat 3.0.26 (2014-03-07)
mkfs.msdos: failed whilst writing reserved sector

```
and dmesg spits out
```

[ 2042.185278] end_request: I/O error, dev fd0, sector 1
[ 2043.786781] end_request: I/O error, dev fd0, sector 1

```
If I load the floppy module with floppy=messages (for more useful messages) dmesg spits out
```

[ 2138.234183] floppy0: Setting flag 0x1
[ 2138.234700] Floppy drive(s): fd0 is 1.44M
[ 2138.250071] FDC 0 is a post-1991 82077
[ 2192.513694] floppy0: Auto-detected floppy type H1440 in fd0
[ 2194.115173] end_request: I/O error, dev fd0, sector 1
[ 2195.716756] end_request: I/O error, dev fd0, sector 1

```
and if I load the floppy module with floppy=debug (for debugging messages) dmesg spits out [this]("http://pastebin.com/Qm8QuDv1").

So far I've tried loading the floppy module with floppy=nodma, floppy=broken_dcl and floppy=0,daring as described [here]("https://www.kernel.org/doc/Documentation/blockdev/floppy.txt") to no avail.

I'm dual booting Ubuntu 14.04 and Windows 7. The drive works flawlessly under Windows 7 (and I'm able to boot from it without issue), so its definitely a Linux problem and not a hardware problem. I'm also using an ASRock M3A770DE motherboard.

---

### Post by weatherman2 on 2014-10-09
Did you try this:

[http://ubuntuforums.org/showthread.php?t=2222487&page=2](http://ubuntuforums.org/showthread.php?t=2222487&page=2)

and put that "umask=0" in your /etc/fstab line ?

---

### Post by orbitaldecay on 2014-10-09
No dice :( Commands that don't require mounting such as fdformat don't work either.

---

### Post by Dennis N on 2014-10-09
An option that works with these disks is to use a USB floppy disk drive. 

low level format: ufiformat /dev/sdx
high level format: mkdosfs -I /dev/sdx

[http://manpages.ubuntu.com/manpages/precise/man8/ufiformat.8.html](http://manpages.ubuntu.com/manpages/precise/man8/ufiformat.8.html)
[http://linux.die.net/man/8/mkdosfs](http://linux.die.net/man/8/mkdosfs)

---

### Post by orbitaldecay on 2014-10-09
> **Dennis N said:**
> An option that works with these disks is to use a USB floppy disk drive. 

low level format: ufiformat /dev/sdx
high level format: mkdosfs -I /dev/sdx

[http://manpages.ubuntu.com/manpages/precise/man8/ufiformat.8.html](http://manpages.ubuntu.com/manpages/precise/man8/ufiformat.8.html)
[http://linux.die.net/man/8/mkdosfs](http://linux.die.net/man/8/mkdosfs)

Yeah, I'll probably try that route if I can't get the internal drive working, but I'd like to avoid buying one if I can.

---

