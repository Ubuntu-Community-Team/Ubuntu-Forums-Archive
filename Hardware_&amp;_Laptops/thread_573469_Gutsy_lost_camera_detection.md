---
title: "Gutsy: lost camera detection"
date: 2007-10-11
forum: Hardware &amp; Laptops
---

### Post by Capone on 2007-10-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/151684](https://bugs.launchpad.net/ubuntu/+bug/151684) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Oct 10 12:14:58 mustang kernel: [  112.591673] usb 5-7: new high speed USB device using ehci_hcd and address 57
Oct 10 12:14:58 mustang kernel: [  112.747608] usb 5-7: configuration #1 chosen from 1 choice
Oct 10 12:14:58 mustang kernel: [  112.748107] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(VC0321)
Oct 10 12:14:58 mustang kernel: [  112.956195] usb 5-7: USB disconnect, address 57
Oct 10 12:14:58 mustang kernel: [  112.956213] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: Failed to configure camera
Oct 10 12:14:58 mustang kernel: [  112.956224] gspca: probe of 5-7:1.0 failed with error -5

It goes on until it reaches 97:
Oct 10 12:15:09 mustang kernel: [  218.902344] usb 5-7: configuration #1 chosen from 1 choice
Oct 10 12:15:09 mustang kernel: [  219.065945] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(VC0321)
Oct 10 12:15:09 mustang kernel: [  219.422641] usbcore: registered new interface driver gspca
Oct 10 12:15:09 mustang kernel: [  219.422709] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered


Yet, the webcam ain't available anymore. Anyone has a clue about this?

---

