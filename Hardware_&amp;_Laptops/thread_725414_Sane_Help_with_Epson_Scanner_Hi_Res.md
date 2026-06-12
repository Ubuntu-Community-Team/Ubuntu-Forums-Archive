---
title: "Sane Help with Epson Scanner Hi Res"
date: 2008-03-15
forum: Hardware &amp; Laptops
---

### Post by bennybobw on 2008-03-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/47024](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/47024) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm trying to get my scanner to work. It's an Epson Stylus CX4200
I tried the ubuntu version of xsane and then discovered this bug:
[XSane Backend Bug -- Can't Scan at Hi Res]("https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/47024")

So I uninstalled Sane and XSane, downloaded the source, and applied the patch here:
[https://alioth.debian.org/tracker/index.php?func=detail&aid=303493&group_id=30186&atid=410366]("https://alioth.debian.org/tracker/index.php?func=detail&aid=303493&group_id=30186&atid=410366")

Everything compiled fine, but now I can't get xsane to recognized my scanner.
Here's what dmesg tells me:
[  423.972000] usb 5-3: new high speed USB device using ehci_hcd and address 5
[  424.108000] usb 5-3: configuration #1 chosen from 1 choice
[  424.112000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 5 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0820

[  720.396000] ppdev0: registered pardevice
[  720.396000] ppdev0: unregistered pardevice
[  720.412000] usb 5-3: usbfs: interface 1 claimed by usblp while 'xsane' sets config #1
[  721.420000] usb 5-3: usbfs: interface 0 claimed by usbfs while 'xsane' sets config #1

it doesn't work if I use sudo xsane either....
Keep in mind that I only installed sane-backends and xsane. Ubuntu uninstalled a bunch of stuff when I uninstalled libsane. Is there something else that I need to do? Thanks for your help.

---

### Post by teaker1s on 2008-03-21
looks like epkowa.conf needs editing. or save your self a lot of grief and get epson iscan and driver from [here]("http://avasys.jp/hp/menu000000500/hpg000000442.htm") and if no deb, then install  rpm with alien.

some of the later drivers from epson will edit epkowa.conf for you when installed:popcorn:

---

### Post by bennybobw on 2008-04-13
So I installed Iscan 2.11 from avasys. When I try to start Iscan, i get the error

```
Could not send command to scanner. Check the scanner's status.
```

Here's what I've tried to correct this:
[LIST=1]
[*]Added epkowa to /etc/sane.d/dll.conf
[*]Commented out /etd/sane.d/epson.conf
[*]Added usb 0x04B8 0x0820 to /etc/sane.d/epkowa.conf
[/LIST]

Dmesg gives me:
```
[  652.612000] usb 5-3: new high speed USB device using ehci_hcd and address 4
[  652.748000] usb 5-3: configuration #1 chosen from 1 choice
[  652.752000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0820


```

sane-find-scanner returns:
```
found USB scanner (vendor=0x04b8 [EPSON], product=0x0820 [USB2.0 MFP(Hi-Speed)]) at libusb:005:003
```

But nothing from scanimage -L
```
No scanners were identified.
```

and Dmesg says:
```
[  669.648000] ppdev0: registered pardevice
[  669.648000] ppdev0: unregistered pardevice
```

How can I make it use the right driver?? Also, I originally installed sane, then removed it, then compiled from source, and then installed from Synaptic. If I completely uninstall and reinstall, will that have any effect?

Thanks.

---

### Post by teaker1s on 2008-04-15
depending on how you installed iscan, if with alien, it should have created a . deb package.
Safest way is to use synaptic to find and remove it

---

