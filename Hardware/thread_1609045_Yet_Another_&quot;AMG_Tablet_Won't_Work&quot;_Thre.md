---
title: "Yet Another &quot;AMG Tablet Won't Work&quot; Thread"
date: 2010-10-29
forum: Hardware
---

### Post by Qombat on 2010-10-29
Alright so I have a Medion (AKA Aldi Brand) tablet, apparently this is meant to use the Aiptek drivers gig and not the Wacom ones. So I follow through the steps on [this page here]("https://help.ubuntu.com/community/AiptekTablet"), complete, reboot, and tablet still doesn't work.

Looking at lsusb, I get this:
> Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 04b3:301b IBM Corp. SK-8815 Keyboard
Bus 003 Device 003: ID 04b3:301a IBM Corp. 
Bus 003 Device 002: ID 062a:0001 Creative Labs Notebook Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[B]Bus 002 Device 005: ID 172f:0034 Waltop International Corp. Slim Tablet
[/B]Bus 002 Device 003: ID 1241:1603 Belkin Keyboard
Bus 002 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Waltop? The odd thing is that the Wacom drivers didn't work for me either. This tablet hasn't worked for me since Jaunty, and I'm starting to really need it again. Is there a way I can get this one working?

**Edit:**

I checked the dmesg logs and got this as well:
> [  263.773104] usb 2-2.2: new full speed USB device using uhci_hcd and address 5
[  263.964371] input: WALTOP International Corp. Slim Tablet as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2.2/2-2.2:1.0/input/input8
[  263.964680] generic-usb 0003:172F:0034.0007: input,hidraw3: USB HID v1.10 Mouse [WALTOP International Corp. Slim Tablet] on usb-0000:00:1d.0-2.2/input0

**Edit:**

I didn't realise there was a hardware section. Could a mod move this please?

---

### Post by Iowan on 2010-10-29
Moved to Hardware & Laptops  by request.

---

### Post by Favux on 2010-10-30
Hi Qombat,

Actually in Maverick it looks like you can get your Waltop tablet working with the Wacom driver.  See the [Waltop HOW TO]("http://ubuntuforums.org/showpost.php?p=9966110&postcount=1").  There are also instructions on how to put it on the WizardPen driver in Lucid.

---

### Post by Qombat on 2010-10-30
> **Favux said:**
> Hi Qombat,

Actually in Maverick it looks like you can get your Waltop tablet working with the Wacom driver.  See the [Waltop HOW TO]("http://ubuntuforums.org/showpost.php?p=9966110&postcount=1").  There are also instructions on how to put it on the WizardPen driver in Lucid.

[img]http://www.filemaw.com/file/LC7vdd.png[/img]

---

