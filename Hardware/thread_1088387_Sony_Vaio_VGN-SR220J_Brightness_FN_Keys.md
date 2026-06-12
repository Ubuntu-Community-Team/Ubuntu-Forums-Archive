---
title: "Sony Vaio VGN-SR220J Brightness FN Keys"
date: 2009-03-06
forum: Hardware
---

### Post by mortana176 on 2009-03-06
Hello, I have not been able to get my FN keys for brightness working on my laptop. I've searched around on the forums quite a bit. I eventually found a post where someone suggested seeing if the module sonypi would load with:

```
sudo modprobe sonypi
```

He/she then went on explaining other things to check for if it did load, but my problem is that my laptop returned:

```
FATAL: Module sonypi not found.
```

I tried to reply on the other thread, but it told me I was unable to reply for some reason; that's why I have started this new one. My question is: how do I get this sonypi module?

---

### Post by deepclutch on 2009-03-06
there is a module called "sony-laptop" function:
try modinfo sony-laptop .
Sony laptop extras driver (SPIC and SNC ACPI device

---

### Post by mortana176 on 2009-03-06
Output:

```
filename:       /lib/modules/2.6.27-11-generic/kernel/drivers/misc/sony-laptop.ko
version:        0.6
license:        GPL
description:    Sony laptop extras driver (SPIC and SNC ACPI device)
author:         Stelian Pop, Mattia Dongili
srcversion:     12207C6DAC0AF6C53422489
alias:          acpi*:SNY6001:*
alias:          acpi*:SNY5001:*
depends:        
vermagic:       2.6.27-11-generic SMP mod_unload modversions 
parm:           debug:set this to 1 (and RTFM) if you want to help the development of this driver (int)
parm:           no_spic:set this if you don't want to enable the SPIC device (int)
parm:           compat:set this if you want to enable backward compatibility mode (int)
parm:           mask:set this to the mask of event you want to enable (see doc) (ulong)
parm:           camera:set this to 1 to enable Motion Eye camera controls (only use it if you have a C1VE or C1VN model) (int)
parm:           minor:minor number of the misc device for the SPIC compatibility code, default is -1 (automatic) (int)
```

I honestly have no idea what any of this means.

---

### Post by mortana176 on 2009-03-06
Anyone?

---

### Post by mortana176 on 2009-03-06
Please?

---

### Post by Rod-a on 2009-03-16
A blog from David Louis Edelman discusses how to get rid of trial/bloatware from Sony Vaio laptops.  

[http://www.davidlouisedelman.com/technology/vaio-bloatware/](http://www.davidlouisedelman.com/technology/vaio-bloatware/)

According to reply number 16 from Orlin the Fn keys need the Vaio Event Service for these key combinations to work (under Windows). I haven't found any Linux equivalent or work-around. I don't like our chances, but you never know your luck.

Rod

---

### Post by monkeyking on 2010-05-05
For anyone that cares to read this,
the fn+volume fn+brightness is working on 10.04 64bit livecd

---

### Post by wanted.alive on 2010-10-25
Hey people,

I have a Sony Vaio VGN-FW460J, with Ubuntu 10.10, kernel 2.6.35-22-generic.

I'm searching for a week about the problem with brightness keys (Fn+F5 and Fn+F6), and I got nothing until now.

There's a solution that seems to be working for everyone but me, on this site: [http://vaioubuntu.wordpress.com/2008/12/04/finally-a-brightness-how-to-for-vaio-fw-series/](http://vaioubuntu.wordpress.com/2008/12/04/finally-a-brightness-how-to-for-vaio-fw-series/)

The other keys are working just fine. Anyone knows what can I do?


One thing:

When I use acpi_listen, I got this:
 sony/hotkey SNC 00000001 00000010
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011
sony/hotkey SNC 00000001 0000003b
 Two first lines is for Fn+F5. Two last for Fn+F6.

:confused::confused::confused::confused:


Thank you all

---

### Post by maikoi15011 on 2010-11-04
Hey wanted.alive, if you still didn't get the keys to work, I found another solution a few days ago that worked for me on my Sony Vaio F12M1E with Ubuntu 10.04:

Change the grub file at /etc/default/grub so

```
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```says
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
```I've tried many other solutions as well but they didn't work for me.. hope this works for you too ^^

---

### Post by Quackers on 2010-11-04
My brightness keys don't work either. They have never worked from Lucid onwards. One thing I have noticed is that when I look at the Sony-Laptop.ko file is that it is always in the x86 folder. I use 64 bit and am wondering whether that is something to do with the problem. Unless it should work for both. Dunno.

---

