---
title: "Ubuntu 12.04 64bit sees only 7.8GiB when i have 8GB. no igp."
date: 2012-11-02
forum: Hardware
---

### Post by snowcake on 2012-11-02
Hello, I recently using Ubuntu 12.04 64bit and i like it.

Windows and memtest86 both are saying i have 8155MB for full use. And windows say i have 8gb on computer properties.

Ubuntu says i have 7.8GiB in system monitor. I also booted Fedora 64bit live cd and it says the same thing.

Why?? As far as i can tell, there is nothing wrong with my memory.
I also use a dedicated GPU, so no igp is stealing my memory.

How much ram memory having you all in system monitor?
Does it also display less memory than in windows or memtest? Assuming you have no igp.

I am really worried since this is a new pc.


Thanks,

---

### Post by jerome1232 on 2012-11-02
Windows displays **installed** physical memory while Ubuntu displays **usable** memory.

If you dig a bit deeper in Windows, by going into the resource monitor, you should see a total that is much closer to what Ubuntu is reporting.

---

### Post by snowcake on 2012-11-02
> **jerome1232 said:**
> Windows displays **installed** physical memory while Ubuntu displays **usable** memory.

If you dig a bit deeper in Windows, by going into the resource monitor, you should see a total that is much closer to what Ubuntu is reporting.

Not really.

[IMG]http://i.imgur.com/AFWlI.png[/IMG]

---

### Post by jerome1232 on 2012-11-02
8155 MB converts to 7.96387 GB, easily within a rounding error, what does this command show on Ubuntu

```
grep MemTotal /proc/meminfo
```

edit: It's also possible they show a slight difference due to the way they reserve space for hardware, I thought this was done by the bios but I could be wrong, I don't know enough about exactly how that is done.

---

### Post by snowcake on 2012-11-02
> **jerome1232 said:**
> 8155 MB converts to 7.96387 GB, easily within a rounding error, what does this command show on Ubuntu

```
grep MemTotal /proc/meminfo
```edit: It's also possible they show a slight difference due to the way they reserve space for hardware, I thought this was done by the bios but I could be wrong, I don't know enough about exactly how that is done.

It shows me: ¨MemTotal:        8141292 kB¨ 
= 7950.48046875mb = 7.764141083gb if i calculated it correctly.

Computername:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7950       1718       6232          0         59        461
-/+ buffers/cache:       1196       6753
Swap:         8581          0       8581

What is strange because in windows i have 1186+6798 = 7984mb = 7.796875gb vs  7.764141083gb in Ubuntu. A slight difference. How can this be explained?

---

### Post by snowcake on 2012-11-02
test. Edit: nevermind, it works again. Had problems with the site.

---

### Post by jerome1232 on 2012-11-02
I honestly don't know, likely it's just a difference in how the OS is using it, I know the Kernel itself claims some etc...


You can also show physically installed ram with this command, I don't think there is anything wrong with your setup, just slight differences between the OS's.

```
sudo lshw -C Memory
```

---

### Post by snowcake on 2012-11-02
Well, the strange thing is that i tested it with ubuntu 32bit and it says i have 7.9GiB vs 7.8GiB with 64bit. How can this be explained?

I tested it with the command: sudo lshw-C Memory

Computername:~$ sudo lshw -C Memory
[sudo] password for pc:
  *-firmware
       description: BIOS
       vendor: xx
       physical id: 0
       version: Pxxx
       date: xxx
       size: 64KiB
       capacity: 8128KiB
       capabilities: xx
  *-cache:0
       description: L2 cache
       physical id: a
       slot: CPU Internal L2
       size: 512KiB
       capacity: 512KiB
       capabilities: internal write-through instruction
  *-cache:1
       description: L1 cache
       physical id: b
       slot: CPU Internal L1
       size: 64KiB
       capacity: 64KiB
       capabilities: internal write-through
  *-cache:2
       description: L3 cache
       physical id: c
       slot: CPU Internal L3
       size: 3MiB
       capacity: 3MiB
       capabilities: internal write-back instruction
  *-memory
       description: System Memory
       physical id: x
       slot: System board or motherboard
       size: 8GiB
     *-bank:0
          description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
          product: xx
          vendor: Kingston
          physical id: 0
          serial: xx
          slot: ChannelA-DIMM0
          size: 4GiB
          width: 64 bits
          clock: 1333MHz (0.8ns)
     *-bank:1
          description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
          product: xx
          vendor: Kingston
          physical id: 1
          serial: xx
          slot: ChannelB-DIMM0
          size: 4GiB
          width: 64 bits
          clock: 1333MHz (0.8ns)

---

