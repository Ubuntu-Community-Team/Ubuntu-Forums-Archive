---
title: "Keyboard and Mouse Disabled?"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by Termight on 2006-06-04
Hi all,

I've just finished installing Dapper on my laptop, but now my external keyboard and one of the two mice (three if the touchpad counts) has stopped working.  The setup I've got is this:  One mouse (Logitech Mx510) is attached directly to my USB hub.  The non-functional components (MS Intellimouse and 'Illuminator' Series keyboard) are hooked up to a KVM switch (Startech SV211MICRO) with their standard PS/2 cables; the KVM switch is then attached to the USB hub through the use of a PS/2 to USB converter.  That converter is (I think) the problem.  Normally I'd just hook them up to PS/2 ports on the machine (bypassing the converter), but my laptop doesn't have any of that type of port ](*,)

In the device manager the converter shows up as a 'USB to PS2 Adaptor v1.09' and has two 'USB HID Interface' below it with one 'Composite USB PS2 Converter USB to PS2 Adaptop v1.09' beneath each of those entries.

Anyway, I'm pretty sure that this is an Ubuntu error, since both work just fine in Grub and Windows.  Does anyone have an idea what could be causing this?  It worked just fine in Hoary...

---

