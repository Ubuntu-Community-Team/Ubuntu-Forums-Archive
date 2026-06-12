---
title: "Can't seem to get my ac97 modem to work"
date: 2005-07-25
forum: Hardware &amp; Laptops
---

### Post by delltony on 2005-07-25
I will be doing a lot of travel with my new job and I need to have a way to access email and all using uhum "dialup".  I'm almost certain this is a winmodem so here is what i have done thus far.
Output of scanModem is as follows
```

DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.04 "Hoary Hedgehog"  kernel 2.6.10-5-686-smp
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at DISCUSS@linmodems.org
Code updated on:  2005_July_21
------------ --------------  System information ------------------------
 Ubuntu 5.04 "Hoary Hedgehog" 
 on System with processor: i686
 currently under kernel:   2.6.10-5-686-smp

There are emerging complications under 2.6.10 and later kernels. 
Concerning Intel-536ep and 537
   http://www.ubuntulinux.org/wiki/IntelFiveThreeSixEPModemHowto/ 
   http://linmodems.technion.ac.il/archive-fifth/msg00280.html
   http://linmodems.technion.ac.il/archive-fifth/msg00881.html
   
 The kernel was assembled with compiler:  3.3.5
 with current System compiler GCC=3.3.5
    /usr/bin/gcc -> gcc-3.3

A package kernel-kbuild-2.6-3 or later version must be installed to support compiling

Checking for kernel-headers needed for compiling.
The kernel-headers have base folder: 
/lib/modules/2.6.10-5-686-smp/build -> /usr/src/linux-headers-2.6.10-5-686-smp
/usr/src/linux-headers-2.6.10-5-686-smp
Please install the package WVDIAL for modem testing and dialout.

 A /dev/modem symbolic link is not set.
 USB modem not detected.

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

Modem candidates are at PCI_buses:  0000:00:1f.6
    
Providing detail for device at  0000:00:1f.6
  with vendor-ID:device-ID
     ----:----
Class 0703: 8086:24d6   Modem: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
  SubSystem 14e4:4d64   Broadcom Corporation: Unknown device 4d64
0000:00:1f.6 0703: 8086:24d6 (rev 02)
 Flags: medium devsel, IRQ 17
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 8086:24d6 14e4:4d64 debian 2.6.10-5-686-smp  3.3.5 3.3.5    i686

       
 The soft modem Subsystem operates under a controller
   8086:24d6 82801EB ICH5 
 capable of supporting under Linux AT LEAST modem Subsystem chips from manufacturers:

 Conexant
 Intel
 Smartlink
Use the SmartLink slmodem software for support.
For this Broadcom subsystem modem, the slmodemd daemon must be used in ALSA mode
 slmodemd --alsa --country=YOURS hw:1

 Smartlink software in ALSA mode may support this modem 

  Driver snd-intel8x0m  may enable codec acquisition 

```

I then went and tried to install sl-modem-daemon and get a borked message
```
sl-modem-daemon depends on sl-modem-modules-new | sl-modem-source (>> 2.9.6-1);
 however:
  Package sl-modem-modules-new is not installed.
  Package sl-modem-modules-2.6.10-5-386 which provides sl-modem-modules-new is n
ot configured yet.

```

I am running 2.6.10-5-686-smp and help would be appreciated.

---

