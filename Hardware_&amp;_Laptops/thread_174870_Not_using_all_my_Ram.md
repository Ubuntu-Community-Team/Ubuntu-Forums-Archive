---
title: "Not using all my Ram"
date: 2006-05-12
forum: Hardware &amp; Laptops
---

### Post by kwhatcher on 2006-05-12
hey I've got 1GB of ram and but SysMon only see 884 MB, could some one plz help thanks,


Intel P4 HT
Foxcon MB
2x512GB DDR Ram sticks

fully upgraded w/ apt-get using all repozis

---

### Post by johnc4510 on 2006-05-12
I have 512, but SysMon shows 503. I suppose like cpu's it's not an exect number, but your's seems low compare to what you should have.

---

### Post by mips on 2006-05-12
post output of **free** command

---

### Post by tonyr on 2006-05-12
Reported memory use with **free** and in **/proc/meminfo** does not
include the kernel footprint. Here's a reasonable article:
[http://linuxweblog.com/node/232]("http://linuxweblog.com/node/232")

So the next logical question is: How do you independantly verify
the kernel footprint?

---

### Post by tonyr on 2006-05-12
[QUOTE=tonyr]
So the next logical question is: How do you independantly verify
the kernel footprint?[/QUOTE]

To answer my own question
```

grep Memory: /var/log/messages

```

Mine (extracted sample) shows:
> 
May 12 09:59:06 localhost kernel: [4294670.804000] Memory: 508568k/523776k available (1975k kernel code, 14612k reserved, 607k data, 288k init, 0k highmem)



Now **SysMon** on my machine also shows 503MB total, so there may still be
some usage unaccounted for.  Someone who understands kernel memory
usage better than I would have to explain this.  I believe that the kernel
has some dynamic objects, allocated at startup,  whose total size may
depend on hardware configuration.

---

### Post by Abild on 2006-05-12
[QUOTE=kwhatcher]hey I've got 1GB of ram and but SysMon only see 884 MB, could some one plz help thanks,


Intel P4 HT
Foxcon MB
2x512GB DDR Ram sticks

fully upgraded w/ apt-get using all repozis[/QUOTE]

It's because you're using the 386 kernel
Run apt-get install linux-image-686 and ubntu should start using all of your ram.

You may also want to install linux-restricted-modules-686 if you need one of the folowing modules:
 - madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl, fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcdslusba,
   fcpci, fcpcmcia, fcpcmcia_cs, fcusb, fxusb (AVM ISDN)
 - ltmodem (Winmodem)

---

### Post by bluevoodoo1 on 2006-05-12
If you're using onboard video it might use some of your memory. It did with my system. You can disable this (or lower the number) in your BIOS.

---

### Post by tonyr on 2006-05-12
Just for kicks, here's some fun stuff.

```

cat /proc/iomem

```

There's a memory map of your current system. Yeah, it's hex. Either you
know it by sight, or do the math (or use a converting calculator like I did).

Here's what mine says:
```

00000000-0009efff : System RAM
0009f000-0009ffff : reserved
000a0000-000bffff : Video RAM area
000c0000-000cdfff : Video ROM
000ce000-000ce7ff : Adapter ROM
000f0000-000fffff : System ROM
00100000-1feeffff : System RAM
  00100000-0030b608 : Kernel code
  0030b609-0039ea43 : Kernel data
1fef0000-1fefefff : ACPI Tables
1feff000-1fefffff : ACPI Non-volatile Storage
1ff00000-1ff7ffff : System RAM
1ff80000-1fffffff : reserved
30000000-32ffffff : PCI Bus #02
  30000000-31ffffff : PCI CardBus #03
  32000000-3201ffff : 0000:02:01.0
33000000-330003ff : 0000:00:1f.1
34000000-35ffffff : PCI CardBus #03
  34000000-34001fff : 0000:03:00.0
    34000000-34001fff : 0000:03:00.0
e0000000-e7ffffff : PCI Bus #01
  e0000000-e0ffffff : 0000:01:00.0
    e0000000-e0ffffff : nvidia
  e1000000-e100ffff : 0000:01:00.0
e8000000-e80fffff : PCI Bus #02
  e8000000-e800007f : 0000:02:01.0
  e8001000-e8001fff : 0000:02:04.0
    e8001000-e8001fff : yenta_socket
ec000000-efffffff : 0000:00:00.0
f0000000-f7ffffff : PCI Bus #01
  f0000000-f7ffffff : 0000:01:00.0
ff800000-ffbfffff : reserved
fff00000-ffffffff : reserved

```

The indentations show subranges; some are single spanning subranges.
My system has 512MB.  Note that the line **1ff80000-1fffffff : reserved**
represents the top of my memory, 1fffffff=536870911 ((512*512*1024)-1). 
Everything above that seems to be I/O space related.

I submit  that a little analysis here might provide some answers, and the
realization that the answer to the original question is not-so-simple.

---

### Post by kwhatcher on 2006-05-18
kwhatcher@Odin:~$ free
             total       used       free     shared    buffers     cached
Mem:        905336     898992       6344          0      54040     611488
-/+ buffers/cache:     233464     671872
Swap:      2835464      14004    2821460
kwhatcher@Odin:~$

---

