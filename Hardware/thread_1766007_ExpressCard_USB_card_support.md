---
title: "ExpressCard USB card support"
date: 2011-05-23
forum: Hardware
---

### Post by kung fu buntu on 2011-05-23
It seems my laptop is suffering from low USB power which is causing problems with an external HDD over USB 2.0
For anyone interested [http://community.wdc.com/t5/My-Passport-for-PC/How-to-eliminate-potential-problems-on-USB-Powered-Drives-and/td-p/118262](http://community.wdc.com/t5/My-Passport-for-PC/How-to-eliminate-potential-problems-on-USB-Powered-Drives-and/td-p/118262)

So my idea is to use a USB Y connector in order to provide the necessary power. But my laptop lacks USB ports, so my idea is to buy a ExpressCard/34 USB card with 2 or 4 slots (would all the slots provide the 5V and 500mA?) and connect the 2 males from the Y connector there and then plug the HDD on the Y female.

I never used an ExpressCard before, so I don't know if the ExpressCard interface in my laptop is supported by linux *nor* what specific card to buy that will be supported by linux.

Both pccardctl ls and pccardctl status show nothing. I would at least except a "no card in host 43453:46gf5" or something like that.
I couldn't find any reference to "express card" or "pcmcia" from lspci or dmesg.



Can I determine if my 2.6.32 kernel supports the ExpressCard interface in my laptop?
What ExpressCard USB cards are supported in 2.6.32?

Thank you for your help.

---

### Post by kung fu buntu on 2011-05-24
So I decided to take a chance and buy a ExpressCard... but it doesn't work :(
When I plug it in the led turns on but nothing shows up in dmseg :(
Again, both pccardctl ls and pccardctl status showed nothing.

How can I know that Linux supports my ExpressCard interface in my laptop?
I suppose it doesn't... so how can I enable it? 

I looked at lspci and lsusb but I couldn't see anything from it :|


The hardware itself seems to be working. When I booted to windows and plugged it in it showed in control panel as an USB device with "PCI bus 6, device 0, function 0"

---

### Post by locutus42 on 2011-06-18
try enabling the ACPI Hot Plug support with this command:

sudo modprobe acpiphp

this is what started getting my eSATA expresscard working on Lucid.
listing dmesg and looking for pcie shows that the hotplug was enabled in the kernel:

dmesg | grep pcie
[    0.274741] pciehp: PCI Express Hot Plug Controller Driver version: 0.4

---

