---
title: "Ubuntu 15.10 Bay Trail compatibility status"
date: 2015-09-14
forum: Hardware
---

### Post by 28362836a on 2015-09-14
As some of you may know, Ubuntu 15.04 had several compatibility issues with Bay Trail (tablet specific) hardware, that made it unusable. Ubuntu 15.10 gives me hope already, because many incompatibilities have been fixed!

hardware: Winbook TW100

This list describes progress made (14.10 is provided only as a reference) Note: Incompatibilities here are based on one set of hardware, results may differ tablet by tablet

14.10:
-ACPI, non-existent support
-sound, no support
-touchscreen, no support
-Wifi/BT, no support
-Internal flash, support
-USB/HDMI, support
-Detachable keyb, support
-External SD card, spotty support

15.04
-ACPI, slightly improved
-sound, no support
-touchscreen, spotty support (usually inverted input)
-Wifi/BT, no support
-Internal flash, spotty support
-USB/HDMI, spotty support
-Detachable keyb, support
-External SD card, spotty support
ALSO: Stability issues, not present in 14.10. Random freezing/crashing, especially during periods of high disk usage.

15.10 (latest ISO build)
-ACPI, even more improved, still spotty
-sound, no support
-touchscreen, fully supported!
-Wifi/BT, no support
-Internal flash, spotty support
-USB/HDMI, supported
-Detachable keyb, support
-External SD card, untested, but expected support
ALSO: Stability issues not present (interacting with internal flash may cause stability issues still)

UPDATE 12/22/2015:
Ubuntu 15.10 is now usable on Bay Trail hardware. Here is a comprehensive list of what the final release of Wily Werewolf fixed

What works
-Touch (almost flawless)
-Battery level
-Screen Brightness
-Graphics acceleration (Intel Gen7)
-USB/HDMI/SDCard
-Internal storage read/write
-Hardware Detection

What doesn't work
-Wifi/BT
-Gyro (Screen rotation)
-Sound
-Capacitive buttons

ALSO: Stability issues almost gone, still remain.

---

### Post by 28362836a on 2015-09-15
UPDATE: Ubuntu 15.10 has fixed the instability issues that plagued 15.04 on bay trail hardware. That being said, 15.10 still doesn't support the internal flash for most bay trail tablets, making it literally impossible to install Ubuntu internally. Anybody wishing to install Ubuntu on their bay trail tablet will be forced to revert to 14.10, as it supports all internal flash types.

---

