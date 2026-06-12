---
title: "Compatibility whith this computer?"
date: 2009-02-21
forum: Hardware
---

### Post by azas on 2009-02-21
Hello

I want to buy a new computer and i want to know if Ubuntu works fine with it.

Specifications:
Motherboard:
Gigabyte GA-EP45T-UD3R
Chipsets:  

  Intel® P45 Express 
  Intel® ICH10R 
  iTE IT8718 
  T.I. TSB43AB23 
  Realtek ALC889A de 8 canales 

Link: [http://www.giga-byte.es/products/mb/specs/ga-ep45t-ud3r_10.html](http://www.giga-byte.es/products/mb/specs/ga-ep45t-ud3r_10.html)

Processor

Intel® Core™2 Quad 12MB L2 
3 GHz
1.333 Mhz

Graphic card is nvidia.

Thanks.

---

### Post by damis648 on 2009-02-21
Looks fine to me, I automatically assume Ubuntu works on anything unless I hear otherwise. :popcorn:

---

### Post by azas on 2009-02-24
Someone test a similiar computer?

---

### Post by Patr on 2009-03-21
I have a GA-EP45T-UD3R, and it is fine with Ubuntu 8.10 and with the new 9.04. My CPU is E8400. My graphics card is NVIDIA.

To set the sound properly, you have to try out the sliders en switches of the mixer. I set up the sound in Windows XP first to get to know it.

In the BIOS it is possible to set the AHCI mode. This will work perfect with Ubuntu. I didn't enable the AHCI in the BIOS, because I didn't like the extra Intel ROM during boot.

The HPET (high resolution timer) can be set on or off in the BIOS. I have it 'on' now.

I tried RAID, but could not get it working both in Windows XP and Ubuntu on the same RAID disks. So I dropped RAID.

I have tested in Ubuntu: SATA, IDE, COM1, USB, SOUND, LAN.
I have NOT tested in Ubuntu: Firewire, parallel port.

Important BIOS settings:
  Robust Graphics Booster: Auto   (higher crashes my 7300GS)
  C1E: on
  C2/C2E and C4/C4E: off          (have to test this more)
  Virtualization Technology: On   (needed for KVM)


Overall it is a very good choice.

---

### Post by broad on 2009-06-06
I'm thinking the same hardware except Intel motherboard 
[http://www.intel.com/products/desktop/motherboards/DP45SG/DP45SG-overview.htm](http://www.intel.com/products/desktop/motherboards/DP45SG/DP45SG-overview.htm)

I hope it works, I assume IDE instead AHCI in BIOS for Win XP?

---

