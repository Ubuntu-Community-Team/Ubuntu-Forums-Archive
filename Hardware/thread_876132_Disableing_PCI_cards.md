---
title: "Disableing PCI cards"
date: 2008-07-31
forum: Hardware
---

### Post by ssm360 on 2008-07-31
I have a BFG ageia physX card witch seems 2 b running with the blue light on the card witch is off when not in use in windows when using hardy, I was wondering is there a way 2 disable this card in Ubuntu to save on power consumption.

Any help is appreciated.

Thanks

---

### Post by pytheas22 on 2008-07-31
You should be able to do it by removing the module that drives it.  What is the output of:
```

lspci
```

With that we can figure out which module to disable.

---

### Post by ssm360 on 2008-07-31
```
02:08.0 Class ff00: AGEIA Technologies, Inc. Physics Processing Unit [PhysX]
```

if u need the rest of the list i can add it

Thanks

---

### Post by pytheas22 on 2008-07-31
I'm having trouble figuring it out...could you please post the output of:

```
lshw
```

as well?  That should pinpoint better which module the ppu is using.

---

### Post by ssm360 on 2008-08-01
```
 *-generic UNCLAIMED
             product: Physics Processing Unit [PhysX]
             vendor: AGEIA Technologies, Inc.
             physical id: 8
             bus info: pci@0000:02:08.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=32
```

if u need the rest of the list let me know, thanks

---

### Post by pytheas22 on 2008-08-01
Interesting; it doesn't seem to think that there's any driver controlling the card, so I'm not sure why the light is on.  Do you ever use the device in Ubuntu?

Also, just in case (should have thought of this earlier), did you check your BIOS to make sure there's not an option to disable the device?  Or do you have an option to disable specific PCI slots?

Otherwise, I'm thinking that there must be some way to tell Linux to ignore the PCI bus that the PPU is using; I'll do some research and see what I find.

---

### Post by ssm360 on 2008-08-01
soz i probably should of said there is no Linux driver 4 it, well i don't think there is a Linux driver 4 it, i don't really want 2 disable it in the BIOS, i just don't want the hassle of enabling it and disabling it all the time when i'm playing games in windows.

But if disabling it in the BIOS is the only way i would have 2 put up with it, lol lol

Thanks

---

### Post by pytheas22 on 2008-08-01
At the grub boot menu, press 'e' and add to the boot line:
```

pci=noacpi
```

then press enter to start booting.  Is the light still on?

---

### Post by ssm360 on 2008-08-03
that command had no change

thanks

---

### Post by pytheas22 on 2008-08-03
In that case, I don't know...I guess I have to say that I'm out of suggestions (although I was probably not best qualified for this question anyway).  My only other thought was to tell Linux to ignore a device based on IRQ number, but I googled for a while and couldn't figure out how to do that (I'd be shocked if there's really no way, but I couldn't find it whatever it is).  So sorry, but I guess disabling it in BIOS is the only option for shutting it off completely that I can give you.  Maybe if you start a new thread someone else could help better...

---

### Post by ssm360 on 2008-08-04
Thanks for trying anyway

---

