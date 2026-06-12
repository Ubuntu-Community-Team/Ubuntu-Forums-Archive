---
title: "Problem with my graphics card in laptop"
date: 2008-10-10
forum: General Help
---

### Post by ajsup on 2008-10-10
I have a laptop with a configuration as follows

Model name:Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz
Frequency: 800.000 MHz
L2 cache: 2048 KB
Bogomips: 3196.41
Numbering: family(6) model(15) stepping(6)
Flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm


Ubuntu 8.04 (hardy)
2.22.3 (Ubuntu 2008-07-09)
2.6.24-19-generic (#1 SMP Wed Aug 20 22:56:21 UTC 2008)
Linux
4.2.3 (i486-linux-gnu)

And graphic card

VIA Technologies, Inc. Chrome9 HC IGP (rev 01) (prog-if 00 [VGA controller])
Subsystem: CLEVO/KAPOK Computer Unknown device 5408

(I used sysinfo)

I am dying to install compiz fusion into the laptop.. but the problem is it doesnt recognize the graphics card ( i cant even have normal effects).. and in the ubuntu login window, only half of it is visible though the desktop's resolution is proper..

I tried some of the links for ubuntu 7.10 etc. but didnt work.. 

I am a great fan of ubuntu.. and i know lots of modifications can be done to the laptop.. yet i cannot do anything.. i am desperate.. Please help..

---

### Post by loomsen on 2008-10-10
Uhh, you didn't nail it well with your graphics card.
It's an onboard card right? On German Boards you get to read many many complaints about this card. It's claimed to be the slowest onBoard card the actually is.

However, if you have hwinfo installed you can type 

hwinfo --gfx

to get somewhat verbose output, the status qou, at least what I remember about VIA, is, that everyone was constantly switching drivers and waiting for better drivers to be offered. 
There are 
openchrome unichrome and via
drivers you can use with your card. Just give it a try.

*edit*
lucky you, the VIA guys actually released sth.
[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

give it a try, good luck with it.

---

### Post by ajsup on 2008-10-10
i used the hwinfo

i got the following 

12: PCI 100.0: 0300 VGA compatible controller (VGA)            
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3371
  Unique ID: VCu0.KoMbAhPshQ2
  Parent ID: vSkL.S16qDHSKEeD
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "CLEVO/KAPOK VGA compatible controller"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3371
  SubVendor: pci 0x1558 "CLEVO/KAPOK Computer"
  SubDevice: pci 0x5408
  Revision: 0x01
  Memory Range: 0xa0000000-0xbfffffff (rw,prefetchable)
  Memory Range: 0xc9000000-0xc9ffffff (rw,non-prefetchable)
  IRQ: 9 (no events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001106d00003371sv00001558sd00005408bc03sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #27 (PCI bridge)

i need it.. and its activivity unknown.. how do i activate it..

---

### Post by loomsen on 2008-10-10
> i need it

Then do what I told ya. First few lines are similar to yours, but you're lacking an appropriate driver. This is what it shows me:

  Revision: 0xa1
  Driver: "nvidia"
  Driver Modules: "nvidia"
  Memory Range: 0xc6000000-0xc6ffffff (rw,non-prefetchable)
  Memory Range: 0xd0000000-0xdfffffff (rw,prefetchable)
  Memory Range: 0xc4000000-0xc5ffffff (rw,non-prefetchable)
  I/O Ports: 0x2000-0x2fff (rw,disabled)
  IRQ: 16 (1367922 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v000010DEd00000407sv000014C0sd00000025bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: nv
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #32 (PCI bridge)


I posted 3 drivers you could have given a try, and even posted a link where you just had to find the download button yourself.
CMON! I'm eveb quoting it again esp for you, but... 
Let me tell ya, if you keep refusing to READ you should consider if you might be wrong on the internet...
[quote=ME]

**openchrome   unichrome ** and ** via**
are drivers you can use with your card
**[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)**[/quote]

Definetely your turn now.

---

