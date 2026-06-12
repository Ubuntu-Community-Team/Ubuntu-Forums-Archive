---
title: "netgear wg111t  doesn't work after reboot"
date: 2010-10-17
forum: Hardware
---

### Post by Kyh31 on 2010-10-17
Hello,

I am trying to install my netgear wg111t usb wifi stick on ubuntu 10.10 .

I have searched already on the net to find some info.

It seems that i have to use ndiswrapper to install the windows-driver, because there isn't a working linux-driver.

I installed it with the ndiswrapper-gtk.
Afterwards, i was pleased to see a working wifi-connection.

But after rebooting my pc, the excitment was over.
The usb-stick isn't working anymore.

I also read somewhere i have to add ndiswrapper in /etc/modules, which i did, but still nothing.

When i look in /var/log/messages, i see following message when i insert the stick:

[I]Oct 17 18:02:17 vik-pc kernel: [  846.692040] usb 1-7: new high speed USB device using ehci_hcd and address 9
Oct 17 18:02:17 vik-pc kernel: [  846.948165] usb 1-7: reset high speed USB device using ehci_hcd and address 9
Oct 17 18:02:17 vik-pc kernel: [  847.083166] ndiswrapper: driver athfmwdl (,12/05/2003,1.00.001) loaded
Oct 17 18:02:18 vik-pc kernel: [  847.451494] usb 1-7: USB disconnect, address 9
Oct 17 18:02:18 vik-pc kernel: [  847.692031] usb 1-7: new high speed USB device using ehci_hcd and address 10
Oct 17 18:02:18 vik-pc kernel: [  847.948120] usb 1-7: reset high speed USB device using ehci_hcd and address 10
Oct 17 18:02:18 vik-pc kernel: [  848.080566] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
Oct 17 18:02:18 vik-pc kernel: [  848.080571] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
Oct 17 18:02:18 vik-pc kernel: [  848.080579] ndiswrapper (mp_halt:262): device f68b8480 is not initialized - not halting
Oct 17 18:02:18 vik-pc kernel: [  848.080583] ndiswrapper: device eth%d removed
Oct 17 18:02:18 vik-pc kernel: [  848.080606] ndiswrapper: probe of 1-7:1.0 failed with error -22[/I]

Can anybody help me with this please?

Thanks,
Kyh31

---

### Post by chosenbeans on 2010-11-08
Bump ^

---

