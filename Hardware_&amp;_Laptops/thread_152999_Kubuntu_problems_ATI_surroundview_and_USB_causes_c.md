---
title: "Kubuntu problems: ATI surroundview and USB causes crash!"
date: 2006-03-31
forum: Hardware &amp; Laptops
---

### Post by TobyK on 2006-03-31
Hi

I've installed Kubuntu Breezy 32-bit version on my PC, which is a AMD64 with a Sapphire Pure Performance motherboard (ATI chipset). It has a SATA 160Gb hard drive and a PCI Express ATI Radeon X500 card.

Firstly, I cannot get a dual monitor setup working on this machine. I can't load the fglrx driver because X refuses to start up, saying something about not being able to read the V_BIOS. So I have to use the "vesa" driver. The whole reason behind buying the PCI-Express card was to enable a dual monitor setup. In the BIOS, I can enable "surroundview" which enables both the onboard card AND the PCI-Express card. I can see them both if I type "lspci", but setting them up in xorg.conf with the "fglrx" driver doesn't work due to the "V_BIOS" error, and then using the "vesa" driver causes no errors, but only the PCI-E card actually works. ](*,)  Any solutions to this?


Secondly, if I plug a USB flash drive into my PC, it crashes the entire PC! Not immediately. If I look at the output of dmesg, I see messages like "usb device inserted", "trying address 1, device rejected address 1, trying address 2, etc.." and so it goes on until it says something like "ata command XXXX timeout". After this ANY application trying to access my hard drive crashes, until eventually my whole machine freezes and I have to hard-reset ](*,)  Obviously, it's kind of hard for me to copy & paste those messages here... doesn't anyone else have this problem? I'm guessing it has something to do with the fact that it's detecting the USB drive and then it clashes with my SATA drive which is mapped to /dev/sda, and hence crashes the machine.

Any help on these two issues would be greatly appreciated.
Thanks,
Toby.

---

### Post by TobyK on 2006-04-03
Anyone? Any pointers to relevant threads?

---

### Post by TobyK on 2006-04-10
Geez, thanks for the overwhelming response to this rather serious problem! So after much frustration, the solution to the USB flash disk hanging your PC (for those who are having this problem) is to add this to the kernel boot parameters:  irqpoll.

Still no luck trying to get the ATI drivers to load :-(

---

