---
title: "HDD case stopped working (this is an emergency! lol)"
date: 2009-05-27
forum: Hardware
---

### Post by Laucien on 2009-05-27
Hey guys, I have a huuuuge problem.
I recently bought a new laptop (Lenovo ThinkPad SL500) and Icy Box case for 2.5" hdd. So far everything worked fine, I used the hdd from old laptop via the case, but just few minutes ago I connected it again and my laptop just wont mount it.

lsusb gives me:
```
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 013: ID 14cd:6600 Super Top USB 2.0 IDE DEVICE
Bus 008 Device 002: ID 17ef:480b Lenovo 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 147e:1000  
Bus 003 Device 003: ID 0a5c:2145 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

``` meaning that it *is* there (device 013).

Also, syslog says:
> May 28 01:04:25 byte-laptop kernel: [ 1626.536087] usb 8-3: new high speed USB device using ehci_hcd and address 16
May 28 01:04:25 byte-laptop kernel: [ 1626.670680] usb 8-3: configuration #1 chosen from 1 choice
May 28 01:04:25 byte-laptop kernel: [ 1626.671579] scsi19 : SCSI emulation for USB Mass Storage devices
May 28 01:04:25 byte-laptop kernel: [ 1626.673482] usb-storage: device found at 16
May 28 01:04:25 byte-laptop kernel: [ 1626.673493] usb-storage: waiting for device to settle before scanning
May 28 01:04:30 byte-laptop kernel: [ 1631.673474] usb-storage: device scan complete
May 28 01:04:30 byte-laptop kernel: [ 1631.674859] scsi 19:0:0:0: Direct-Access     FUJITSU  MHT2080AH PL          PQ: 0 ANSI: 0
May 28 01:04:30 byte-laptop kernel: [ 1631.678061] sd 19:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
May 28 01:04:30 byte-laptop kernel: [ 1631.679060] sd 19:0:0:0: [sdb] Write Protect is off
May 28 01:04:31 byte-laptop kernel: [ 1631.679071] sd 19:0:0:0: [sdb] Mode Sense: 03 00 00 00
May 28 01:04:31 byte-laptop kernel: [ 1631.679077] sd 19:0:0:0: [sdb] Assuming drive cache: write through
May 28 01:04:31 byte-laptop kernel: [ 1631.680778] sd 19:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
May 28 01:04:31 byte-laptop kernel: [ 1631.681408] sd 19:0:0:0: [sdb] Write Protect is off
May 28 01:04:31 byte-laptop kernel: [ 1631.681412] sd 19:0:0:0: [sdb] Mode Sense: 03 00 00 00
May 28 01:04:31 byte-laptop kernel: [ 1631.681414] sd 19:0:0:0: [sdb] Assuming drive cache: write through
May 28 01:04:31 byte-laptop kernel: [ 1631.681761]  sdb: sdb1 sdb2 < sdb5 >
May 28 01:04:31 byte-laptop kernel: [ 1632.234081] sd 19:0:0:0: [sdb] Attached SCSI disk
May 28 01:04:31 byte-laptop kernel: [ 1632.237518] sd 19:0:0:0: Attached scsi generic sg2 type 0

And when I connect it and enter 'Computer', I can see the icon for like half a second, and then it disappears.


Please help, all my college projects are on that mutherfucker and I need one for monday (if I don't give it to professor by then I'll flunk the year).

---

### Post by Laucien on 2009-05-28
Bump (don't want to be boring but this is really important to me) [-o<

---

### Post by Laucien on 2009-05-29
Umm... Yeah, thanks a lot. :|

---

### Post by Laucien on 2009-06-04
Ok, some new info (I really hope some1 will finally notice this thread :)).
I tried to boot from two different HDD-s connected over the case.
First I tried the HDD with Ubuntu on it. On boot-up I got a message: 'Error 17'. Now I cannot even find it on the boot device list (when I press F12 on start-up).
Then I tried the HDD with WinXP on it. And I got the ******' blue screen of death, but I still do have it on a boot device list, and I can mount it when using internal HDD (built-in one, y'know...).
I just don't know what to do here, and I have some really important data on that Ubuntu HDD I cannot use.
Please help, I just can't believe nobody here knows the solution. ;)

---

### Post by Laucien on 2009-06-09
Aaaaaaaaaaa will somebody please notice this thread?!
):P

---

### Post by dandnsmith on 2009-06-09
If you're using HDDs in a case which connects via USB, then booting from them is bound to give problems if they weren't specifically 'built' for that configuration - the references will all be wrong.

You'd have a better chance booting from a liveCD to see what you can get that way. You might need System Rescue CD or something of that nature - come to think of it *testdisk* is reported to be a good tool, and it occurs as a component on a number of liveCDs (including, possibly, Ubuntu)

Have a look at [the wiki for it](http://en.wikipedia.org/wiki/TestDisk)

---

