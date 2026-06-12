---
title: "BusyBox v1.10.2 USB Stick"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by vahnx on 2009-04-23
This has been happening to me ever since they put the "Make USB Stick" option in Ubuntu. No matter which USB stick I use, after I reboot into the USB stick it passes the loading screen then I get:

```
BusyBox v1.10.2
(initramfs)
```

then an ash prompt.

I've installed Ubuntu on two or three different USB sticks with as I said, each Ubuntu that had this option and same BusyBox result. Does anyone know why this happens and has anyone ever succeeded in making a bootable Ubuntu stick?

---

### Post by Tarmael on 2009-04-24
I have the same problem.

I've tried the following boot parameters:

pnpbios=off
pci=nomsi (worked for me when I had the same problem on my lappy for 8.04)
noapic
nolapic
apci=noirq

any thoughts?

Should I get out a cd and burn it to that and try that? Should I wait till Fedora 11 comes out? :P

---

### Post by bolucpap on 2009-04-24
I worked around this (sort of) by waiting until the busybox prompt, removing the USB stick (mine was an external harddisk, actuall), reinserting it and waiting for the computer to recognize the device (there is a notification about assuming write cache or some such, or you can "ls -l /dev/disk/by-uuid" till you start seeing your usb-stick. then I typed exit at the prompt and voila, booted as if nothing was wrong.

---

### Post by vahnx on 2009-05-05
Hm, does everyone have this problem that installs to USB? I've yet to put Ubuntu back on USB but if there's a method that permanently fixes this then I'm all for it. If I do decide to put it back on a USB though, I'll try the above method.

---

### Post by vahnx on 2009-05-14
I tried unplugging and plugging it back in, and while it started to do something, just went back to BusyBox prompt (EDIT:Forgot to type exit). I also noticed during boot, my HDD light was flickering twice then off, twice then off, etc. and my USB Light was not flickeirng at all.

---

