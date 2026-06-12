---
title: "LaCie USB 3 drives causing Ubuntu to crash"
date: 2015-03-17
forum: Hardware
---

### Post by Bleakley on 2015-03-17
Hi,

I'm having problems with my LaCie USB 3.0 external drives. When I plug them into any USB 3.0 port on my machine 1 of two things happens, almost immediately

[LIST=1]
[*=2]The monitor goes blank and I have to restart my computer because there is no way to get the computer and monitor talking again 
[*=2]I get some sort of kernel panic or something - 'bad: scheduling from the idle thread!' and a bunch of text I don't really understand - see pic. 
[/LIST]

This only happens with LaCie drives and only when I'm plugging into a USB 3.0 port. 

I'm running 14.10, Intel i7, Gallium 0.4 on NVA8

Anyone else have these issues or know a way to fix it?

Thanks!

[ATTACH=CONFIG]260690[/ATTACH]

---

### Post by dino99 on 2015-03-17
At start-up push the delete button and enter the bios.

Go to the advanced menu. Go to usb configuration and change the xHCI mode from enabled to disabled.
Set the EHCI Hand-off to enabled. 
Legacy usb support enabled

Safe changes and reboot. 

See if it works now.

---

### Post by dino99 on 2015-03-17
Looks like that issue has been fixed with the latest kernel 4 rc3

Probably this thread discussed a similar problem - [http://thread.gmane.org/gmane.linux.usb.general/110579/focus=114763](http://thread.gmane.org/gmane.linux.usb.general/110579/focus=114763)
And if my assumption correct then fix is already committed in kernel v4.0rc3 and to be applied to stable 3.18 and 3.19 (hopefully) - [http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/drivers/usb/host?id=27082e2654dc148078b0abdfc3c8e5ccbde0ebfa](http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/drivers/usb/host?id=27082e2654dc148078b0abdfc3c8e5ccbde0ebfa)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

note: you need to download 3 deb into an empty folder: headers...all.deb, image...deb, headers....deb (i386 or amd64 as of your installation is)
         then from that folder: sudo dpkg -i *

---

### Post by Bleakley on 2015-03-17
cool! Thank you!!! I will try these and hope it works.

cheers.

---

### Post by Bleakley on 2015-03-17
hmmm. I can't locate a xHCI mode or an EHCI Hand-off in my BIOS...

---

### Post by Bleakley on 2015-03-18
I did what you suggested as best I could but it didn't solve the problem. I' now getting an error that says "ERROR Transfer event for disabled endpoint or incorrect stream ring"

The computer isn't crashing as often but the drives still wont' be recognized thru USB 3.0 ports.

---

### Post by dino99 on 2015-03-18
about the hardware:
- is the mobo with a usb3 or usb2 port ?
- or is it an usb3 card addon ?
- do you know its chipset ? (sudo lspci && sudo lsusb)

---

