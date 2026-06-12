---
title: "keyboard not working when liveCD kernel is loaded"
date: 2008-06-30
forum: Hardware
---

### Post by RancidAmoeba on 2008-06-30
The machine is an LG E200, and the problem is the same for the regular as well as alternate CDs.

The machine boots into the bootloader, keyboard working fine. As soon as the kernel gets loaded, the keyboard completely stops working (yes, even cps lock and the magic sysrq).

The usual suspects (noapic, nolapic, pci=bios, toggling the enable legacy usb in the bios settings) don't make any difference.

I would post an lspci output if I could, obviously. :)

Any clues or ideas on narrowing down the problem? Any supplementary information I could be providing? Thank you in advance!

(NB: knoppix doesn't see the keyboard either...)

---

### Post by RancidAmoeba on 2008-07-01
In case anyone runs into this one, you need to edit your kernel boot parameters. After the -- at the end, add the following:

i8042.nopnp=1 i8042.dumbkbd=1

---

### Post by devraj on 2008-09-02
we have tried the above suggested nopnp, dumbkbd

this activtes the keyboard and fedora core gets installed, however it is not in the graphical mode, we get linux in the text mode only

even startx does not give us graphical linux

how do we solve this problem for LG E200

---

### Post by usualsuspect00 on 2008-11-08
niiice I'm stuck with the keyboard problem so I'll try this... for the X not starting, just plug another screen into the laptop, the other screen will show X.

install all the graphical drivers suggested, reboot and you should not need the other screen anymore... 

Weird, but it worked on my lg e300

---

### Post by usualsuspect00 on 2008-11-08
> **usualsuspect00 said:**
> niiice I'm stuck with the keyboard problem so I'll try this... for the X not starting, just plug another screen into the laptop, the other screen will show X.

install all the graphical drivers suggested, reboot and you should not need the other screen anymore... 

Weird, but it worked on my lg e300

no luck for me... no trick will work... I,m stuck with my $#@$#@ usb keyboard... so much for a light traveling laptop...

---

### Post by putonghua73 on 2008-11-09
N/m.

---

