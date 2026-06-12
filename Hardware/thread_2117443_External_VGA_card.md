---
title: "External VGA card"
date: 2013-02-18
forum: Hardware
---

### Post by jman86 on 2013-02-18
I just got this USB 2.0 External VGA Video Card GUC2015CV from IOGEAR. Im running ubuntu 10.04.1 LTS I cant seem to get hardware to detect Looks the like they made the drives for windows and mac

---

### Post by jman86 on 2013-02-18
Help

---

### Post by sanderj on 2013-02-18
Why do you want to use that hardware?

Why such an old Ubuntu version?

What is your Linux Experience?

What have you done to solve this yourself?

---

### Post by jman86 on 2013-02-18
> **sanderj said:**
> Why do you want to use that hardware?

Why such an old Ubuntu version?

What is your Linux Experience?

What have you done to solve this yourself?

What is this a Q&A session

---

### Post by sanderj on 2013-02-18
> **jman86 said:**
> What is this a Q&A session

Yep. Or to be more precise: an assessment of your situation.

---

### Post by jman86 on 2013-02-20
Why do you want to use that hardware? Dual Monitor

Why such an old Ubuntu version? Did not now that

What is your Linux Experience? Low 

What have you done to solve this yourself? I googled ways to convert windows drives to linux

---

### Post by QIII on 2013-02-20
Let's keep this civil.

sanderj -- a bit less terse an introduction might be welcomed by a new user.

jman86 -- sometimes it is helpful to get some information from someone who has a question to avoid just taking wild stabs in the dark.

Shake it off, take a deep breath and get to the solution.  

Thanks.

---

### Post by sanderj on 2013-02-20
> **jman86 said:**
> Why do you want to use that hardware? Dual Monitor

OK, clear. Is putting in a VGA-adapter into your computer an option? I expect that to be plug-and-play.

> **jman86 said:**
> 
Why such an old Ubuntu version? Did not now that

Yes: Ubuntu is already at 12.10. A newer version means more bug fixes and more features.


> **jman86 said:**
> 
What is your Linux Experience? Low 

What have you done to solve this yourself? I googled ways to convert windows drives to linux

Open a terminal, and type:
```
lsusb

```
and post the output here.

When you plug in the adapter, does there appear a green indicator in the upper right corner of your Ubuntu 10.04?

---

### Post by jman86 on 2013-02-20
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 17e9:0058 Newnham Research 
Bus 005 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 004 Device 002: ID 04d9:1702 Holtek Semiconductor, Inc.

---

### Post by sanderj on 2013-02-20
OK. Now unplug the external VGA, run 'lsusb' again, post it, and see which entry is missing; that's the USB-ID of your VGA device.

Aren't you forgetting my other question?

EDIT: and in the meantime, can you download Ubuntu 12.10 and write it to CD / USB-stick?

---

### Post by jman86 on 2013-02-20
Correction its ubuntu 12.04.1 LTS 

Bus 001 Device 002: ID 17e9:0058 Newnham Research is missing after usb vga adpater comes unplugged 

DisplayLink comes up when I did a search on "Newnham Research"

---

### Post by sanderj on 2013-02-20
OK. When I google "17e9:0058" in combination with Linux or Ubuntu, not much shows up. That's a bad sign.

Next step: 
make sure Ubuntu is running (unplug the USB VGA device it is connected), 
open a terminal, and type 'dmesg'. Note the last line: remember / write down the number on the left.
Now plug in the USB VGA device. Type 'dmesg' again, and copy paste everything that happened since you plugged in the device. Post that info here.


And ... can you answer my question about plugging in a PCI VGA card ... ?

---

### Post by jman86 on 2013-02-20
Bus 001 Device 002: ID 17e9:0058 Newnham Research is missing

---

### Post by jman86 on 2013-02-20
[QUOTE=sanderj;12520607]OK. When I google "17e9:0058" in combination with Linux or Ubuntu, not much shows up. That's a bad sign.

Next step: 
make sure Ubuntu is running (unplug the USB VGA device it is connected), 
open a terminal, and type 'dmesg'. Note the last line: remember / write down the number on the left.
Now plug in the USB VGA device. Type 'dmesg' again, and copy paste everything that happened since you plugged in the device. Post that info here. 

[174717.200852] udlfb: freeing dlfb_data f6a1c800

And ... can you answer my question about plugging in a PCI VGA card ... ?[/QUOTE

It dose not have a any PCI slots

---

### Post by sanderj on 2013-02-20
> **jman86 said:**
> Bus 001 Device 002: ID 17e9:0058 Newnham Research is missing


That's all that dmesg shows? Nothing else?

If so, that doesn't look great. You could google that line to see if you find anything.

You could also dive into NDISwrapper ([http://en.wikipedia.org/wiki/NDISwrapper](http://en.wikipedia.org/wiki/NDISwrapper)), but I'm not sure that is going to work.

HTH

---

### Post by sanderj on 2013-02-20
> **jman86 said:**
> 
It dose not have a any PCI slots

Any other slots? ISA? VESA? PCMCIA?

What kind of system is it?

---

### Post by sanderj on 2013-02-20
PS:

[http://karuppuswamy.com/wordpress/2010/07/19/how-to-get-lilliput-displaylink-based-usb-monitor-um-70-17e902a9-working-in-ubuntu-linux/](http://karuppuswamy.com/wordpress/2010/07/19/how-to-get-lilliput-displaylink-based-usb-monitor-um-70-17e902a9-working-in-ubuntu-linux/) might be useful, but it's dmesg shows much more than yours ...

---

### Post by jman86 on 2013-02-20
[QUOTE=sanderj;12520714]Any other slots? ISA? VESA? PCMCIA?

What kind of system is it?[/QUOTE

I dont think there is

---

### Post by jman86 on 2013-02-20
> **sanderj said:**
> That's all that dmesg shows? Nothing else?

If so, that doesn't look great. You could google that line to see if you find anything.

You could also dive into NDISwrapper ([http://en.wikipedia.org/wiki/NDISwrapper](http://en.wikipedia.org/wiki/NDISwrapper)), but I'm not sure that is going to work.

HTH
tryed that already did not work

---

### Post by jman86 on 2013-02-20
174717.200852 is what I get on the last line after entering dmesg on the last line

---

