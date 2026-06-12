---
title: "Need help with a graphics card (9800gt)"
date: 2015-12-30
forum: Hardware
---

### Post by lovelinuxlol on 2015-12-30
I have Ubuntu 14.04 LTS, and I have a 9800 GT Nvidia graphics card I want to use. I have a HP Envy 700 I installed Linux on because the WIndows 8.1 wouldn't recognize the graphcis card (it'd just go black). Well it's doing the same thing it's just a black screen, I've had the graphics card checked out by multiple PC shops they've all said it's good. I'm on a wireless connection, is there a way I can Download and install the drivers and then install the graphics card??? I've only set it up via the find/update drivers in the past, but that's when the screen was working and on a older computer.

---

### Post by Bashing-om on 2015-12-30
lovelinuxlol; Hello;

That card takes the 340 version driver, It is available in the 14.04 software repository.

Try this:
Boot the liveDVD(USB);

At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> f6 key (other options) -> arrow down to the preset option(s)space or enter to accept and then the escape key to exit; 
Try "nomodeset" at this time; for other additions the boot options kernel boot line is now available, one may append "other" desired boot parameters to the end of the line that are not present in the "presets".
Enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.

-> Additional Drivers, location varies depending on the version, ->locate the Additional Drivers utility and install the recommended driver.

If this works in the live environment we can make it work in the install !..
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) on how to use this parameter

[INDENT][INDENT][INDENT]hope this helps
[/INDENT][/INDENT][/INDENT]

---

