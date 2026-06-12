---
title: "2 extra CD/DVD drives appear by magic"
date: 2010-03-27
forum: Hardware
---

### Post by white-seraph on 2010-03-27
I booted up my laptop today after the battery ran dry while I was out of the room. Every thing worked as normal, but when I went into Places-Computer, there was 2 more CD/DVD drives than when I left. Right next to my real one!
I looked in /media and they were there too, listed as cdrom and cdrom0, but they both open into my Cd drive.
i tried unmounting them through the terminal but it says there's nothing there, and I looked in fstab and only the actual drives and partitions on my computer were there.

how do i get rid of them?

---

### Post by IcarusR on 2010-03-28
Do they disappear if you reboot ??

---

### Post by srs5694 on 2010-03-28
Chances are the system got confused and thought it hadn't seen the device before and therefore built a new rule for it. You may be able to fix the problem by editing the /etc/udev/rules.d/70-persistent-cd.rules file. You'll see lines like these, although many details will differ:

```

SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:03:00.0-scsi-0:0:0:0", SYMLINK+="cdrom3", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:03:00.0-scsi-0:0:0:0", SYMLINK+="cdrw3", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:03:00.0-scsi-0:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:03:00.0-scsi-0:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"

```

Back up the original file. Study your rules and then eliminate the duplicates (/dev/cdrom0 and /dev/cdrom1, probably). If the problem recurs, you may need to eliminate the original and one duplicate and rename the device filenames for another duplicate to whatever you want.

Personally, I hate this "feature" of recent Linux distributions. (Older distributions didn't try to track specific hardware devices; if you swapped one DVD drive for another, the new one would just appear under the old one's name.) I understand its utility for some devices, which might legitimately benefit from such device-specific tracking, but it's caused me more problems than it's solved.

---

