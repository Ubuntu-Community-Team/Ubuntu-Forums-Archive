---
title: "Lubuntu 18.04 dual monitor ati radeon hd 6450"
date: 2020-04-09
forum: Hardware
---

### Post by gxxg on 2020-04-09
HI, i have a computer intel i5 with ati radeon hd 6450, LUBUNTU 18.04, i have installed arandr, and i have plugged in the second monitor dell 19",  with vga cable and dvi adapter, but i cannot absolutely find the second monitor. how can i fix it? thanks a lot

  *-display
                description: VGA compatible controller
                product: Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:34 memory:e0000000-efffffff memory:f7e20000-f7e3ffff ioport:e000(size=256)

---

### Post by guiverc on 2020-04-09
I've had problems with VGA-DVI converters before, are you using a digital or analog signal?, and does your converter cope with analog/digital or both? (passive DVI-to-VGA converters for example won't work with digital signals). 

 DVI plugs can provide a clue as to the type of signal they're intended for (ie. pin arrangement).

I'll provide [https://en.wikipedia.org/wiki/Digital_Visual_Interface](https://en.wikipedia.org/wiki/Digital_Visual_Interface) , but I wonder if you've made assumptions without doing the homework needed to validate it'll work.

---

### Post by gxxg on 2020-04-15
thank you, so if i will use a cable is possible to fix it? i will try... my converter is this one... [https://www.ebay.it/itm/Connettore-Adattatore-Cavi-DVI-D-24-1-Pin-A-VGA-Fem/222304162724?ssPageName=STRK%3AMEBIDX%3AIT&_trksid=p2057872.m2749.l2649](https://www.ebay.it/itm/Connettore-Adattatore-Cavi-DVI-D-24-1-Pin-A-VGA-Fem/222304162724?ssPageName=STRK%3AMEBIDX%3AIT&_trksid=p2057872.m2749.l2649)
how can i check if i use analog or digital signal?

---

### Post by gxxg on 2020-04-15
lspci -k | grep -EA3 'VGA|Display'
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
    Subsystem: PC Partner Limited / Sapphire Technology Radeon HD 6450 1 GB DDR3
    Kernel driver in use: radeon
    Kernel modules: radeon


dmidecode 3.1
Getting SMBIOS data from sysfs.
SMBIOS 2.8 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: Hewlett-Packard
    Product Name: 2B34
    Version: 2.10 
    Serial Number:  
    Asset Tag:  
    Features:
        Board is a hosting board
        Board is removable
        Board is replaceable
    Location In Chassis:  
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

---

### Post by guiverc on 2020-04-15
The picture of your link looked like a passive converter to me (it just changes pins, wiring each pin to another pin on the other plug). Active converters need chips & circuit to change signals, thus require power to be provided from somewhere to operate, allowing digital signals to convert the data traffic from one type to another (plus the change of wiring as well). 

No sorry I'm not aware of a method to tell if signal is digital or analog, I usually go by feel (try a few converters, if they all have result, esp if hardware is less than a decade old it's likely to be digital thus no-go with passive types). Analog is more common on older equipment (c2d, pentium 4, etc) though some cards/cables/ports tell you via use of DVI-D (digital only) rather than DVI-A (analogue only) though if it has a DVI-I you cannot tell (digital & analog can be used)

I'm no expert sorry, it's only a problem I deal with a few times & not recently.

---

### Post by CelticWarrior on 2020-04-15
> **gxxg said:**
> thank you, so if i will use a cable is possible to fix it? i will try... my converter is this one... [https://www.ebay.it/itm/Connettore-Adattatore-Cavi-DVI-D-24-1-Pin-A-VGA-Fem/222304162724?ssPageName=STRK%3AMEBIDX%3AIT&_trksid=p2057872.m2749.l2649](https://www.ebay.it/itm/Connettore-Adattatore-Cavi-DVI-D-24-1-Pin-A-VGA-Fem/222304162724?ssPageName=STRK%3AMEBIDX%3AIT&_trksid=p2057872.m2749.l2649)
how can i check if i use analog or digital signal?

No, not a converter, it's a simple plug adapter for very specific usages.
I'm not a specialist either but I can say with 100% certainty it doesn't work for your intended purpose.

---

### Post by gxxg on 2020-04-17
ok thank you !!! solved! with a dvi cable, no adapter; before closing all, since the video card has another hdmi output, do you think is possible to use a third monitor ? is this adapter wrong or correct ----- [https://www.ebay.it/itm/1080P-HDMI-Maschio-a-VGA-Femmina-Cavo-Video-Adattatore-Convertitore-per-DVD-Hl/164001861284?ssPageName=STRK%3AMEBIDX%3AIT&var=463620973898&_trksid=p2057872.m2749.l2649](https://www.ebay.it/itm/1080P-HDMI-Maschio-a-VGA-Femmina-Cavo-Video-Adattatore-Convertitore-per-DVD-Hl/164001861284?ssPageName=STRK%3AMEBIDX%3AIT&var=463620973898&_trksid=p2057872.m2749.l2649) ?

---

### Post by CelticWarrior on 2020-04-17
> **gxxg said:**
> ok thank you !!! solved! with a dvi cable, no adapter; before closing all, since the video card has another hdmi output, do you think is possible to use a third monitor ? is this adapter wrong or correct ----- [https://www.ebay.it/itm/1080P-HDMI-Maschio-a-VGA-Femmina-Cavo-Video-Adattatore-Convertitore-per-DVD-Hl/164001861284?ssPageName=STRK%3AMEBIDX%3AIT&var=463620973898&_trksid=p2057872.m2749.l2649](https://www.ebay.it/itm/1080P-HDMI-Maschio-a-VGA-Femmina-Cavo-Video-Adattatore-Convertitore-per-DVD-Hl/164001861284?ssPageName=STRK%3AMEBIDX%3AIT&var=463620973898&_trksid=p2057872.m2749.l2649) ?

Maybe, maybe not. It also depends on the driver supporting it.
But yes, this one is an actual converter ("convertitore"-> Supporta la conversione di segnali digitali in segnali analogici) and it works only from HDMI to VGA, not the other way around. The other one is just a plug adpater that is used for very specific setups, mostly for non-standard fake HDMIs.

---

