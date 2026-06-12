---
title: "Can't print to USB with Feisty"
date: 2007-05-25
forum: Hardware &amp; Laptops
---

### Post by silver-fox on 2007-05-25
I have a Canon ip4200 but not sure the printer model is significant, it seems to be a USB problem. It works fine in WinXP from the same PC and was working fine in SuSE 10.0 until I decided to try Kubuntu 7.04 for various reasons, including the size of the supported repository.

Using CUPS, the printer status shows as "processing, accepting jobs, published". When I try to print a test page, it goes to "printing... 8% complete" or something like that, meanwhile the printer is doing precisely nothing.

I tried printing from a PCLinuxOS live CD just out of interest - it worked.

lsusb shows:
Bus 004 Device 012: ID 04a9:10a2 Canon, Inc.

I've attached dmesg, messages and cups/error_log. I'm just running from the live cd until I decide whether to install it again, that's if I can fix the printing problem.

I'm using the Turboprint driver which I bought due to it being far better than Canon's offering but again, I'm not sure that's significant. I tried them and they said everything looked fine in Turboprint-land but CUPS doesn't seem able to access the port.

In CUPS, when I go to install the printer and choose "local", the printer is detected at "usb://Canon/iP4200". I've tried pointing it at /dev/usblp0 instead, no difference.

ls -l /dev/usb* shows this for usblp0:
crw-rw---- 1 root lp   180,  0 2007-05-25 17:48 /dev/usblp0

Thanks for your help!

Silver-fox

---

### Post by silver-fox on 2007-05-30
Quick update... I plugged the printer into a hub running from a port on the main board instead of using a port on my old PCI card, that fixed it. I suppose I should be using a USB 2.0 port anyway.

silver-fox

---

