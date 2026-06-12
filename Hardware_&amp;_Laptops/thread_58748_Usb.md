---
title: "Usb"
date: 2005-08-21
forum: Hardware &amp; Laptops
---

### Post by Pouet on 2005-08-21
Hello,

My USB printer and my USB modem are not correctly detected by Hoary. I just get dmesg messages like :

    usb1-1: new full speed USB device using uhci_hcd and address 8
    usb1-1: khubd timed out on ep0in
    usb1-1: khubd timed out on ep0out
    usb1-1: device not accepting address 18, error -110

I get them, with an increasing address value, each time I disconnect and reconnect this devices. My USB is however working. I have just updated the BIOS of my motherboard. What can I do ?

---

### Post by nad on 2005-08-21
Some USB bios implementations are flaky. After all, this is code written for a particular implementation of chipset and other hardware under often severe time constraints, with often no peer review other than quick engineering checks to determine if it is _acceptable_.

Try tweaking your USB bios settings and the several boot options available to you ( see: [http://www.ibiblio.org/pub/Linux/docs/HOWTO/BootPrompt-HOWTO](http://www.ibiblio.org/pub/Linux/docs/HOWTO/BootPrompt-HOWTO) ).

Sometimes it just won't work the way that you wish it to, if at all.

---

