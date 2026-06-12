---
title: "USB 2.0 PCI cards"
date: 2007-08-23
forum: Hardware &amp; Laptops
---

### Post by Amorphous_Snake on 2007-08-23
My brother got a new iPod and he is fed up with the slow transfer speed on our PC which is quite old and has USB 1.1. There are PCI cards that enable you to use USB 2.0 on your current motherboard. Are they compatible with Linux? Since I started using Linux, I only try to get hardware that is compatible with it. I still use Windows XP though, and I know that the card will work under it (which is where I am going to use it, for iTunes). But the knowledge that it will work with Ubuntu too will be great!

---

### Post by linuxwizard on 2007-08-23
I use a Belkins PCI 2.0 card it has 6 USB ports works with no problems & is detected. I use it with Dapper,Edgy,Feisty Ubuntu/Kubuntu.

---

### Post by w4ett on 2007-08-23
Linux compatible USB 2.0 card  under $7.00

[http://www.buyextras.com/synecchusb20.html?gclid=CInG9t2JjY4CFRwNgQodskrgQw](http://www.buyextras.com/synecchusb20.html?gclid=CInG9t2JjY4CFRwNgQodskrgQw)

There are lots of them out there....best to search your local online vendors.

---

### Post by psyburn on 2007-08-23
Most USB 2.0 PCI-cards are based on either a NEC or VIA chip
Even then most cards are NEC-based
(the Belkin are NEC chipsets)

I have not run into one USB 2.0 PCI-card that hasn't worked yet

However:
the VIA chipset pci cards can conflict with VIA-based motherboards
disabling on-board USB in the mobo bios is all you would need to do
(my IWill KK266 VIA-based board would not even POST until I removed the new VIA card and disabled the on-board USB, reinstalled the card, and x/ubuntu recognized the card)

---

### Post by lungboy on 2007-09-10
I bought a Mercury PCI USB2.0 card (It has a NEC chip set in it) and it was just plug and play on Dapper.

---

### Post by Fingolfin on 2007-10-07
> **Amorphous_Snake said:**
> There are PCI cards that enable you to use USB 2.0 on your current motherboard. Are they compatible with Linux?

Recently purchased Belkin PCI card from Amazon. 
It has 2 external USB 2.0 ports, 2 external firewire 400 ports and 1 internal USB (to connect to the front panel card reader) and one internal firewire (also to connect to the front panel card reader which has usb and firewire ports).
I can also tell the same story, it worked flawlessly with every Ubuntu without me having to configure anything. What can be better than that?

---

### Post by eeried on 2007-10-17
hello, 
I boought two no-name USB2 PCI card (4 ports) for our old PIII et PII. The chipset is apparently VIA. I don't think the mobos are based on Via, but I haven't checked. Here's the command and its output for the PIII:

```
 sudo lshw | grep usb


          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification netboot
        *-usb:0
           *-usbhost
                bus info: usb@1
                logical name: usb1
                capabilities: usb-1.10
        *-usb:1
           *-usbhost
                bus info: usb@2
                logical name: usb2
                capabilities: usb-1.10
              *-usb
                   bus info: usb@2:2
                   capabilities: usb-1.10
        *-usb:2
           *-usbhost
                bus info: usb@4
                logical name: usb4
                capabilities: usb-2.00
        *-usb:3
           *-usbhost
                bus info: usb@3
                logical name: usb3
                capabilities: usb-1.10

```

Threre are two USB1 ports as well.

I'm not too sure about the output. There doesn't seem to be 4 USB2 ports. Should I disable something in the BIOS? 

Your help would be much appreciated! Thanks!

---

### Post by linuxwizard on 2007-10-17
in terminal > lspci         this will list all pci cards

---

### Post by Amorphous_Snake on 2007-10-17
I forgot to reply back!

Thanks a lot to everyone who replied. I got a VIA-based card. It has 4 external USB 2.0 ports and 1 internal (I don't know how I will use it, I don't keep my case open).

Anyway, it works flawlessly with Linux (I have tried it with Ubuntu and openSUSE).

I couldn't find an NEC chipset though. My motherboard is Intel based.

---

### Post by eeried on 2007-10-19
lspci:

```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:0d.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:0d.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:0d.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
00:0f.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
```


However this command gives less detail than the others I pasted earlier.

Can anyone decipher the outputs of my earlier command?

---

### Post by eeried on 2007-11-12
> the VIA chipset pci cards can conflict with VIA-based motherboards
disabling on-board USB in the mobo bios is all you would need to do

the problem is I can't find a way of disabling it in the BIOS (Compaq computer).

Strangely enough, my external HD doesn't work on the USB PCI card but works fine if I plug it to a USB hub...However I used the PCI card on a friend's computer and the HD worked fine -- I'm not sure it worked at USB2 speed but there was no I/O error. that computer has a Via mobo and I didn't have to disable the onboard USB.

So it may be a problem with the PIII mobo itself. Connections may be flaky or something.

```
00:0d.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:0d.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:0d.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
```

Can you explain why the lspci command shows two USB1.1 ports (which is correct) and only one USB2. port while the card has 4 USB ports (and one internal)?

cheers

---

