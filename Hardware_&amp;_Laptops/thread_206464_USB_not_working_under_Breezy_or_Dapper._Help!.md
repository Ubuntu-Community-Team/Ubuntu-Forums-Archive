---
title: "USB not working under Breezy or Dapper. *Help*!"
date: 2006-06-30
forum: Hardware &amp; Laptops
---

### Post by fmalan on 2006-06-30
Hi

I had Breezy running on a AMD64 X2 4400+ on a Gigabyte NForce 4 platform. With this setup I only had USB1.1 running (No USB2 = annoying).

Since then I had a upgrade to a AMD64 X2 4800+ on a **MSI NForce4** platform (K8N SLi MS-7185). Since this upgrade I have ***no* USB** on any of the ports. USB is enabled in the BIOS. Major problem! I *have* to use USB flash drives.

I already installed the newest NVidia chipset drivers, which only seem to update the sound and networking drivers.

This problem seems to be similar to another thread [http://www.ubuntuforums.org/showthread.php?t=179031](http://www.ubuntuforums.org/showthread.php?t=179031) , but I found no solution offered there.

I **upgraded to** the official **Dapper** release yesterday, in the hope that this would resolve my problem. **The problem persists as before!**

If I run the following before inserting the device ```
 sudo tail -f /var/log/messages
``` I get the following output:

[I]Jun 30 11:13:32 localhost kernel: [ 1175.132307] usb 2-9: new high speed USB device using ehci_hcd and address 3
Jun 30 11:13:37 localhost kernel: [ 1180.368896] usb 2-9: new high speed USB device using ehci_hcd and address 4
Jun 30 11:13:43 localhost kernel: [ 1185.604388] usb 2-9: new high speed USB device using ehci_hcd and address 5
Jun 30 11:13:48 localhost kernel: [ 1190.728059] usb 2-9: new high speed USB device using ehci_hcd and address 6[/I]

Nothing happens from this point onwards. **[COLOR="Red"]Please help![/COLOR]**

---

### Post by fmalan on 2006-07-03
OK - I got it working now... (albeit without any help from the forum).
My linux-knowlegeable friend and I put heads together, and found the problem to be the ehci driver. By removing it with ```
sudo modprobe -r ehci_hcd
``` I got the USB flash drives to work, but only at USB1.1 as with the old mobo.
How can issues like the be allowed to persist!?

---

