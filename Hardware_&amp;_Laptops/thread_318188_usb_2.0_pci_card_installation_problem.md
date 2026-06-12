---
title: "usb 2.0 pci card installation problem"
date: 2006-12-13
forum: Hardware &amp; Laptops
---

### Post by underthing on 2006-12-13
Hi folks,

My newly installed USB 2.0 PCI card does not seem to be working. Plugging devices into the ports on the card don't get any sort of response from Ubuntu. I hope someone can steer me in the right direction.

The box is an older P4 with 4 built-in USB 1.1 ports. These are too slow, hence the need for the PCI card upgrade. I am running Dapper with kernel 2.6.15-27-386.

Some debugging info:

Output of *lsmod | grep ehci*

```
ehci_hcd               34184  0
usbcore               130820  6 usb_storage,usbhid,ehci_hcd,ohci_hcd,uhci_hcd

```


*lspci | grep USB*

```

0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)
0000:02:0a.0 USB Controller: NEC Corporation USB (rev 43)
0000:02:0a.1 USB Controller: NEC Corporation USB (rev 43)
0000:02:0a.2 USB Controller: NEC Corporation USB 2.0 (rev 04)

```


*grep Ver /proc/bus/usb/devices*

```
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1

```


These seem to suggest that the card is being detected just fine, and from what I understand I have the correct kernel module in place as well - ehci_hcd.

So what could be the problem? /var/log/messages provides a potential clue:

```


<...snips...>

Dec 13 12:56:48 localhost kernel: [17179570.720000] Initializing Cryptographic API
Dec 13 12:56:48 localhost kernel: [17179570.720000] io scheduler noop registered
Dec 13 12:56:48 localhost kernel: [17179570.720000] io scheduler anticipatory registered
Dec 13 12:56:48 localhost kernel: [17179570.720000] io scheduler deadline registered
Dec 13 12:56:48 localhost kernel: [17179570.720000] io scheduler cfq registered
[B]Dec 13 12:56:48 localhost kernel: [17179570.720000] 0000:02:0a.2 EHCI: unrecognized capability 8e
Dec 13 12:56:48 localhost last message repeated 63 times[/B]
Dec 13 12:56:48 localhost kernel: [17179570.720000] isapnp: Scanning for PnP cards...
Dec 13 12:56:48 localhost kernel: [17179571.072000] isapnp: No Plug & Play device found

<...snips...>


```

...but then a little further down in /var/log/messages it says:

```

Dec 13 12:56:48 localhost kernel: [17179576.920000] ehci_hcd 0000:02:0a.2: EHCI Host Controller
Dec 13 12:56:48 localhost kernel: [17179576.944000] ehci_hcd 0000:02:0a.2: new USB bus registered, assigned bus number 3
Dec 13 12:56:48 localhost kernel: [17179576.944000] ehci_hcd 0000:02:0a.2: irq 193, io mem 0xdfe02000
Dec 13 12:56:48 localhost kernel: [17179576.944000] ehci_hcd 0000:02:0a.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec 13 12:56:48 localhost kernel: [17179576.944000] hub 3-0:1.0: USB hub found
Dec 13 12:56:48 localhost kernel: [17179576.944000] hub 3-0:1.0: 15 ports detected

```


I've tried to provide as much system info as I know how to get. I'm in way over my head here and would be **really grateful** if someone could give a shove in the right direction 8) 

cheers!

---

### Post by underthing on 2006-12-14
Solved.....

I swapped the card over to another PCI slot and the issue disappeared. :twisted:

---

