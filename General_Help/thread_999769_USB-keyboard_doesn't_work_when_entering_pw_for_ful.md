---
title: "USB-keyboard doesn't work when entering pw for fully encrypted disk"
date: 2008-12-02
forum: General Help
---

### Post by re_dile on 2008-12-02
In order to use Ubuntu at all on my computer I have to use "pci=nomsi irqpoll noapic acpi=off" as boot options, otherwise Ubuntu freezes at random times when I've loged in.

This has worked well for about a month, but now when Ubuntu prompts me for the pass phrase (pw) for the fully encrypted disc my keyboard won't work. It works in BIOS and I can use "ESC" to enter the GRUB menu, but not when I need to enter the pw.

If I remove "acpi=nomsi" boot option, the USB-keyboard works fine all the way, but then my computer freezes as mentioned above... 

It's no solution to use a PS/2 keyboard and mouse since I use a USB KVM-switch to split my keyboard and mouse between two computers.

Why has this problem suddenly arised?

---

### Post by re_dile on 2008-12-04
nobody experiencing the same problem or having any suggestion?

---

### Post by re_dile on 2008-12-06
OH JOY!!!

It appears I've set the PnP option in BIOS to Yes, and that screwed up everything concerning USB (at least in Linux). After changing PnP to No in BIOS, I've been able to use my USB-keyboard as usual to enter the password to the disk-encrytption.

---

### Post by jame86 on 2008-12-06
Was just about to suggest that for you, would have replied quicker but have been away!

Hope your Ubuntu fun can start from here!

Jame86

---

