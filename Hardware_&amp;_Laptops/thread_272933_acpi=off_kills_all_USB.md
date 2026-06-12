---
title: "acpi=off kills all USB"
date: 2006-10-07
forum: Hardware &amp; Laptops
---

### Post by burgermann on 2006-10-07
Hi

Since dapper my USB devices crashed my system. So I've tried with acpi=off in boot string. Now none of my USB devices work, but at least they don't freeze Dapper when plugging them in.

I've had same trouble in Dreamlinux, but the one of the boot options made everything work like a charm. Only I don't remember what the exact boot line command was, but I believe it's something like apci=noapci or like that. Does anyone have any ideas? This is really, really frustrating. If this "bug" doens't get fixed I'm totally screwed.:???:

Sorry for the lack of information, but I have no clue on which informations to give.

---

### Post by burgermann on 2006-10-07
The bootline from Dreamlinux was acpi=off noapic - and it doesn't work in ubuntu. Can anyone give me a clue on what to do?.. isn't there some logs somewhere that can point me in some direction?

I really need help with this one.

---

### Post by fluffnik on 2006-10-07
> **burgermann said:**
> The bootline from Dreamlinux was acpi=off noapic - and it doesn't work in ubuntu. Can anyone give me a clue on what to do?.. isn't there some logs somewhere that can point me in some direction?

I really need help with this one.

"dmesg |less" should let you see what happened during boot, the rest of the logs live in /var/log/, /var/log/messages is  a good place to start.

You may need to add yourself to the "adm" group to read them

---

### Post by Neovos on 2008-02-11
You should check out some of these boot options:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

acpi=off is sort of a blunt tool. You might just need to do something like "acpi=noirq" or "acpi_irq_balance"because it might be conflicting on an irq basis with the usb.

---

