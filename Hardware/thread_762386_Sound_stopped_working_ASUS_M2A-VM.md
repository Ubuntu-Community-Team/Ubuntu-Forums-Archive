---
title: "Sound stopped working ASUS M2A-VM"
date: 2008-04-22
forum: Hardware
---

### Post by selwynpolit on 2008-04-22
My sound recently stopped working.  I tried cranking up the volume and checked the speakers on another system.  Amorok thinks it is playing very nicely and will allow me to change the volume and everything.

I am using an ASUS M2A-VM board with an AMD 64x2 CPU, 4GB Ram.Kubuntu 7.10 AMD 64 bit.

I've been keeping up with all the patches.  Any suggestions where I should look?  

hwinfo --sound shows the following:

22: PCI 14.2: 0403 Audio device
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4383
  Unique ID: 5Dex.fwPnjOKuURD
  SysFS ID: /devices/pci0000:00/0000:00:14.2
  SysFS BusID: 0000:00:14.2
  Hardware Class: sound
  Model: "ASUSTeK Audio device"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4383 
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8249 
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfe020000-0xfe023fff (rw,non-prefetchable)
  IRQ: 16 (65822 events)
  Module Alias: "pci:v00001002d00004383sv00001043sd00008249bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

No errors as far as I can see.

thanks

Selwyn

---

### Post by selwynpolit on 2008-04-22
OK, I'm a newbie to this Linux.  I found something called kmix.  Click the speaker in the bottom right, then click Mixer - right below the slider.  I turned all the volumes up and clicked the green light below the little plug and presto - sound.  All sound is working great now.

---

