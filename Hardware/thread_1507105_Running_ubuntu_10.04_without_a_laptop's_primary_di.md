---
title: "Running ubuntu 10.04 without a laptop's primary display"
date: 2010-06-11
forum: Hardware
---

### Post by itsmeritesh on 2010-06-11
I have an IBM thinkpad(R50e) whose display is broken. I would still like to use the laptop by connecting it to an external monitor and keyboard/mouse. This is what I did:


[LIST=1]
[*]Removed the hard disk from the broken IBM
[*]Put the hard disk in the working IBM and installed 10.04 on it.
[*]It booted fine and I installed many packages and stuff.
[*]I put the hard disk back into the broken display IBM thinking I could use it by connecting it to an external monitor that I own.
[/LIST]
Well, it turns out that while booting, the display shows up but because the display shifts from the VGA display to the primary display mid-boot, the laptop does not boot. Is there a way in which I can force the laptop to not use its primary display while booting. I looked at Randr and also grub.conf settings but nothing seemed to work. Please help!

---

### Post by ToasterThief on 2010-06-14
You need to change primary display to external in your BIOS setup.

---

