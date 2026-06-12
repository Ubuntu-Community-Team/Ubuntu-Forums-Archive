---
title: "RAM upgrade, tweaking MHz"
date: 2011-10-07
forum: Hardware
---

### Post by Drone4four on 2011-10-07
I picked up Kingston Hyper-X 4x4GBs of DDR3 1600 MHz ram at my local PC shop.  The new RAM runs Windows 7 without any BSODs and it runs Ubuntu without any kernel panics.  I have however run into an issue. The BIOS says it is only running at 1333 MHz, rather than 1600 MHz as it says on the packaging.  I know my relatively new motherboard (a GIGABYTE GA-P45T-ES3G LGA 775 Intel P45) is capable of running 1600MHz memory because it says so in the motherboard manual and says so on Newegg where I ordered it:  

[http://www.newegg.ca/Product/Product.aspx?Item=N82E16813128496](http://www.newegg.ca/Product/Product.aspx?Item=N82E16813128496)

What settings should I change in my BIOS to up the speed from 1333Mhz to 1600Mhz?  Here is the section of the BIOS designated DRAM Performance Control:  

[http://picpaste.com/BIOS-iii-ONeKC6sd.jpg](http://picpaste.com/BIOS-iii-ONeKC6sd.jpg)

Also, here is the new memory related output for sudo lshw:

```

daniel@natty:~$ sudo lshw
...
    *-memory
        description: System Memory
        physical id: 1c
        slot: System board or motherboard
        size: 16GiB
      *-bank:0
           description:  400 MHz (2.5 ns)
           physical id: 0
           slot: A0
           size: 4GiB
           width: 2244 bits
           clock: 400MHz (2.5ns)
      *-bank:1
           description: DIMM 400 MHz (2.5 ns)
           physical id: 1
           slot: A1
           size: 4GiB
           width: 2244 bits
           clock: 400MHz (2.5ns)
      *-bank:2
           description: DIMM 400 MHz (2.5 ns)
           physical id: 2
           slot: A2
           size: 4GiB
           width: 2244 bits
           clock: 400MHz (2.5ns)
      *-bank:3
           description: DIMM 400 MHz (2.5 ns)
           physical id: 3
           slot: A3
           size: 4GiB
           width: 2244 bits
           clock: 400MHz (2.5ns)
...

```

As you can see, the clock for the 4 DIMMs are set to 400 MHz rather than 1333 MHz as it says in the pic of my BIOS.  What gives?

---

