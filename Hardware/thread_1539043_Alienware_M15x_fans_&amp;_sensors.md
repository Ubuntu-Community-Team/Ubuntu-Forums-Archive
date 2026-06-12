---
title: "Alienware M15x fans &amp; sensors"
date: 2010-07-26
forum: Hardware
---

### Post by GhodMode on 2010-07-26
I'm using an Alienware M15x with Kubuntu 10.04, Lucid Lynx.  For the most part, it has been working wonderfully, but often X (not the whole computer) will restart for no reason.  I've monitored ~/.xsession-errors from a virtual console while it happened and I didn't see any meaningful messages like a segfault or anything, but that file seems to fill very quickly and I might've missed something.

I think the problem is related to cooling.  I never hear the fans speed up while using Linux, but it happens often when I'm using Windows (dual-boot).  I originally thought this was due to greater efficiency under Linux.

Based on the assumption that the problem is related to cooling, I've been trying to search and read to figure this out without much luck. I've installed lm-sensors, pwmconfig, & fancontrol.  I don't really know how to use them, but sensors-detect reports "Sorry, no sensors were detected" and I think that the other two utilities depend on the functionality of lm-sensors.

So, I guess it's a hardware compatibility issue?

Does anyone have any ideas how I might make lm-sensors work with this laptop, or some other way to get better control over the laptop's inbuilt cooling system?

Thank you.

--
-- Ghodmode

---

### Post by juancarlospaco on 2010-07-26
Maybe a problem of the DE (?)

Try a LiveCD with Gnome.

---

### Post by GhodMode on 2010-07-26
Is "DE" "Desktop Environment" in this context?  That wouldn't explain why lm-sensors isn't working since that operates separately from the desktop environment.

I'll still give the live CD idea a try, though.  It might be difficult to reproduce the problem.  Since the LiveCD environment won't have most of my normal applications, I won't be able to put it under a similar load, but I'll try opening several browser tabs and play a video and see if I can get something to happen.

If it does turn out to be a problem with the desktop environment, that helps me narrow down the source of the problem, but it doesn't help me find a solution.

Thank you.

--
-- Ghodmode

---

### Post by mdog on 2010-08-18
I too have an M15x (i5-540m + gtx 260m) and never hear the fans spin up. They run, but even with 4 burnBX threads running (1 for each core/hyperthread), my system fans never speed up. The exhaust gets quite hot though.

Attempting to load each driver in /lib/modules/2.6.32-24-generic-pae/kernel/drivers/hwmon yields no more results with sensors-detect.

It is kind of frustrating if the fans are not controlled by the bios in response to a heat sensor.

```

# lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:19.0 Ethernet controller: Intel Corporation 82577LC Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
02:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 260M] (rev a2)
07:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
09:07.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:07.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:07.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:07.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

---

### Post by skullmunky on 2010-09-09
hi,

any other news on this?  I'm looking at buying the same model, but am reconsidering if there's cooling problems.

---

### Post by GhodMode on 2010-09-18
> **skullmunky said:**
> hi,

any other news on this?  I'm looking at buying the same model, but am reconsidering if there's cooling problems.

I haven't heard anything new about this and I've all but given up.  I've even switched to Windows most of the time on this particular computer because I'm concerned about it overheating.

I'm pretty sure this isn't actually a hardware problem.  It's just a lack of support.  I even wrote a blog post about this experience: [Why Do I Have To Use Windows?]("http://www.ghodmode.com/blog/2010/08/why-do-i-have-to-use-windows/") :icon_frown:

---

### Post by HunterThomson on 2010-11-23
Pluss +1

I have tried everything. No matter what I do these directories stay empty...

/proc/acpi/thermal_zone
/proc/acpi/power_resource

And The fan directory is only created when I modprobe fan ,but even then it is just and empty directory.
/proc/acpi/fan

The Nvidia grafics card seems to controle it's fan by itself but the CPU fan stays at a low speed 24/7 even though it is burnning hot.

I am using Arch Linux on Kernel 2.6.35.8

---

### Post by esplinter on 2010-11-29
I am having the same problem in a friend´s alienware m15x.

All the hardware works perfect out of the box using ubuntu lucid but there is still this ugly bug which makes linux unusable. The computer works perfectly but suddenly the X system restart when it gets hot.

It is a really pain because this is the only reason to not use ubuntu linux in this computer and my friend would prefer to use linux :(

---

### Post by c00lwaterz on 2010-11-30
it is sad part when it has no support. afaik that alienware is under dell and dell is one of the largest company that supports linux? im not good at this point but i want to know what happens to alienware (under dell) that should have support for linux. :( I thought of this alienware as option to future when i buy new laptop and I did not know that there still issue even it is dell. sad part only.

---

### Post by netman_zion on 2011-05-18
I  have a  Alienware m15x Geforce GTX 260m with Ubuntu 11.04 latest Nvidia driver 270.41.06 and still have the same problem just random X server crash that make Linux really unstable

Any one got a solution ?

---

### Post by Alunduyn on 2012-11-28
Up. I don't want to start a new thread, but this issue is still here. Ubuntu 12.04.1, Alienware m15x. *pwmconfig* gives this error :
```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```
So I can't run fancontrol
```
Loading configuration from /etc/fancontrol ...
Error: Can't read configuration file
```
Is there any other way?

I followed [this guide](http://askubuntu.com/questions/22108/how-to-control-fan-speed).

I really like Ubuntu : it is faster and smoother and better than Windows in everything that is not playing ( for that I boot Windows ). Having to return to it for a cooling issue would be very sad...

---

