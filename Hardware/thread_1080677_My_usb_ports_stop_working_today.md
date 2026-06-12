---
title: "My usb ports stop working today"
date: 2009-02-25
forum: Hardware
---

### Post by ianstump on 2009-02-25
Hi everyone. I am kinda new to the ubuntu OS, but i have been using it over 2 months. I am actually using the 8.10.
Today my USB ports stopped working, and for me thats a big problem. When i connect them (my ipod or mouse) , sometimes they recieve energy, but are not recognized. ALL HELP IS APPRECIATED.;)

---

### Post by ddrichardson on 2009-02-26
Open a terminal and plug in a device, type
```
dmesg
```
And let us know the last few lines of output - they'll be about EHCI or USB.

---

### Post by eeezzzeee on 2009-02-26
Not to hijack this thread but I just started having the same problem so I figured I would post here rather than starting a new thread about the same issue. The only things I could find in dmesg about usb were

[    3.901180] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[    3.901540] usb usb4: configuration #1 chosen from 1 choice
[    3.901606] hub 4-0:1.0: USB hub found
[    3.901631] hub 4-0:1.0: 2 ports detected

 3.797187] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[    3.797546] usb usb3: configuration #1 chosen from 1 choice
[    3.797613] hub 3-0:1.0: USB hub found
[    3.797634] hub 3-0:1.0: 2 ports detected


[    3.693331] usb usb2: configuration #1 chosen from 1 choice
[    3.693412] hub 2-0:1.0: USB hub found
[    3.693436] hub 2-0:1.0: 2 ports detected

[    3.505842] usbcore: registered new interface driver usbfs
[    3.505892] usbcore: registered new interface driver hub
[    3.511101] usbcore: registered new device driver usb

[    3.537450] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    3.537472] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.537478] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.537594] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.541528] ehci_hcd 0000:00:1d.7: debug port 1
[    3.541537] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    3.541553] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf6effc00
[    3.545588] USB Universal Host Controller Interface driver v3.0
[    3.588067] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.588381] usb usb1: configuration #1 chosen from 1 choice
[    3.588446] hub 1-0:1.0: USB hub found
[    3.588471] hub 1-0:1.0: 6 ports detected


I don't know what any of that means of if it will help, but that is all I could find with that command.

---

### Post by bjchip on 2009-04-08
I just started running into this as well.   They work for a while, but if I walk away and do something else they disappear.   No power to the mouse.  No power to the keyboard.  I have configured the bios to NOT try to save energy and it still happened.  I don't think this is strictly a USB problem. 

I have a vmware server 2 on the system.  Wondering if there is an interaction as it holds the focus for itself for long periods.  

I told the preferences to avoid mucking about with power settings.  

I can't even ssh into the box.  This tells me it is not JUST the usb ports that have decided to clam up.  When I reboot this time I am going to have to scour the logs for bread-crumbs.  

I have about decided to simply avoid the next-release-after-an-LTS release.  :-)    This is getting better, but it isn't yet good.   

BJ

---

