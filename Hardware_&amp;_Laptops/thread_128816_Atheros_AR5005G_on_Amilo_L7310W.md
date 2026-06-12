---
title: "Atheros AR5005G on Amilo L7310W"
date: 2006-02-12
forum: Hardware &amp; Laptops
---

### Post by wickwire on 2006-02-12
Hello,

I've been scouring the web, these forums, gentoo, fedora, you name it, trying to get my wireless built-in card to work with Ubuntu.

My lspci:

```
0000:00:06.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)
        Subsystem: Atheros Communications, Inc.: Unknown device 2052
        Flags: medium devsel
        Memory at 3c000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2
```

Dmesg spits out:
```

[4296273.444000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[4296273.447000] wlan: 0.8.6.0 (EXPERIMENTAL)
[4296273.449000] ath_rate_sample: 1.2
[4296273.455000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[4296273.458000] ACPI: PCI Interrupt 0000:00:06.0[A]: no GSI
[4296273.458000] ath%d: request_irq failed
```


Here's what I've tried so far:

uname -r --> 2.6.12-10-686

I removed the restricted-modules package and installed madwifi-modules-2.6.12-10-686 (having both installed resulted in many errors on dmesg)

I started the OS with kernel parameters "acpi=off", or "pci=biosirq" or "pci=routeirq". dmesg varies a bit but it will still fail to create ath due to irqs..

I tried to find somewhere in the BIOS if the IRQs are being controlled there. Couldn't find any options regarding IRQs.

I'm stuck. I don't know what else to try and I always get that error when loading ath_pci.

Can someone help, please?


EDIT:

I also tried with ndiswrapper, I followed the wiki to the letter, downloaded the drivers, installed, got confirmation of driver/hardware present, and here's dmesg:

```

[4295875.155000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4295875.163000] ndiswrapper: driver neta3ab (D-Link,03/22/2005,4.0.0.1414) loaded
[4295875.163000] ACPI: PCI Interrupt 0000:00:06.0[A]: no GSI
[4295875.645000] ndiswrapper: request for irq 0 failed
[4295875.645000] ndiswrapper (NdisWriteErrorLogEntry:273): log: C000009A, count: 4 (df62f220), return address: f97828c6, entry: f9783050 offset: 4294965366
[4295875.645000] ndiswrapper (ndiswrapper_add_one_pci_dev:188): Windows driver couldn't initialize the device (C0000001)
[4295875.645000] ndiswrapper: probe of 0000:00:06.0 failed with error -22
```

---

### Post by wickwire on 2006-02-13
Ok, after much trying, I figured out that it DOES work as long as I remove the parameter "noapic" from the kernel line in grub.
The reason why I had it is because my USB mouse becomes all sluggish when connected (touchpad works like a charm though).

So, removing "noapic" gives me my wireless connection, but the mouse goes sluggish.

I'm using the madwifi driver from the restricted modules - I'd like to use WEP but it only seems to work without WEP active on the AP.
I'll read some more around here and see what I can find.

Should anyone have an alternative method to using the usb mouse, feel free to let me know.

EDIT:

WEP works out of the box, just went to System --> Administration --> Networking , fill the AP name, place the WEP key (in hexadecimal) and  it worked all right! I was putting an incorrect WEP key... one of the hex values was wrong. :oops:

Next I'll try WPA and see how that goes...! :)

2nd EDIT:

Turns out that the sluggish usb mouse problem extended to fully using the USB ports, couldn't get anything to work at all!

"noapic" would fix the usb ports, and no more stuttering mouse/ usb storage mounting problems BUT no WIFI, irq registering problem!

["irqpoll"]("http://www.ubuntuforums.org/showthread.php?t=81153&highlight=noapic+usb") however solved the problem - WIFI and USB 2.0 are working fine...!

---

### Post by wickwire on 2006-06-04
Ok, since there are so many threads regarding laptop compatibility, I'm taking the opportunity to point out some of the issues between this laptop and Linux.

**irqpoll** on the grub kernel line makes all of these possible, in one go:

