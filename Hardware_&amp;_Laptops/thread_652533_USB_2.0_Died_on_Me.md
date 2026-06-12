---
title: "USB 2.0 Died on Me"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by bennybobw on 2007-12-28
I was going to backup everything and install 7.10 only to run into USB problems (never had them before). I tried three of my dad's drives and thought it was a problem with them. Then I tried plugging in a Kingston thumbdrive and a Sandisk Sansa **that I always use on this computer**, only to discover they are not working either.

**Basic info:**
> IBM Thinkpad T41
Ubuntu Fiesty
2.6.20-16-generic (I've tried booting several previously installed kernels with no luck) 

**dmesg output:**
> [  582.220000] usb 4-3: new high speed USB device using ehci_hcd and address 5
[  585.748000] usb 4-3: new high speed USB device using ehci_hcd and address 18
[  586.756000] usb 4-3: new high speed USB device using ehci_hcd and address 21
[  589.276000] usb 4-3: new high speed USB device using ehci_hcd and address 30
[  589.536000] ehci_hcd 0000:00:1d.7: port 3 reset error -110
[  589.536000] hub 4-0:1.0: hub_port_status failed (err = -32)
(Rinse and repeat...)

I've checked out a bunch of threads on this. Namely these ones:
**Most important: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/8874](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/8874)**6
Others: 
[LIST]
[*][http://ubuntuforums.org/archive/index.php/t-482989.html](http://ubuntuforums.org/archive/index.php/t-482989.html)
[*][https://answers.launchpad.net/ubuntu/+question/4272](https://answers.launchpad.net/ubuntu/+question/4272)
[*][https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/23346](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/23346)
[*][https://bugs.launchpad.net/ubuntu/+bug/18877](https://bugs.launchpad.net/ubuntu/+bug/18877)
[*][https://bugzilla.redhat.com/show_bug.cgi?id=213411](https://bugzilla.redhat.com/show_bug.cgi?id=213411)
[/LIST]

After running sudo modprobe -r ehci_hcd
**dmesg:**
> [ 1247.012000] ehci_hcd 0000:00:1d.7: USB bus 4 deregistered
[ 1247.012000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[ 1257.168000] usb 2-2: new full speed USB device using uhci_hcd and address 4
[ 1257.332000] usb 2-2: configuration #1 chosen from 1 choice
[ 1257.544000] usbcore: registered new interface driver libusual
[ 1257.560000] Initializing USB Mass Storage driver...
[ 1257.560000] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1257.560000] usbcore: registered new interface driver usb-storage
[ 1257.560000] USB Mass Storage support registered.
[ 1257.560000] usb-storage: device found at 4
[ 1257.560000] usb-storage: waiting for device to settle before scanning
[ 1262.560000] usb-storage: device scan complete
[ 1262.564000] scsi 2:0:0:0: Direct-Access     WDC WD12 00UE-00KVT0      0000 PQ: 0 ANSI: 0
[ 1262.568000] SCSI device sdb: 234441648 512-byte hdwr sectors (120034 MB)
[ 1262.572000] sdb: Write Protect is off
[ 1262.572000] sdb: Mode Sense: 27 00 00 00
[ 1262.572000] sdb: assuming drive cache: write through
[ 1262.580000] SCSI device sdb: 234441648 512-byte hdwr sectors (120034 MB)
[ 1262.584000] sdb: Write Protect is off
[ 1262.584000] sdb: Mode Sense: 27 00 00 00
[ 1262.584000] sdb: assuming drive cache: write through
[ 1262.584000]  sdb: sdb1
[ 1262.632000] sd 2:0:0:0: Attached scsi disk sdb
[ 1262.632000] sd 2:0:0:0: Attached scsi generic sg2 type 0

***But I really don't want to turn off USB 2.0*** because I have to back up a bunch of stuff. I tried turning off autosuspend and I get:
> sudo echo -n -1 > /sys/module/usbcore/parameters/autosuspend
bash: /sys/module/usbcore/parameters/autosuspend: Permission denied

According to [this Redhat thread]("https://bugzilla.redhat.com/show_bug.cgi?id=213411"), changing the order of the usb modules in /sbin/mkinitrd helped, but I don't see that on Ubuntu.

Am I screwed?

---

### Post by tgalati4 on 2007-12-28
Check the power settings in the BIOS.  Try "Allow USB to wake from suspend".  There may have been a change that is causing a change in USB behavior.

---

### Post by bennybobw on 2007-12-28
I checked in the power settings in the BIOS, but I didn't see any settings like that. Any other suggestions? Is there a way to check what upgrades / changes I've made on the system? That might help to track it down...?

---

### Post by tgalati4 on 2007-12-29
It's quite possible that the USB controller on the motherboard has taken a crap.  Because several devices get plugged into USB, and they all draw current, it's possible that the chip overheated and took a dump.  The chip still communicates with the CPU and registers properly, but it's not sending data.  There are 4 pins on USB:  The outside 2 are ground and +5V, the inner pair are a balanced data signal (which usually shows ~2VAC on a meter).  If you lose the 5V supply or if the data pair receiver/transmitter is blown then USB will not work obviously.

Try a Live CD and boot from that.  Then plug in a USB device that you KNOW works properly.  If this test fails, then you can be reasonably sure that the USB port is bad.  I assume that none of the USB ports work?  If you have 2 ports and neither works, then the USB controller hub could be bad.  If only one port is bad, then it could be a loose connector (cold-solder junction) from too much flexing of the socket.  Any exterior case damage from dropping?

---

### Post by bennybobw on 2007-12-29
After reading your post and searching in other forums, I'm 99% sure it's a hardware problem, not Ubuntu. I'm going to buy a pcmcia usb card and try that. I hope my system board is not dying...

Thanks tgalati4

---

