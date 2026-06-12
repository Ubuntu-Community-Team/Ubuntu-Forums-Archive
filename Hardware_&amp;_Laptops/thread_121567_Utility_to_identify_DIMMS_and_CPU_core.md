---
title: "Utility to identify DIMMS and CPU core"
date: 2006-01-25
forum: Hardware &amp; Laptops
---

### Post by hartz on 2006-01-25
Hi guru's.

What utility exist under Linux that I can use to tell me some of the information shown by the Windows tool CPUz.  In particular, I would like to see the CPU Core / revission, and the memory module identification information, eg what timings is supported under various speeds.

It does not need to be just one utility, and it certainly does not have to be a graphical tool, command line is totally fine :-)

Thanx,
  _Hartz

---

### Post by jlburly on 2006-01-25
[QUOTE=hartz2]
What utility exist under Linux that I can use to tell me some of the information shown by the Windows tool CPUz.  In particular, I would like to see the CPU Core / revission, ...
[/QUOTE]

Not sure if it will give you all that you want/need, but you might try **lshw**:

```

$ sudo lshw

    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: LP NF4 Series
       vendor: DFI Corp,LTD
       physical id: 0
       version: 1.0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (06/23/2005)
          size: 128KB
          capacity: 448KB
....

```

A couple of other cli tools that might be of interest are **lspci** and **lsusb**. 

Cheers,

Jeff

---

### Post by hartz on 2006-01-26
Sorry for posting just to bump the thread, but I am hoping more eyes will see this as I desparately do NOT want to have to install Windows JUST to run this one utility!!!!

I am trying to make a break (from Windows) here!

---

### Post by ekarni on 2006-01-26
Coincidentally, someone else posted a similar thread yesterday here:
[http://www.ubuntuforums.org/showthread.php?t=121615]("http://www.ubuntuforums.org/showthread.php?t=121615")

You can try 
cat /proc/cpuinfo 
and
cat /proc/meminfo

for info on your CPU and memory, respectively.
(and ignore the link in that thread back to this one!)

---

