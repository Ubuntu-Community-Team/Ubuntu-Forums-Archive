---
title: "Pentium D - Dual Core SMP problems with Edgy Eft"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by jedir0x on 2006-11-15
I've got a Dell XPS workstation with a Pentium D dual core.  I've recently wiped my dapper install to do a fresh install of Edgy.  In Dapper I had dual core support without any problems.  I've read around the forums that all the linux-generic package should support SMP, however I don't see it.  Here's my hardware configuration:

```
bdilley@bdilley-linux:~$ uname -a
Linux bdilley-linux 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux
bdilley@bdilley-linux:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 6
model name      : Intel(R) Pentium(R) D CPU 3.00GHz
stepping        : 2
cpu MHz         : 2993.701
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 3
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up pni monitor ds_cpl vmx cid cx16 xtpr lahf_lm
bogomips        : 5993.94

bdilley@bdilley-linux:~$ lspci
00:00.0 Host bridge: nVidia Corporation Unknown device 0071 (rev a3)
00:00.1 RAM memory: nVidia Corporation Unknown device 007f (rev a1)
00:00.2 RAM memory: nVidia Corporation Unknown device 0075 (rev a1)
00:00.3 RAM memory: nVidia Corporation Unknown device 006f (rev a1)
00:00.4 RAM memory: nVidia Corporation Unknown device 00b4 (rev a1)
00:01.0 RAM memory: nVidia Corporation Unknown device 0076 (rev a1)
00:01.1 RAM memory: nVidia Corporation Unknown device 0078 (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 0079 (rev a1)
00:01.3 RAM memory: nVidia Corporation Unknown device 007a (rev a1)
00:01.4 RAM memory: nVidia Corporation Unknown device 007b (rev a1)
00:01.5 RAM memory: nVidia Corporation Unknown device 007c (rev a1)
00:01.6 RAM memory: nVidia Corporation Unknown device 007d (rev a1)
00:02.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:04.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:09.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
00:0a.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a4)
00:0a.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4)
00:0d.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:0f.0 IDE interface: nVidia Corporation CK804 IDE (rev f3)
00:10.0 RAID bus controller: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:11.0 RAID bus controller: nVidia Corporation CK804 Serial ATA Controller (rev f4)
00:12.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:13.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:17.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation NV41.1 [GeForce 6800] (rev a2)
03:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
bdilley@bdilley-linux:~$ 

```

Can anyone recomend a method of enabling SMP/multi processor/core in Edgy?  Thanks in advance :)

---

### Post by mnoble on 2006-12-01
I had a similar problem and saw this thread
[http://www.ubuntuforums.org/showthread.php?t=277400&highlight=intel+d820](http://www.ubuntuforums.org/showthread.php?t=277400&highlight=intel+d820)
and saw the linux-686-SMP package is obsoleted by linux-image-generic, so i installed the linux-image-generic and i can see both proc's now

---

