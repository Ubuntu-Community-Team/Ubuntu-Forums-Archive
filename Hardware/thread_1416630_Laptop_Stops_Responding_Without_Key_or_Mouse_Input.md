---
title: "Laptop Stops Responding Without Key or Mouse Input"
date: 2010-02-26
forum: Hardware
---

### Post by bluebledthesea on 2010-02-26
It seems that my particular model laptop has an inherent problem running any Linux distro I try. At first I thought it was restricted to Debian/Ubuntu, but since then I have also tried Fedora 12 and openSUSE 2010.

The laptop will frequently stop responding or doing anything without keyboard or mouse input. This is to the point that it just isn't usable. I will try to install something or move a large file and I will have to sit there constantly moving my mouse for it to continue to operate. If I leave it alone or walk away it will just stop doing anything.The mouse pointer will also freeze when this happens and won't budge for another 10 seconds or so. This isn't a constant problem but comes up every couple minutes. This also happens while booted to a live CD, during installation from a live CD, and during the bootup process of the Linux distro.

The laptop is a Compal JFL90/92 model. I have tried searching for solutions and found a few people with the same problem, but haven't come up with a fix that I could make work. At first I thought this was strictly a Ubuntu/Debian incompatibility with my hardware, but after trying Fedora and SUSE to the same result I am broadening my search to see if anyone has any idea what could be going on. Thanks.

---

### Post by bluebledthesea on 2010-02-26
After some research and poking around I believe that disabling AHCI in the BIOS fixes this.

---

### Post by dabl on 2010-02-26
My Toshiba NB205 netbook does the same thing when in text mode (but not usually while X is running).  It is caused by firmware in their hard drive, which shuts it down automatically in the absence of something poking it.  I believe their Windows driver is able to keep it going while there is user input, but the Linux system does not have a "tuned" driver for it, so it falls asleep.  Playing music or tickling the touchpad works to keep mine going.  I don't think changing the SATA AHCI mode to "Legacy IDE" in BIOS would make a difference, but I admit I have not tried that.

---

