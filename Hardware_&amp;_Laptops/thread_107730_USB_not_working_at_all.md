---
title: "USB not working at all"
date: 2005-12-23
forum: Hardware &amp; Laptops
---

### Post by kingzasz on 2005-12-23
I've never gotten any USB devices working in Ubuntu.

I've my iPod, and USB Stick, and my USB mouse.

None of them are even recognized.

I really need USB to work.

How do I fix this problem?  Where do I start?  

Thanks, and have a great day,
Brian

---

### Post by randy on 2005-12-24
Have you looked at the output of dmesg and lspci to see if your usb controller is detected and the driver for it is being loaded correctly?

---

### Post by kingzasz on 2005-12-24
This is dmesg (I think the USB stick was plugged in when I booted):

> [4356204.051000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4356204.051000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=153516000, sector=153515959
[4356204.051000] ide: failed opcode was: unknown
[4356204.051000] end_request: I/O error, dev hda, sector 153515959
[4356218.788000] lp0: ECP mode
[4356219.390000] lp0: ECP mode
[4356224.431000] lp0: ECP mode
[4364930.789000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).


This is lspci

> 
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0c.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc Radeon RV250 [Radeon 9000] (Secondary) (rev 01)


---

### Post by nystire on 2005-12-24
I don't know too much about the USB, but that bit from your dmsg about the read error on your hard drive may be a sign that you should back up rather quickly. Is a new hard drive an option for you?

---

### Post by kingzasz on 2005-12-26
I figured it out....

USB was disabled in the BIOS for some reason....

I thought that I had USB working in Windows so I never checked that until now. I guess I was wrong. :D

---

### Post by erikringmar on 2006-01-23
Hi there,

I have a similar issue with the USB key.  dmesg gives me:

[4358567.643000] usb 1-1: USB disconnect, address 2
[4358571.559000] usb 1-1: new full speed USB device using uhci_hcd and address 3

What can I do to reconnect the USB?

cheers,

Erik

---