USB 2.0;
All USB ports working ( this model has three );
USB mouse not sluggish anymore;
CD/DVD recorder won't "crash" in the middle of a burning session;
Built-in WIFI working with all the rest.

Next, the VIA Unichrome Pro graphics:

Selecting **via** as the xorg.conf driver allowed:

DRI support;
Better 2D performance, especially with totem;
External monitor works, **laptop's own screen stayed black upon gdm loading**. Login is even possible, but nothing more than a black screen to deal with;
Remote GDM login to another Ubuntu box in my LAN works.

Selecting "vesa" as the xorg.conf driver allowed:

Both external monitor and build-in monitor to work;
Poor 2D performance ( totem-wise );
Failed remote GDM login, when trying to access another LAN Ubuntu box.

WIFI performance: very poor, around 150Kbytes/sec.


Recent developments:

Made the transition from Breezy to Dapper.

**irqpoll** issue remains, but it works, so I'm ok;
**via driver** is working with the **_Option "VBEModes" "true"_** in the **Section "Device"** of the **xorg.conf** file;

This means DRI enabled and **no black screen** on built-in screen, must test with the external monitor once I get the chance.

WIFI performance is at 1MByte/sec. Not perfect ( on the same spot, Windows is better ) but it's an improvement all right! :D

I believe that right now, everything's working ( can't say anything about the internal 56.6Kbit modem, don't use it ), even the Function key allows me to control volume and brightness!

The only snag still around is this:

**hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)**

However, the CD/DVD burner is working... :)

Anyways, as far as compatibility goes, it sure looks like this L7310W from Fujitsu-Siemens makes it as linux-friendly! :D:D:D:D:D:D

---

### Post by thoralf on 2007-11-29
> **wickwire said:**
> 
**irqpoll** on the grub kernel line makes all of these possible, in one go:

USB 2.0;
[...]
Built-in WIFI working with all the rest.


just trying to get 7.10 (gutsy gibbon) to work on such a laptop, this issue still persists. 

passing irqpoll to the kernel results in a very significant performance hit - and rightly so, polling for interrupts somewhat defies the very concept of interrupts ...

without irqpoll, it's either having the wlan working but no usb or vice versa.
noapic is necessary to get (hi-speed-) usb working, but when passing this to the kernel, the madwifi driver doesn't find its interrupt. various other options (pci=routeirq, pci=biosirq, pci=enable-busses etc.) didn't help.

is there a way to explicitly tell uhci or madwifi what interrupt they should use? 

> **wickwire said:**
> 
Next, the VIA Unichrome Pro graphics:

I'd suggest using the openchrome-drivers - they enable the (modest, no beryl etc.) 3d acceleration the card provides and work just fine. see [https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome") for details ... i had to edit xorg.conf manually to use this driver, as the deb-package didn't change vesa to via.
btw., installing 7.10 on this laptop required the alternate install cd in my case, as the default via driver used by the live cd installer yielded a blank screen and nothing else.

> **wickwire said:**
> Anyways, as far as compatibility goes, it sure looks like this L7310W from Fujitsu-Siemens makes it as linux-friendly! :D:D:D:D:D:D
naah, that's way to much kudos to fujitsu siemens. the bios plainly sucks, as it doesn't route interrupts properly.

with kind regards,
t.

---

### Post by wickwire on 2007-12-11
Hi there,

I guess your're right, in spite of all the hoops, the BIOS is quite buggy,

I've recently needed to make that laptop functional again, after installing a new harddrive and ran into the same problems you did, using Gutsy...

However, found out a couple of interesting facts:

1- PC LinuxOS 2007 worked right out of the box, wireless + WPA and everything...

But as I'm more of a gnome kinda guy, decided to give Ubuntu another shot

2- As long as you stick with Dapper, everything works with **irqpoll**, and Network Manager will do its job when it comes to WPA networks.

As I haven't had the need to move on to more up-to-date releases, I'll be keeping Dapper installed (I'm writing this post from said system) but I admit it's quite lame to not be able to get a little crazy and update things...!

---

