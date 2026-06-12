---
title: "USB Mouse problem with Fujitsu Siemens Amilo L series laptop"
date: 2006-07-01
forum: Hardware &amp; Laptops
---

### Post by Ber3i on 2006-07-01
Hi All!

I have a big problem with my Fujitsu Siemens Amilo L series laptop.:( 
When i install the Ubuntu 6.06, anything was good, but only a mouse wasn't working correctly. The USB mouse is slowly, and the movement is staccato.
:confused: 

Here my USB devices:

Bus 004 Device 001: ID 0000:0000 
Bus 001 Device 003: ID 1267:0201 Logic3 / SpectraVideo plc A4Tech SWOP-3 Mouse 
Bus 001 Device 001: ID 0000:0000 
Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 001: ID 0000:0000

The touchpad is working fine, but I want to use my USB mouse:D 

I tried modify the xorg.conf, but nothing happens.
Anybody can help me???
Please. Thanks.

---

### Post by Hellkeepa on 2006-07-01
HELLo!

Please read the following thread, as this may be a side-effect of the bug discussed in there:
[http://ubuntuforums.org/showthread.php?t=204100](http://ubuntuforums.org/showthread.php?t=204100)

No guarantees though, just a suggestion from a fellow Amilo owner. ;-)

Happy codin'!

---

### Post by Ber3i on 2006-07-02
My problem didn't repair, the mouse is still bad.

Anyone else??? Please help me:-s 

Does nobody use Amilo laptops? Does nobody see this Bug? Is it possible?

---

### Post by Eversmann on 2006-07-02
I own an amilo l1310g. No problem with the USB mouse, just the damn bug using fglrx that disable all the usb ports after a while.

Try to boot with irqpoll on the kernel load line on grub and see how it goes. If it resolves the problem, it's an irq problem.

---

### Post by Ber3i on 2006-07-05
THX THX THX

Thanx for all!

This irqpoll is working, and my mouse is too!

THXTHX

---

### Post by Eversmann on 2006-07-05
Glad that worked but... that's not really a solution. irq polling while reduce the computer performance. Search on the forum about irq workarounds on kernel and irq, and read what dmesg says about irq.

---

### Post by Stings on 2006-11-20
I have the same problem with my amilo. However it isnt only USB mouse which is awefully slow. Moving images from a USB pen with a rate of 5mb/min isnt funny :)

Im very new with Linux and would love some newb guidance if possible.

If its an IRQ conflict. What can i do to solve it?
I am running Ubuntu 6.06
Stings.

---

