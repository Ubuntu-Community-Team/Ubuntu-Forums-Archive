---
title: "LG E500 laptop"
date: 2008-07-15
forum: Hardware
---

### Post by rdjse on 2008-07-15
Hi!

I'm having a LG E500 (V.AP77V) laptop with these specs: Intel Core 2 Duo T8100 2.2GHz, 3GB DDR2, 250GB SATA HDD, ATI Mobility Radeon X2600HD 256MB, 15.4"

After installing Windows XP I also tried to install both Ubuntu and Debian Testing without success. The only way to boot the installer and the installed system is with acpi=off. Because this is a laptop I need power management functionality. Simple things like the gnome battery monitor doesn't work and if that doesn't work I guess I will be unable to use power saving functions. 

So my questions is simple, am I able to install Ubuntu or Debian on this laptop and maintain the same functionality I have in Windows (battery monitor, cpu freq. scaling and such)?

Someone also told me to post my lspci along with my question and here it is:
```

    00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
    00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
    00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
    00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
    00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
    00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
    00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
    00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
    00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
    00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
    00:09.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
    00:09.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
    00:09.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
    00:09.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
    00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
    01:00.0 VGA compatible controller: ATI Technologies Inc M76 [Radeon Mobility HD 2600 Series]
    02:00.0 Network controller: RaLink Device 0781
    03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)


```
I appreciate all help I can get, post everything you can think of that may help me! This laptop would be perfect if I only could dual boot Windows and Ubuntu/Debian. 
Thanks // rdj

---

### Post by bhessen on 2008-07-28
Hi rdjse,

You are not alone out there ;-). Sadly, Ubuntu on the LG E500 is possible, but with some major drawbacks right now (no ACPI features).

We had a rather large discussion about this Laptop at the german Ubuntu forum. Maybe you can get a few pointers from the posted codes:

[German LG E500 Thread]("http://forum.ubuntuusers.de/topic/acpi-fix-auf-lg-e500-unter-ubuntu-8.04-funkti/").

LG support is also not very interested in giving bug-free DSDT and SSDT tables because it works ok with Vista.

If you have more questions, feel free to ask.

Regards Benjamin

---

### Post by rdjse on 2008-07-28
Hi! Thanks for your reply. I've actually got Ubuntu to work with ACPI support on my laptop after countless hours. :)

What I first did was that I tried to compile my own kernel and while doing that I discoverd that when I enabled <*> Processor in the ACPI-config I was unable to boot, but if I enabled all ACPI features except this one everything worked out. But I wasn't satisfied with that, I needed <*> Processor to be able to use cpufreqd.

After much reading I found out that passing noapictimer as a kernel parameter both my own kernel and the generic Ubuntu kernel boot and I was able to use ACPI and everything seems to work. I don't really know what noapictimer does, an explanation would be nice. :)

Also the first parameter I used to be able to boot was this one: idle=poll, it worked, but the processor got very hot and the fan was running all the time. 

I've also read that using irqbalance and irqpoll could help with hot processors. But I'm able to boot with only noapictimer but it works with all, ie: kernel-example-2.6.24 noapictimer irqbalance irqpoll. 

But as I said, I'm not sure what these parameters do, but atleast it works. Battery time is a little shorter atm, but I haven't had the time to tweak that much after I got the kernel to boot.

Unfortunate I'm from Sweden so I don't understand German to read that board and see what you came up with.

---

### Post by bhessen on 2008-07-29
Hi rdjse,

Sadly, these parameters don't work for my version of the e500 (V.APSCG, specs: Intel Core 2 Duo T8100 2.1GHz, 2GB DDR2, 250GB SATA HDD, ATI Mobility Radeon X2600HD 256MB, 15.4".

I don't get any ACPI errors with dmesg but things like Standby, Speedstepping etc. still don't work.

Do you have to fix your DSDT ([ACPI-Fix]("https://help.ubuntu.com/community/ACPIBattery")) in order to get it to work?

I haven't tried to compile my own kernel yet (this was something I would have like to avoid ;) ). Do you know a how-to for this kind of problem?

Thanks

Benjamin

---

### Post by rdjse on 2008-07-31
No i did not use any DSDT fix, just a vanilla Ubuntu install with those parameters. But I´m not really sure they work that great. Sure, Ubuntu is able to boot but I think my processor is running hotter than normal. I´ve noticed that when running Windows, its a difference. But I haven´t done any testing yet, that´s just what I feel when I use my laptop, it feels a lot hotter.

---

