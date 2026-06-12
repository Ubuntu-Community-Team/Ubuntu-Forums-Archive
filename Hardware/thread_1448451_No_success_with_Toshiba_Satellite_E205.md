---
title: "No success with Toshiba Satellite E205"
date: 2010-04-06
forum: Hardware
---

### Post by Forastan on 2010-04-06
New disk with 9.10.  Disk worked fine on an old Dell laptop.

When trying to test it on the brand-new Toshiba Satellite E205, it gets as far as the language choice screen/choice of demo or install and then all goes black and stays that way.  An underline blinks for a few seconds before everything goes black.  Disk keeps clicking for a while, but never shows anything.

Did I do something stupid and buy a laptop that can't run Ubuntu?:confused:

Tried a second disk, burned at slow speed - no difference.

Tried 9.04, safe graphics mode.  Identical failure.

Final try: 9.10 in safe graphics mode - it did boot, came up in 1024x768 resolution.  That's a start!

---

### Post by linuxlovinwarren on 2010-06-09
Hello!
I hope you didn't give up already, I know how frustrating it seems trying to load linux on the E205 but there is good news!

The problem is with ACPI which has to do with the way your laptop views your battery, so if you've already installed ubuntu when the grub comes up go to the kernel you are useing and hit e for edit, and somewhere within the boot-up options type in ACPI=off I normally put it by where it says SPLASH...

everything should be ready to go, but be pre-warned you will have no idea how much battery life is left when your not plugged in :( hopefully there will be a fix for this soon!

---

