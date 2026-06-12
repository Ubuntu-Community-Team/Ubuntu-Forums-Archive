---
title: "Cannot boot ubuntu with IDE controller enabled"
date: 2011-01-08
forum: Hardware
---

### Post by colingw on 2011-01-08
I installed Ubuntu 10.10 today on a computer of mixed new/old components. The motherboard, processor are new, as well as an SSD for the operating system, accompanied by my very old windows (ntfs) hard drive and cd burner. Both hard drive and cd burner are IDE, plugged into the IDE port on the mobo; the installation of windows still exists but I am not trying to use it, just use that drive as storage space.

It seems that all the new hardware is working well, but the old IDE drives are causing trouble. When I first completed the installation, the IDE hard drive was not plugged in, and ubuntu called the ssd sda. Then when I plugged in the IDE drive, it took over sda and made the ssd to be sdb. I then edited fstab to auto-mount the hard drive into a nicely named folder instead of the auto-generated name that ubuntu came up with, but when I rebooted it would not boot. I disabled the IDE controller in the bios and it booted fine, and the ssd was back to sda. Reverting the changes in fstab have no effect; I'm trying to figure out where else there could be an error in the system causing confusion when the IDE drive is enabled, but I have no idea where to look. I'm wondering if there's anything up with the drives that causes them to conflict now when they both try to claim sda.

system basics:
motherboard: M4A88TD-M/USB3
Athlon II X2 265
Crucial C300 CTFDDAC064MAG-1G1 SSD
HDD: WDC WD1200JB-75CRA0 (about 8 years old, but still worked fine until my old motherboard failed)

current fstab:
```

proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=890f8566-3a78-44a0-9bb4-ff50a17d70da /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=a152c426-7507-401a-80b0-c1fca69ffedc /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=c4349ba2-a570-4930-9534-a25316404eba none            swap    sw              0       0

```

---

### Post by colingw on 2011-01-09
looks like I solved my own problem. I guess I'd messed up my initrd, so I ran update-initramfs and that took care of it

---

