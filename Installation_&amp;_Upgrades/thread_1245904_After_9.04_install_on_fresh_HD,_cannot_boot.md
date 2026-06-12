---
title: "After 9.04 install on fresh HD, cannot boot"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by cheshirex on 2009-08-21
I've been playing with Ubuntu for a little bit before, and since we now have a separate computer for the Windows-dependent, and a brand new HD (both my HDs are SATA, if that makes a difference), I decided to do a clean Ubuntu install and leave everything else off of the system.

I've installed 9.04 from an amd64 live install CD. The install CD worked fine, but when I try to boot the system, I get the standard "DISK BOOT FAILURE..." message which indicates that the computer can't find anything to boot off of. If I insert the live CD and then select "Boot off of first hard disk", then the computer boots up just fine.

On trying to figure this out for myself, most similar errors Google found indicate that Grub needs to be reinstalled. So I tried two slightly different solutions I found. I tried 

```
sudo grub-install /dev/sda
```It seemed to succeed, but when I rebooted, I got the same error message. The other solution I tried was to start grub's interface and issued:

```
find /grub/stage1
```which returned (hd0,0)

So I issued

```
root (hd0,0)
setup (hd0)
```Again, everything seemed to work, but again, when I rebooted, no change.

I couldn't find anything via Google that seemed to address this, and I'm out of ideas to figure this out. My computer functions as long as I boot off of the live CD and select "Boot off of first hard drive", but I'd really rather remove that dependency. Can anyone help please?

Thanks!

---

### Post by nhanquy on 2009-08-21
> **cheshirex said:**
> I've been playing with Ubuntu for a little bit before, and since we now have a separate computer for the Windows-dependent, and a brand new HD (both my HDs are SATA, if that makes a difference), I decided to do a clean Ubuntu install and leave everything else off of the system.

I've installed 9.04 from an amd64 live install CD. The install CD worked fine, but when I try to boot the system, I get the standard "DISK BOOT FAILURE..." message which indicates that the computer can't find anything to boot off of. If I insert the live CD and then select "Boot off of first hard disk", then the computer boots up just fine.

On trying to figure this out for myself, most similar errors Google found indicate that Grub needs to be reinstalled. So I tried two slightly different solutions I found. I tried 

```
sudo grub-install /dev/sda
```It seemed to succeed, but when I rebooted, I got the same error message. The other solution I tried was to start grub's interface and issued:

```
find /grub/stage1
```which returned (hd0,0)

So I issued

```
root (hd0,0)
setup (hd0)
```Again, everything seemed to work, but again, when I rebooted, no change.

I couldn't find anything via Google that seemed to address this, and I'm out of ideas to figure this out. My computer functions as long as I boot off of the live CD and select "Boot off of first hard drive", but I'd really rather remove that dependency. Can anyone help please?

Thanks!

Maybe the BIOS did not see the disk. Do you need to set up jumpers on the disk? 
Read the computer manual about howto set up a new hard drive.

---

### Post by pawhtiobo on 2009-08-21
Check the BIOS about the SATA operating mode - AHCI or Compatible (PATA), try that option, in the main page of the BIOS is the HD listed?


see ya....

---

### Post by cheshirex on 2009-08-21
The BIOS sees the HD and identifies it correctly. 

I'll just note that I've been running this system for a long time now with SATA drives only, both under Windows and (for a short time, until my wife decided she always needed to reboot to Windows) under Ubuntu 8.04 with no problems. Admittedly, then the boot drive was a different drive altogether, but I can't imagine that being the issue here.

No jumpers needed. (I haven't actually seen any SATA drives that need jumpers set -- I won't miss that from the PATA days!)

---

