---
title: "Powering on the Sony TX750 GPRS Modem"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by sheaiden on 2007-10-19
I am finding I need help in breaking the chains of windows...

I recently decided to move to Linux on my work Laptop.  I have a Sony VGN-TX750P/B, and All is working fine with the exception of the built-in (internal) GPRS Modem; it either won't power on, or I don't know where to find its configuration items.  I saw the thread by OutdoorIcon, regarding installing Breezy on a tx650 (almost identicle to my machine), but though some people stated they got the modem to power on, no one detailed HOW they got it to power on.  

I know that the sony_laptop module is included in Gutsy's kernel, and according to the sonypi and sony_laptop website, "Some newer Vaio models (currently some SZ models) have an integrated GPRS/EDGE modem that can be powered on/off by writing 1 (enable) or 0 (disable) to /sys/devices/platform/sony-laptop/wwanpower"  

The issue I'm running into is that this wwanpower file doesn't exist.  I have a few other entries under platform/sony-laptop, namely 
[LIST]
[*]Brightness default
[*]cdpower (this works well, simply echoing 1 or 0 to it)
[*]uevent
[*]and the power directory
[/LIST]

I am coming from a background of using and administering Gentoo and Solaris, and so am used to totally custom configurations of the kernel from source (e.g. Gentoo) or totally out-of-your-hands kernel configurations (e.g. Solaris).  I've never worked with kernel modules (I know, I know....but I've always ended up just going monolithic on my gentoo boxes...), and more importantly, I've never worked with packages for those kernels or their modules; I have linux-source installed via synaptic, but I can't get "make menuconfig" running...so answers in the line of "Just make sure you're using sony-laptop" are not usefull to me...I need to know what to do to ensure I'm using them to their full potential.  

I have done Google searches, searched the forums here, and not found any conclusive posts...can someone help me get rid of Windows?  the only purpose it serves is to allow me to use my gprs data plan when I'm on call and not at home...


Edit: I thought it may be usefll to post the dmesg lines regarding the sonypi and sony-laptop:

[   40.312000] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   40.316000] sonypi: please try the sony-laptop module instead and report failures, see also [http://www.linux.it/~malattia/wiki/index.php/Sony_drivers](http://www.linux.it/~malattia/wiki/index.php/Sony_drivers)
[   40.316000] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[   40.316000] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[   40.316000] sonypi: device allocated minor is 63
[   40.376000] input: Sony Vaio Jogdial as /class/input/input6
[   40.404000] input: Sony Vaio Keys as /class/input/input7
[   40.520000] sony-laptop: Sony Notebook Control Driver v0.5.
[   40.552000] input: Sony Vaio Keys as /class/input/input8
[   40.568000] input: Sony Vaio Jogdial as /class/input/input9
[   40.896000] Failure registering capabilities with primary security module.

---

### Post by nyc_863 on 2007-10-19
I have a txn which included the sprint WWAN and i have the wwan_power entry I can turn the light on and off but I didn't bother playing with it because somewhere I read there is no device driver to use this, and nor is there likely to be. I imagine it is the same with the GPRS integrated WWAN as well.

---

### Post by sheaiden on 2007-10-19
Are you running Gutsy?  Did you do anything special?  or was it just a plain install?

I wonder if the sony-laptop plugin only worked with the models that have sprint modems...I will worry about drivers once I get the thing powered on-can't even play with it till I get it powered on...

I should have been more specific, by the way; I run and have been running Gutsy (since beta).

Edit:
I just found the post by Sergio regarding his patches to sonypi, spicctrl, etc...he put his patches for his 650 (fully working, by the way) on his site, at [http://sergio.spb.ru/vaio](http://sergio.spb.ru/vaio), but he doesnt' have patches out for kernel 2.6.22 series, only through .21....so I can't use that patch, and I don't know enough about kernels and modules to patch it myself.  Either way, this should be unnecessary, since the sony-laptop module is set to replace the sonypi module, and sony-laptop should be providing the hooks necessary to turn on the modem, according to the author's site.

---

### Post by nyc_863 on 2007-10-19
I am running gutsy, I stopped sonypi loading by removing the modprobe from the hotkeys startup, if I remember that got me more device entries such as bluetoothpower. But, again, even if you can get at the power (on or off) of either WWAN circuitry, I'd bet that it is pointless as there is no linux driver for it, nor is there ever likely to be.
By the time someone did some work to reverse engineer how the chipset works they'd come out with a new version for newer laptops anyway.
All I wanted to do was to power off anything I could to save power when the laptop is running.

---

### Post by sheaiden on 2007-10-21
Well, following your advice, I stopped sonypi from loading; not sure why it was loading considering I still have the ability to do everything pi was doing via laptop...

anyways, I can now power the WWan on, and I will explore Sergio's method of using the connection-he posted that he got his working properly and got connected.  I'll post back here if I figure it out.

---

### Post by docrohith on 2007-11-04
I am new to linux. gusty on vaio vgn-sz480. Please explain how I can stop sonypi from loading. Thanks.

---

### Post by Daelyn on 2008-01-22
> **docrohith said:**
> I am new to linux. gusty on vaio vgn-sz480. Please explain how I can stop sonypi from loading. Thanks.

```
 sudo rmmod sonypi 
```
will remove sonypi from your currently running session.

If you "comment" out "sonypi" in /etc/modules that will stop it from loading at every boot.

---

### Post by mannunix on 2008-02-19
You can stop sonypi from being loaded by commenting out the "modprobe sonypi;" line in /etc/init.d/hotkey-setup (as mentioned by nyc_863 in earlier post). See example below:

```

        Sony*)
        #modprobe sonypi; # Needed to get hotkey events
        modprobe sony-laptop
        ;;

```

---

