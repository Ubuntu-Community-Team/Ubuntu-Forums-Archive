---
title: "Battery shows impossible design capacity"
date: 2010-10-02
forum: Hardware
---

### Post by offisapup on 2010-10-02
I have a curious problem, or possibly two, with my HP Compaq nx8220, running Kubuntu 10.04.

There are two manifestations that may or may not be related:

1. The battery is completely dead -- although it gave me something like an hour not that long ago (sorry to be imprecise, but ...) It might be it simply died, but it is recognized, but acpi reports it as having design capacity 1 mAh, which can't be right. Is this a symptom of the battery being bad? Or is it ACPI being buggy? (all of the info below).

2. The system hangs in startup and shutdown, in the BIOS. I've updated the BIOS to the latest version (an adventure in itself, since it required a venture into WIndows-land), but this made no difference. To make it more interesting, the startup works if the machine is cold. Otherwise it hangs with the BIOS screen. May this be related to the battery? Or is it a symptom of the motherbord/cpu/whatever going? There are no messages in the logs, so it's probably not a kernel bug, or ... ?

Is there anything I can do to fix the battery? Reset the EEPROM?

Is there anything I can do to find out what is happening in the boot, to work out whats wrong?

Cheers /offsiapup
present:                 yes
design capacity:         1 mAh
last full capacity:      1 mAh
battery technology:      rechargeable
design voltage:          14400 mV
design capacity warning: 1 mAh
design capacity low:     1 mAh
capacity granularity 1:  100 mAh
capacity granularity 2:  100 mAh
model number:            Primary
serial number:           24656 2005/06/24
battery type:            LIon
OEM info:                Hewlett-Packard

---

### Post by Dark_Stang on 2010-10-02
I had an Acer laptop a few years ago. After it's battery went out I had to boot it with the battery out, otherwise it would hang for several minutes at startup and run terribly. This was in Linux and Windows. A new battery fixed it. Pop your battery out and see if that fixes it.

Failing optical drives, hard drives, raid cards, and some PCI devices can also cause systems to hang at the POST screen during boot.

---

### Post by offisapup on 2010-10-03
Thanks, already tried running without the battery, but doesn't make any difference -- hangs exactly the same way with the battery out.

There are nothing bad with the disks (as shown by fsck), I've checked the RAM with memtest, and that's OK. In fact, as soon as it's booted OK, it works as expected.

/offisapup

---

### Post by P4man on 2010-10-03
If you have the same problem with the battery removed, then its something entirely different.

As suggested by the above poster, try removing everything you dont strictly need for booting. Plug out the optical drive and possibly the wifi card. Disable whatever other peripherals you can in the BIOS, like USB, ethernet, serial/parallel ports, audio. Though most laptops dont give a lot to play with there. You could also try removing the harddrive and booting from an USB stick.

Lastly, make sure you disable the full screen OEM bios logo (if any) so you can perhaps see what the bios is doing.

---

