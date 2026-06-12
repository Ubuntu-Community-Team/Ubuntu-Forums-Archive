---
title: "Unable to use CPU Frequency scaling on LG E500 laptop"
date: 2008-07-19
forum: Hardware
---

### Post by rdjse on 2008-07-19
Hi!

I'm using a LG E500 laptop with an Intel Core 2 Duo processor. When using the default Ubuntu kernel the only way to boot up is to use acpi=off. I tried to compile my own kernel and almost got it to work. 
If I understand correctly I need to enable this in the kernel config to be able to change CPU speed:
```

<*> ACPI (Advanced Configuration and Power Interface) support     [INDENT]<*>Processor[/INDENT] 

```
And
```

<*> CPU Frequency Scaling
[INDENT]<*> ACPI Processor P-states driver[/INDENT]

```
Without the <*> Processor enabled I wont get access to ACPI P-states driver. 
The problem with enabling the Processor-thingy in ACPI menu is that my kernel is unable to boot. When I enabled Processor and Processor P-states driver kernel stops without any real error message. Boothing this kernel with acpi=off works, but then I dont't have any power saving functionality at all.  The last lines before it stops booting are:
```

1.959333 cpuidle: using govenor ladder
1.959333 cpuidle: using govenor menu
1.961333 Marking TSC unstable due to TSC halts in idle

```
And then... Nothing. 
Here's my lspci too:
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
I don't know what to do, I really need to change processor speed or else I'm unable to run the laptop on battery power, and that's really crappy.
Does this mean that I'm stuck with Windows or is there some way to get all this to work? I really appreciate any help on this. Thanks! //rdj

---

### Post by rdjse on 2008-07-19
I just found out that passing "idle=poll" as a boot parameter the kernel starts normally and CPUfreq is working, but I have no clue what this actually does. Anyone care to explain? :)

---

### Post by AFarris01 on 2008-08-06
Im not positive, but i believe that this has something to do with setting a condition where the kernel monitors the activity level of the computer, then reports that level so cpufreq can scale the CPU appropriately.  like i said, not positive, but that seems logical.

---

