---
title: "IEEE 1394 PCMCIA card in laptop"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by AchimRS on 2007-01-11
Hi,
I recentlybought a PCMCIA card for my laptop, to connect my digital-camera via IEEE 1394 (It don't have an USB port :-(

I tried to insert the PCMCIA card into the slot of my IBM T40, but nothing happened.I expected the media toappear under /media/ but nothing is there. If I look to the Device-Manager, I see a "IEEE 1394 Host Controller" with the linux driver ohci1394 from NEC.

What do I need to do, to see the images on my digicam on the Edgy?

Thanks a lot
  Achim

---

### Post by AchimRS on 2007-02-01
Is there nobody out with the same problem or a solution?

Maybe I need to recompile some packages or load some modules??

I checked with lsmod that the following modules are loaded:
  ieee1394              306104  3 raw1394,dv1394,ohci1394
Is'nt that enough???

Thanks
  Achim

---

### Post by fan_ubu on 2007-02-06
download gscunbus to see if it founds your card
also do testlibraw

---

### Post by fan_ubu on 2007-02-06
sorry it is gscanbus:)

---

### Post by koshari on 2007-02-06
you cant just view DV footage like a media file, 

you will need a program such as kino to rip the DV footage from your camera.

i hope your using edgy because kino is broken in dappper.

cheers,

---

### Post by AchimRS on 2007-02-07
> **fan_ubu said:**
> sorry it is gscanbus:)

OK,I installed and used it-this looks good.I see my linux machine in blue and a linked "S400 Kodak". I don't know why "S400" but at least it is a Kodak, that's OK! When I klick on the graphic I see something like:

Physical ID: 0
Link active: Yes

so it looks good so far.

I was not able to start "testlibraw" because I simply don't find it, but is it needed when "gscanbus" output is like shown above?

Furthermore I tried an "dmesg" which shows:

pccard: CardBus card inserted into slot 0
PCI: Enabling device 0000:03:00.0 (0010 -> 0012)
ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[c2000000-c20007ff]  Max Packet=[1024]  IR/IT contexts=[4/4]
ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
ieee1394: Node added: ID:BUS[0-00:1023]  GUID[00e0263d00026d1b]
ieee1394: Host added: ID:BUS[0-01:1023]  GUID[00004c0100000264]

I think this is good as well, but how do I access the jpg files on my photo?
How to mount the firewire device?

Thanks a lot
  Achim

---

### Post by Alfred_McGee on 2007-12-19
PCMCIA firewire/USB 2.0 adapter (Micro Innovations usb755fw): Both the firewire and the USB socket on this card work immediately OTB with Ubuntu 7.04 Feisty.

---

