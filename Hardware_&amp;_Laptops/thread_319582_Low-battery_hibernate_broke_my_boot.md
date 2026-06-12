---
title: "Low-battery hibernate broke my boot"
date: 2006-12-15
forum: Hardware &amp; Laptops
---

### Post by Tonren on 2006-12-15
**Edit**: Two posts down is a transcription of the error messages.

OK guys, I left my laptop on and it ran out of batteries and must have tried going into hibernate.  It wrote something bogus to my swap partition. When I rebooted, it hung on Starting /scripts/pre-mount, so I popped in a live CD to check with gparted and my swap partition was no longer properly formatted.  I reformatted it as linux-swap but it's still not booting, and hanging in the same place.  I can boot into Windows, but if I try to access my ext3 /home partition, it gives me a "This drive is not formatted" message.

It was giving me some kind of error like hda: 0x40.  I'll reboot and hand-copy the errors if I have time.  This totally sux and I badly need my computer.  I can't boot into Linux!  Help!

---

### Post by Tonren on 2006-12-19
Guys, I really badly need some help here.  My laptop is still out of commission.  PLEASE come through for me.  This is really, seriously urgent.  There has to be some kind of explanation.  I can't believe letting my laptop run out of batteries did this.  This is terrible.  Someone please help.

---

### Post by Tonren on 2006-12-20
I got my hands on another computer and have transcribed the errors.  When I boot up without quiet and with the single kernel option, and switch to tty1 via Ctrl + Alt + F1 to read the error output, here's what I get:

It hangs on "Running /scripts/local-premount"

With these errors:

hda: dma_intr: status = 0x51 { DriveReady SeekComplete error }
hda: dma_intr: error = 0x40 { Uncorrectable error } LBASect = 41952600, high = 2, low = 8398168, sector = 41952453 
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 41952515

The error repeats itself, only the uncorrectable error "sector" counts up to 41952595.  Once it gets there, it outputs:

mount: Mounting /dev/disk/by-uuid/(long string of alphanumerics) on /root failed: Invalid argument
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-botttom ...
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
Done.
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

---

### Post by towsonu2003 on 2006-12-20
can you mount the partitions using a liveCD?

---

