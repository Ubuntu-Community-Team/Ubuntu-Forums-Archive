---
title: "No CD-ROM at all on Acer Travelmate 522"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by olmari on 2007-12-04
[COLOR="Red"]Adding acpi=off to grub bootline did the trick![/COLOR]

[COLOR="DarkRed"]PAH! with acpi=off CD-ROM starts to work as should, but then no battery information and charging information etc on the Linux... Any hints how to have both?[/COLOR]


So as title says, I have no optical drive at all on Acer Travelmate 522TXV. /dev has no whatsoever node for cdrom, no hdX, scX, sdX, nothing...

I saw few threads about same issue, but none gives any [here](http://ubuntuforums.org/showthread.php?t=353773) and [here]("http://ubuntuforums.org/showthread.php?t=327942")...

snippet from dmesg:
```
[ 1893.516000] ide-cd: cmd 0x3 timed out
[ 1893.516000] hdc: lost interrupt
[ 1955.520000] hdc: lost interrupt
[ 2015.520000] ide-cd: cmd 0x3 timed out
[ 2015.520000] hdc: lost interrupt
[ 2015.520000] hdc: request sense failure: status=0x7f { DriveReady DeviceFault SeekComplete DataRequest CorrectedError Index Error }
[ 2015.520000] hdc: request sense failure: error=0x7f { IllegalLengthIndication EndOfMedia AbortedCommand MediaChangeRequested LastFailedSense=0x07 }

```

The drive works itself, also shows up in Windows... AFAIK Travelmates BIOS doesn't do it's job very well, if that does matter, installing ubuntu for example (with mini.iso) stated that "installing grub is probing devices to guess BIOS boot device, it may tike some time" or so.

---

### Post by olmari on 2007-12-06
*bump*

---

