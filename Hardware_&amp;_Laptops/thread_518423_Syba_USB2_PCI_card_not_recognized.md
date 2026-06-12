---
title: "Syba USB2 PCI card not recognized"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by allanb on 2007-08-05
I have Feisty Fawn on a Dell GX150 and installed the above card to get USB2's as the GX150 only has USB1.1's. The card uses an NEC D720101 chip. There are no drivers for Linux with the card,nor on Syba's site. Connecting an external HDD to the card shows that power is getting through as the drive spins up, but the OS doesn't list (recognise) the drive. I am new at this, and this is the first hardware compatibility issue I have struck.
Can anyone help please?

---

### Post by waryap on 2007-08-19
Hi, I'm having the same problems too. I just bought a Syba USB Cardbus for my Toshiba Satellite 2410. I'm running Feisty and the card does not work. 

Can't seem to find the drivers anywhere. Any ideas???

---

### Post by Tmi on 2007-11-16
I'm having the same problem with my Syba USB2 PCI card.

Just after installing Gutsy I put my USB hard drive in the USB2-card and it worked, but then when I rebooted my computer would freeze on some harddrive related issue for like 3-4 minutes and then start without detecting the USB harddrive. Now nothing happens when I plug the drive in or out.

The last thing written in my /var/log/messages is

Nov 16 14:33:15 ancient kernel: [ 1038.500592] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: event field not found

Anyone have any ideas at what to do?

---

