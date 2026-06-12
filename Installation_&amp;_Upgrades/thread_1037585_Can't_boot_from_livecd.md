---
title: "Can't boot from livecd"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by Jarn on 2009-01-11
I am trying to install 8.10 and when I put in the live cd and run it, it loads up to the initial menu and I can select my language but then no matter what option I click on the menu (install, check cd for defects, etc.) nothing happens and after a few minutes I get a disk I/O error and it tells me to restart. I have verified that the problem is not the disk (the md5 is correct on the downloaded iso and also I can boot from the disk in virtualization software).

This is a Dell XPS M1530 with an Intel C2D T8300, 4 gigs of RAM, and an nVidia Geforce 8600m gt.

---

### Post by andresmh on 2009-01-11
Weird. I would try burning th CD again, maybe your CD reader is picky sometimes? I've read others recommending not to use CD-RW nor DVDs. Also, maybe try one of the alternative  modes for starting the LiveCD in particular the one with safe graphics. If all that doesn't work you could try booting from a LiveCD stored on a USB.

---

### Post by Jarn on 2009-01-11
I have burned the iso twice at very low burn speeds (I used either 2x or 4x, forget which) and both produce the same error. One was burned onto a DVD and one onto a CD-R. No options work in the LiveCD, no matter what I select this happens the minute I hit enter. How would I store it on a USB drive and boot from that?

---

### Post by kranny on 2009-01-11
--->Clean the lens on the optical drive, and retry
--->Try booting the Live CD on another computer

---

### Post by Jarn on 2009-01-11
I don't think I can get to the lens. It's a slot-loading drive on a laptop. I have already verified that the problem is not the disc.

---

### Post by kranny on 2009-01-11
Try the following kernel options
noapic
irqpoll
acpi=noirq
all_generic_ide

---

### Post by Jarn on 2009-01-11
I assume that I would put those as options (by hitting F6) when booting?

---

### Post by kranny on 2009-01-11
> **Jarn said:**
> I assume that I would put those as options (by hitting F6) when booting?
Yes press f6( It says press f6 for other options)
If you need to pass all_generic_ide as a kernel parameter,just type it after your kernel line like this

```
kernel /vmlinuz-2.6.22-14-386 root=UUID=... ro quiet splash all_generic_ide
```

---

### Post by andresmh on 2009-01-11
For using a USB stick:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
I personally tried this and it worked:
[https://help.ubuntu.com/community/LiveCD/Persistence?action=show&redirect=LiveCDPersistence](https://help.ubuntu.com/community/LiveCD/Persistence?action=show&redirect=LiveCDPersistence)

---

