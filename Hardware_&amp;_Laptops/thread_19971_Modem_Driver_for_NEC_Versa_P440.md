---
title: "Modem Driver for NEC Versa P440"
date: 2005-03-14
forum: Hardware &amp; Laptops
---

### Post by tara_zw on 2005-03-14
Hi. My new Ubuntu system is wonderful. It doesn't look as though it has recognised my modem though. It's a modem MDC 56k v.92. Does anyone have any advice on finding and downloading the appropriate driver (presumably this is the problem?). Thanks!

---

### Post by az on 2005-03-14
Linmodems.org


Get scanmodem and run it.

Post the output here.

---

### Post by steffen on 2005-03-15
Get: [http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)

Download to your home directory. Click downloaded file in Nautilus and unzip. Go to directory that is created.

Right click file 'scanModem' and make sure permission is set to executable.

Click on 'scanModem' file in Nautilus and click 'run' (in terminal). A directory should be created called 'Modem' and in it a file called 'ModemData.txt'. Post that file here.

Instructions taken from: [http://linmodems.technion.ac.il/first.html](http://linmodems.technion.ac.il/first.html)

---

### Post by tara_zw on 2005-03-18
DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.04 kernel 2.6.10-4-686
 Occassionally reponses are blocked by an Internet Providers mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2005_March_3
------------ --------------  System information ------------------------
Ubuntu 5.04 "Hoary Hedgehog" Development Branch 
 on System with processor: i686
 currently under kernel:   2.6.10-4-686

There are emerging complications under 2.6.10 kernels.  Concerning code for:
Smartlink slmodem :
   slmodem-2.9.9a.tar.gz at [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
      has the current fixes.  Related messages are:
   [http://www.datiku.com/documents/2610_migration.php](http://www.datiku.com/documents/2610_migration.php)
   [http://www.ussg.iu.edu/hypermail/linux/kernel/0409.3/0345.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0409.3/0345.html) 
   [http://linmodems.technion.ac.il/archive-fourth/msg03736.html](http://linmodems.technion.ac.il/archive-fourth/msg03736.html) . 
Lucent/Agere DSP/ltmodem:
  [http://linmodems.technion.ac.il/archive-fourth/msg03733.html](http://linmodems.technion.ac.il/archive-fourth/msg03733.html) 
Concerning Intel-536ep 
   [http://linmodems.technion.ac.il/archive-fifth/msg00280.html](http://linmodems.technion.ac.il/archive-fifth/msg00280.html)
   
 The kernel was assembled with compiler:  3.3.5
 a gcc package must be installed to support driver compiling

Checking for kernel-headers needed for compiling.
Kernel-header resources are not evident.
Within your Linux distributions resources, search for package names with:
  linux-headers-2.6.10-4-686
  kernel-source-2.6.10-4-686
  linux-2.6.10-4-686
One of which must be installed if compiling drivers to match kernel 2.6.10-4-686 proves necessary.
This is necessary for most modem drivers, through some Linux distributions provide some compiled drivers.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
  

 A /dev/modem symbolic link is not set.
 Checking for USB modems
 None found

Modem candidates are at PCI_buses:  0000:00:08.0
    
Providing detail for device at PCI_bus 0000:00:08.0
  with vendor-ID:device-ID
	    ----:----
Class 0703: 10b9:5457   Modem: ALi Corporation M5457 AC'97 Modem Controller (prog-if 00 [Generic])
  SubSystem 1631:3009   Unknown device 1631:3009
0000:00:08.0 0703: 10b9:5457
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at e0001000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 1c00 [size=256]
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 10b9:5457 1631:3009 debian 2.6.10-4-686 3.3.5     i686

       
 The soft modem Subsystem operates under a controller
   10b9:5457  ALI 5457 AC-Link Controller 
 capable of supporting under Linux AT LEAST modem Subsystem chips from manufacturers:

	Pctel
	Conexant
	Intel
	Smartlink
 The Subsystem PCI id does not itself identify the modem Codec.
  Driver snd-intel8x0m  may enable codec acquisition

---

### Post by az on 2005-03-18
sl-modem-daemon
sl-modem-source
build-essential
linux-headers

Good luck.

---

### Post by tara_zw on 2005-03-21
Hi Azz

Thanks very much....almost got there I think. Didn't know what to choose after the third link, ie linux-headers, this is what came up:

#

dpkg-dev (>= 1.4.1.19)
    Package building tools for Debian

#

[dep] g++ (>= 3:3.3)
    The GNU C++ compiler

#

[dep] gcc (>= 3:3.3)
    The GNU C compiler

#

[dep] libc0.3-dev [hurd-i386]
    GNU C Library: Development Libraries and Header Files
or libc-dev
    Virtual package

#

[dep] libc6-dev [not alpha, hurd-i386, ia64]
    GNU C Library: Development Libraries and Header Files
or libc-dev
    Virtual package

#

[dep] libc6-dev-sparc64 [sparc]
    GNU C Library: 64bit Development Libraries for UltraSPARC

#

[dep] libc6.1-dev [alpha, ia64]
    GNU C Library: Development Libraries and Header Files
or libc-dev
    Virtual package

#

[dep] make
    The GNU version of the "make" utility. 

Presumably I should chose libc6.1-dev, but then not sure what choice to make ie alpha or ia64.

Sorry, I'm a real novice.

Thanks for your help.

---

### Post by steffen on 2005-03-21
Use Synaptic

install the linux-headers version that ends with 686, since you're using a Pentium 4 processor.

---

