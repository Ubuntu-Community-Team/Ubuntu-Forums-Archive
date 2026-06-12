---
title: "crashes during boot sequence - memory frequency?"
date: 2008-06-22
forum: Hardware
---

### Post by laihafloyd on 2008-06-22
For the past couple of years on rare occasions i have issues with ubuntu crashing while booting.  it happens when the splash screen progress bar first starts to move and i hear a click then a winding sound and everything freezes.  

somehow, when this first started happening, i realized that by lowering my memory frequency (in the bios, i can change it from 200 MHz to 100 MHz).  Originally, it was set at 200 MHz, and I keep having to lower it.  I just lowered it again from 133 to 100 to stop it from crashing tonight. Does this make any sense?  In the bios it is listed as CPU External Frequency.

Also, when i raise it to 200, it doesn't even get to the GRUB menu before locking up and i hear the click and winding sound repeatedly.  

Any help or ideas would be greatly appreciated!

Marc

---

### Post by damphoud on 2008-06-22
Mobo specs? Have you looked into bios updates? Have you ran memtest?

---

### Post by laihafloyd on 2008-06-22
i just ran lshw and here is some of the information:

 description: Desktop Computer
    product: A7N8X2.0
    vendor: ASUSTeK Computer INC.
    version: REV 2.xx
    serial: xxxxxxxxxxx
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: A7N8X2.0
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: REV 2.xx
       serial: xxxxxxxxxxx
       slot: Serial Port 1
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: ASUS A7N8X2.0 ACPI BIOS Rev 1006 (08/19/2003)
          size: 64KiB
          capacity: 192KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm)
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: Socket A
          size: 1100MHz
          capacity: 3GHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst synchronous external write-back data
     *-memory
          description: System Memory
          physical id: 26
          slot: System board or motherboard
          size: 768MiB
          capacity: 1536MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DDR1
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous [empty]
             physical id: 1
             slot: DDR2
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous
             physical id: 2
             slot: DDR3
             size: 256MiB
             width: 64 bits

---

### Post by damphoud on 2008-06-22
You can try to update your bios to c1007... please take great caution if your not too familiar.

[http://support.asus.com/download/download.aspx?modelname=A7N8X&SLanguage=en-us](http://support.asus.com/download/download.aspx?modelname=A7N8X&SLanguage=en-us)

---

### Post by laihafloyd on 2008-06-22
ran the memtest overnight and didn't get any errors.  i'm not too sure if i want to update the bios or not.  is it something that i can recover from if i screw it up?

---

### Post by damphoud on 2008-06-22
No not really, but ASUS is pretty good about making sure the user doesn't mess up. I'm sure they have a easy updater to run in windows, if you have windows installed. You can download the updater util and the c1007, and if your mobo doesn't match the bios update, it wont run.

---

### Post by laihafloyd on 2008-06-22
no more windows here!  i've read a few posts about creating a bootable freedos disk that i can flash the mobo with.  guess i'll try that.

---

