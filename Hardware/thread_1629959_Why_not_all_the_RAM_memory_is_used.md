---
title: "Why not all the RAM memory is used?"
date: 2010-11-24
forum: Hardware
---

### Post by Marzata on 2010-11-24
There are 2x2 GB RAM installed on the computer and **lswh** detects them (see below), but **free** (see below) shows that Ubuntu uses only 3 GB. PAE is installed. Any idea why Ubuntu is not using all the 4 GB? Thank you! 

Ubuntu 10.04 LTS (lucid) 
Kernel: 2.6.32-26-generic-pae 
Computer: HP Pavilion dv6000t 
Motherboard: Quanta 30BC 

```

user@ubuntu:~$ sudo lshw -C memory
  *-memory
       description: System Memory
       physical id: d
       slot: System board or motherboard
       size: [COLOR="Red"]4GiB[/COLOR]
     *-bank:0
          description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
          physical id: 0
          slot: DIMM 1
          size: [COLOR="Red"]2GiB[/COLOR]
          width: 64 bits
          clock: 667MHz (1.5ns)
     *-bank:1
          description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
          physical id: 1
          slot: DIMM 2
          size: [COLOR="Red"]2GiB[/COLOR]
          width: 64 bits
          clock: 667MHz (1.5ns)

```


```

user@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:       [COLOR="Red"]3095004[/COLOR]     636568    2458436          0      47832     272288
-/+ buffers/cache:     316448    2778556
Swap:      2938872          0    2938872

```

---

### Post by samborambo on 2010-11-24
That's an easy one. Your OS kernel is 32 bit, not 64 bit.

32 bit address space can only address 4GB. 1GB of that address space is reserved for device I/O. This means that only 3GB of a 4GB system running 32 bit is used.

Solution: change to Ubuntu 64 bit. Install ia32libs if you need to run 32 bit software.

It's amazing, I just bought a Lenovo P550. It was advertised as having 4GB but had a 32 bit version of Windows 7 installed, meaning I could only see 3GB! False advertising. Didn't matter, I just installed Ubuntu 64 bit anyway.

Sam.

---

### Post by Marzata on 2010-11-24
Thank you, but the kernel is 2.6.32-26-generic-pae.

---

### Post by Marzata on 2010-11-25
More ideas why?

---

### Post by PRC09 on 2010-11-25
I found this explanation on another site dealing with memory use in 64bit but I think it is accurate for 32 bit as well....I think.....

> Note: When the physical RAM that is installed on a computer equals the address space that is supported by the chipset, the total system memory that is available to the operating system is always less than the physical RAM that is installed. For example, consider a computer that has an Intel 975X chipset that supports 8 GB of address space. If you install 8 GB of RAM, the system memory that is available to the operating system will be reduced by the PCI configuration requirements. In this scenario, PCI configuration requirements reduce the memory that is available to the operating system by an amount that is between approximately 200 MB and approximately 1 GB. The reduction depends on the configuration. 

---

### Post by fishtoprecords on 2010-11-25
> **Marzata said:**
> Thank you, but the kernel is 2.6.32-26-generic-pae.

PAE helps when you have more than 4GB. It does not remove the big blocks of reserved memory in the 3GB and up area. For most folks, when you go over 4GB, you might as well run a 64bit OS. PAE was an important hack for folks running Windows XP/2003 server, where they had to stay 32 bit, but needed more memory.

---

### Post by Fafler on 2010-11-26
I've seen this before. Had to change someting in the BIOS to map the RAM between 3 and 4 gb above the 4 gb boundary. After that, a PAE enabled kernel was able to take advantage of it. I can't remember what the option was called, though.

---

### Post by Marzata on 2010-11-28
> **Fafler said:**
> I've seen this before. Had to change someting in the BIOS to map the RAM between 3 and 4 gb above the 4 gb boundary. After that, a PAE enabled kernel was able to take advantage of it. I can't remember what the option was called, though.

There is no option in the BIOS to change anything about the RAM. The BIOS detects 4 GB. Ubuntu **free** command shows only 3 GB. Other ideas why?

---

### Post by PRC09 on 2010-11-28
The memory use that you see is the result of a combination bios and chipset settings.The 4gb that you have installed is seen by the bios but cannot be used by your operating system because the way that memory is assigned within the system.As posted previously if your chipset or bios does NOT allow memory remapping then  the system automatically reserves a certain amount within  that 4gb for the SYSTEM (PCI devices,) itself to use.In your case even if you use a 64bit OS  it cannot use memory that is technically already in use by the SYSTEM..... The following link should be of interest ao explain it better......


[http://duartes.org/gustavo/blog/post/motherboard-chipsets-memory-map](http://duartes.org/gustavo/blog/post/motherboard-chipsets-memory-map)

---

