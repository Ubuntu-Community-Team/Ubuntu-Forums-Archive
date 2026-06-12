---
title: "Dell D800 won't reboot while in docking station"
date: 2010-07-14
forum: Hardware
---

### Post by OpticsGuy on 2010-07-14
Karmic dual-boot with XP, Dell D800 laptop, noobie to Linux

When in the docking station only, if I power down the next time I try to start up (push the power-on button on the docking station) the power light will come on very briefly and then go back off.  I have to physically remove the laptop from the docking station and pull the battery. After that it will power up just fine in the docking station - until the next power down.  I have no problems powering up and down when not in the docking station.

computer                  
    description: Portable Computer
    product: Latitude D800
    vendor: Dell Computer Corporation
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=docking uuid=44454C4C-4200-1054-8051-B3C04F573231
  *-core
       description: Motherboard
       product: 01W890
       vendor: Dell Computer Corporation
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A12 (01/28/2005)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1600MHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.9.5
          slot: Microprocessor
          size: 1600MHz
          capacity: 1700MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2 cpufreq

---

### Post by OpticsGuy on 2010-08-20
Overcome by events -- hard disk crashed.  New HD with Lucid = no problems.

---

