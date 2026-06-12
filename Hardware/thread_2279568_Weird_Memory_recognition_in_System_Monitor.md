---
title: "Weird Memory recognition in System Monitor?"
date: 2015-05-24
forum: Hardware
---

### Post by cybrsaylr on 2015-05-24
Have a Dell i7 with 8GBs of Ram as noted in my signature.

Out of habit I run 'System Monitor' > Resources,  just to keep in eye on what my PC is doing.
In Memory and Swap History the normal showing is 7.8 GiB of that 8 GiB is recognized. There is also a 8 GiB Swap.
Once in a great while however only 4Gib is recognized! Swap still shows 8 GiB.
After a PC restart, it reverts to its norm of recognizing 7.8 GiB of RAM. 

Any idea on why once in a while it recognizes only half of the RAM in the PC?

---

### Post by Vladlenin5000 on 2015-05-24
SWAP is a partition and as such, it isn't expected to change.
Are you running a Virtual Machine?

---

### Post by cybrsaylr on 2015-05-25
Not running a Virtual Machine. 

Just have a triple boot boot system now.
Have Win7 on a mechanical 2TB HDD and 64 bit Ubuntu 14.04 and 12.04 dual booted on a 128 SSD.

All 3 OSs run fine and normal.

---

### Post by Vladlenin5000 on 2015-05-25
OK, so... Which one of the Ubuntus is showing half of the RAM intermittently or both have the same symptoms? Windows presumably isn't showing the same or is it?

---

### Post by cybrsaylr on 2015-05-25
14.04 is mainly used and where I discovered half of the RAM intermittently shows. 
Didn't check either W7 or 12.04 since they are seldom run anymore.

The reason I noticed this 'half RAM' showing up in 14.04 was when attempting to trouble shoot why 14.04 would totally freeze/lock up intermittently at times a few minutes after booting up. When 14.04 would lock up I had to do a 'hard shutdown' due to mouse and everything being totally unresponsive. Then all ran normal again after restart. This lock up only happens intermittently a few minutes after a cold start. Maybe occurred a dozen times total, over the past month or two. It never locks up after running for many hours. 

Have no idea if the two are related?

FWIW thought of mentioning this. Have a 2½ yr old 128GB Kingston SSD that from day one reported in Ubuntu 'Disk Utility' that this SSD was failing due to a temp issue on a cold start. It seems Kingston temp parameters are set to show this SSD failing when temp is below 88° F. Several minutes after a cold start when the SSD warms to over 88° F, Disk Utility then reports the SSD is A-OK! I did report this to Kingston 2½ yrs ago and they said nothing to worry over, merely a parameter setting they made that was too tight. Other than that this SSD has run fine.

---

### Post by Vladlenin5000 on 2015-05-25
Weird indeed but I've no clue.
Hopefully someone else has.

---

### Post by sammiev on 2015-05-25
Hi,

Your video card is using the rest of your memory out of the 8 GiB.

---

### Post by cybrsaylr on 2015-05-26
> **sammiev said:**
> Hi,

Your video card is using the rest of your memory out of the 8 GiB.

Is there any way to check/verify this?
I have a nvidia  GEFORCE GT 630 video card with 2048MB DDR3 memory.

This lockup only occurrs a few minutes after a cold start when nothing intensive is being done by the PC to overly tax the video card.
As I said this 'half RAM' showing, was only discovered when attempting to trouble shoot the cold start lockup.

---

### Post by sammiev on 2015-05-26
In your Bios you will see next to your memory the size and usually under that you will see Video memory.
Your system will use some of the total memory for itself.

---

### Post by plucky on 2015-05-27
Is the 8Gb memory made up of 2 X 4Gb or 1 X 8Gb of DDR3?

Could be a seating problem if you have two memory modules.

When only 4Gb shows up in System Monitor,does free -m in a terminal show the same value?

What does ```
sudo lshw -c memory
``` show you as well?

Good Luck

---

### Post by cybrsaylr on 2015-05-28
plucky, 
 
PC has 4 X 2GB memory sticks.

Code:
**sudo lshw -c memory** ..... shows:

>  *-firmware              
       description: BIOS
       vendor: Dell Inc.
       physical id: 0
       version: A03
       date: 12/21/2009
       size: 128KiB
       capacity: 1984KiB
       capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
  *-cache:0
       description: L1 cache
       physical id: 5
       slot: L1-Cache
       size: 128KiB
       capacity: 128KiB
       capabilities: internal write-through data
  *-cache:1
       description: L2 cache
       physical id: 6
       slot: L2-Cache
       size: 1MiB
       capacity: 1MiB
       capabilities: internal write-through unified
  *-cache:2
       description: L3 cache
       physical id: 7
       slot: L3-Cache
       size: 8MiB
       capacity: 8MiB
       capabilities: internal write-back unified
  *-memory
       description: System Memory
       physical id: 22
       slot: System board or motherboard
       size: 8GiB
     *-bank:0
          description: DIMM Synchronous 1066 MHz (0.9 ns)
          product: EBJ21UE8BDF0-AE-F
          vendor: Elpida
          physical id: 0
          serial: 15341B2B
          slot: DIMM1
          size: 2GiB
          width: 64 bits
          clock: 1066MHz (0.9ns)
     *-bank:1
          description: DIMM Synchronous 1066 MHz (0.9 ns)
          product: EBJ21UE8BDF0-AE-F
          vendor: Elpida
          physical id: 1
          serial: 18341B2B
          slot: DIMM2
          size: 2GiB
          width: 64 bits
          clock: 1066MHz (0.9ns)
     *-bank:2
          description: DIMM Synchronous 1066 MHz (0.9 ns)
          product: EBJ21UE8BDF0-AE-F
          vendor: Elpida
          physical id: 2
          serial: 3D341B2B
          slot: DIMM3
          size: 2GiB
          width: 64 bits
          clock: 1066MHz (0.9ns)
     *-bank:3
          description: DIMM Synchronous 1066 MHz (0.9 ns)
          product: EBJ21UE8BDF0-AE-F
          vendor: Elpida
          physical id: 3
          serial: 40341B2B
          slot: DIMM4
          size: 2GiB
          width: 64 bits
          clock: 1066MHz (0.9ns)


---

### Post by cybrsaylr on 2015-06-12
FWIW neither this weird Memory recognition issue nor PC freeze-up has happened again since posting this thread.
Hoping it was just some kind on cyber fluke that happens at times.

---