### Post by lovelinuxlol on 2015-12-30
I've managed to install the drivers and then shut down and install the card, now when I boot up it shows the loading screen and then goes straight black. Unfortunately This is all I currently have, so I'm forced to shut off take it out and start it up in order to read these forums lol so if possible I'd like to just do everything via the terminal and then reinstall and hopefully it will load properly. Currently my own board graphics display won't go beyond 1024 x 768 (4:3) which is also annoying considering in windows it could go much larger (I have a 39 inch Monitor that's currently cropped off the sides, however the graphics cards displays the desktop on the entire thing.

---

### Post by Bashing-om on 2015-12-30
lovelinuxlol; Hummm ...

Best show us what we are working with;

With the Nvidia card installed.
Reboot the install; as soon as the bios screen clears depress a shift key -: grub boot menu,
with a latest kernel selected to boot, press the 'e' key for edit mode -> boot parameters screen;
In this screen arrow down to the line starting with linux and across to quiet splash, replace these terms with the term 'text' with out the quotes. Key combo ctl+x to continue the boot process to terminal (TTY1).

Login here with username and password - no result on screen when pass word is entered, enter your password blindly and hit the enter key.

Now we need a convenient means to relay requested outputs, we have a pastebin site to fulfill that need.
In terminal do:
```

sudo apt-get install pastebinit

```
to install the tool.


Now we "see" by:
Terminal commands:
```

lspci -vnn | grep -i VGA | pastebinit
sudo lshw -C display | pastebinit

```
The results are URLs back in the terminal. Pass those links back here in the thread and we access these files to know.

Then we see where we go from here.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by lovelinuxlol on 2015-12-30
> **Bashing-om said:**
> lovelinuxlol; Hummm ...

Best show us what we are working with;

With the Nvidia card installed.
Reboot the install; as soon as the bios screen clears depress a shift key -: grub boot menu,
with a latest kernel selected to boot, press the 'e' key for edit mode -> boot parameters screen;
In this screen arrow down to the line starting with linux and across to quiet splash, replace these terms with the term 'text' with out the quotes. Key combo ctl+x to continue the boot process to terminal (TTY1).

Login here with username and password - no result on screen when pass word is entered, enter your password blindly and hit the enter key.

Now we need a convenient means to relay requested outputs, we have a pastebin site to fulfill that need.
In terminal do:
```

sudo apt-get install pastebinit

```
to install the tool.


Now we "see" by:
Terminal commands:
```

lspci -vnn | grep -i VGA | pastebinit
sudo lshw -C display | pastebinit

```
The results are URLs back in the terminal. Pass those links back here in the thread and we access these files to know.

Then we see where we go from here.
[INDENT][INDENT]where there is a will there is a way
[/INDENT]
[/INDENT]

Yeah, I think I'm just going to buy a new card. Is there any way to fix the resolution issue??? The update drivers doesn't detect anything but my built in wireless. Thanks for the help on the previous issue though.

---

### Post by Bashing-om on 2015-12-30
lovelinuxlol; Welll ...

Show us what we are working with hardware wise, then we can give the more specific advise.
Does the system even see the Nvidia graphic's card ?
What does the system report for the onboard card ?
Post the requested commands outputs.

That 9800 GT is well supported, should have no problem IF the system sees it !

Once we know the hardware we can give the more specific advise for setting a different resolution .

[INDENT][INDENT]only as good as the tools we work with
[/INDENT][/INDENT]

---

### Post by lovelinuxlol on 2015-12-30
courage-700-414           
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 11GiB
     *-cpu
          product: Intel(R) Core(TM) i5-4570 CPU @ 3.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 3200MHz
          capacity: 3200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt cpufreq
     *-pci
          description: Host bridge
          product: 4th Gen Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 06
          width: 32 bits
          clock: 33MHz
          configuration: driver=hsw_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:33 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
        *-usb:0
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB xHCI
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:29 memory:f7e00000-f7e0ffff
        *-communication
             description: Communication controller
             product: 8 Series/C220 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:32 memory:f7e1a000-f7e1a00f
        *-usb:1
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7e18000-f7e183ff
        *-multimedia
             description: Audio device
             product: 8 Series/C220 Series Chipset High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:34 memory:f7e10000-f7e13fff
        *-pci:0
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:2000(size=4096) memory:df200000-df3fffff ioport:df400000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 memory:f7d00000-f7dfffff
           *-network
                description: Wireless interface
                product: BCM43142 802.11b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 74:29:af:e7:89:f5
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=10.0.0.35 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:17 memory:f7d00000-f7d07fff
        *-pci:2
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:e000(size=4096) memory:f7c00000-f7cfffff ioport:f0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 0c
                serial: 7c:05:07:93:93:ae
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:31 ioport:e000(size=256) memory:f7c00000-f7c00fff memory:f0000000-f0003fff
        *-usb:2
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7e17000-f7e173ff
        *-isa
             description: ISA bridge
             product: H87 Express LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:30 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7e16000-f7e167ff
        *-serial UNCLAIMED
             description: SMBus
             product: 8 Series/C220 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7e15000-f7e150ff ioport:f040(size=32)
  *-scsi
       physical id: 1
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage

---

### Post by Bashing-om on 2015-12-30
lovelinuxlol; Welp;


No sign of the Nvidia card ( lspci is the better way to see ).

Running on Intel and the driver is loaded.
> 
configuration: driver=i915

 Intel supports us very well. In linux Intel " just works "

Maybe in bios turn on/off the PCI video device -
If the Nvidia card is removed, and disabled in bios, does the resolution correct ?

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by lovelinuxlol on 2015-12-30
> **Bashing-om said:**
> lovelinuxlol; Welp;


No sign of the Nvidia card ( lspci is the better way to see ).

Running on Intel and the driver is loaded.

 Intel supports us very well. In linux Intel " just works "

Maybe in bios turn on/off the PCI video device -
If the Nvidia card is removed, and disabled in bios, does the resolution correct ?
[INDENT][INDENT]just my thought
[/INDENT]
[/INDENT]


Well I Removed the Nvidia card before I did that, and yeah it's still not giving me any options. when I put xrandr in this it is what it gives me 

courage@courage-700-414:~$ xrandr
Screen 0: minimum 8 x 8, current 1024 x 768, maximum 32767 x 32767
HDMI1 disconnected (normal left inverted right x axis y axis)
VGA1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
courage@courage-700-414:~$ 


The screen I'm using is a TV and worked fine in windows, but I honestly prefer using linux. So basically what I'm looking at right now is a box with two black bars on the left and right side, It's not stretching the entire length of the monitor.

---

### Post by Bashing-om on 2015-12-30
lovelinuxlol; Welll ...

TV as the monitor casts a different light on the matter.
Often times there is a setting on the TV to accommodate the input source as a computer. Have you looked ?

Mind ya
[INDENT][INDENT]I just do not know - everything
[/INDENT][/INDENT]

---

### Post by tokyobadger on 2015-12-30
I'd suggest the following

1) Put the 9800GT back in the PC
2) Switch off the Intel graphics (built-in to the CPU) in the BIOS <-- I know that the card claims Hybrid technology but I'd focus first on getting the card to work in Ubuntu
3) Clean out all your previous efforts to install nvidia drivers [ see posts #3, #7, #9](http://ubuntuforums.org/showthread.php?t=2307693)
4) Make sure you have the right "tools" to build the drivers ```
sudo apt-get install linux-source linux-headers-generic
```
5) Install nvidia-340 drivers (those are the newest that support the 9800GT) from the Ubuntu repository ```
sudo apt-get install nvidia-340 nvidia-settings
```
6) run nvidia-xconfig ```
sudo nvidia-xconfig
```
7) edit your /etc/default/grub to include the nomodeset flag and add your resolution - see link in #3 above
8) update grub
9) reboot

The resolution for the TV and the hybrid graphics mode I'd tackle later and honestly I'd step aside for someone who has experience to guide you

---

