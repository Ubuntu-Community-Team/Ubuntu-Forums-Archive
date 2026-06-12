---
title: "ide-cs hooray! ok now what..."
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by thk on 2008-03-10
So we finally have the ide-cs module in gutsy, which means theoretically I can use the built-in compact flash card reader on my Dell X1. Has anyone gotten this to work? I'm not getting any devices.

dmesg:
[107525.072000] pccard: PCMCIA card inserted into slot 0
[107525.072000] pcmcia: registering new device pcmcia0.0

after sudo modprobe ide-cs, there is nothing new in dmesg

lspcmcia:
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:02:01.0)
Socket 0 Device 0:      [-- no driver --]       (bus ID: 0.0)

lsmod | grep ide_cs:
ide_cs                  9984  0 
ide_core              116804  3 ide_cs,ide_generic,usb_storage
pcmcia                 41388  1 ide_cs
pcmcia_core            40980  4 ide_cs,pcmcia,yenta_socket,rsrc_nonstatic

I tried creating a device node manually, but it gives a "not a valid block device" error when I try to mount it.

Any help appreciated.

---

