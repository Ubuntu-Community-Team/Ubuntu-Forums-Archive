---
title: "Dell Inspiron 8200 Constantly Freezing"
date: 2009-05-11
forum: Hardware
---

### Post by italianoman421 on 2009-05-11
I have a dell Inspiration 8200 running 9.04 that is constantly freezing. I have cleaned the computer of dust using the compressed air cans you can buy. So at this point I have only a limited idea about why it could be freezing. One possibility is that the fans do not seem to be running very often but when I went to download a driver to increase their run time the computer froze within five minutes of turning it on, so I do not think over heating could be a problem.

What other possiblities could it be?

I understand that the post is vauge leaving many possible problems, so any advice on how to narrow down the potential problems would greatly appreciated.

Thanks

---

### Post by italianoman421 on 2009-05-11
Sorry To bump the post, but any feedback about system freezing is appreciated.

---

### Post by Sambie on 2009-05-11
Can you show us your computer's information? go to termina. After going to super user (Sudu su) type in lshw.

---

### Post by italianoman421 on 2009-05-11
This is the computer info that popped up after hitting command ~ lshw

description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 1
          size: 383MiB
     *-cpu
          product: Mobile Intel(R) Pentium(R) 4 - M CPU 1.70GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@0
          version: 15.2.7
          size: 1200MHz
          capacity: 1200MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display
                description: VGA compatible controller
                product: NV11 [GeForce2 Go]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: b2
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801CA/CAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801CA/CAM USB Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-network
                description: Ethernet interface
                product: 3c905C-TX/TX-M [Tornado]
                vendor: 3Com Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 78
                serial: 00:08:74:3e:5f:2f
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=3c59x ip=192.168.0.5 latency=32 maxlatency=10 mingnt=10 module=3c59x multicast=yes
           *-pcmcia:0
                description: CardBus bridge
                product: PCI4451 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-pcmcia:1
                description: CardBus bridge
                product: PCI4451 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1.1
                bus info: pci@0000:02:01.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCI4451 IEEE-1394 Controller
                vendor: Texas Instruments
                physical id: 1.2
                bus info: pci@0000:02:01.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
        *-isa
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801CAM IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801CA/CAM AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
     *-network
          description: Wireless interface
          product: RTL8180L 802.11b MAC
          vendor: Realtek Semiconductor Co., Ltd.
          physical id: 0
          bus info: pci@0000:07:00.0
          logical name: wmaster0
          version: 20
          serial: 00:09:5b:8a:79:82
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list logical ethernet physical wireless
          configuration: broadcast=yes driver=rtl8180 ip=192.168.0.126 latency=64 maxlatency=64 mingnt=32 module=rtl8180 multicast=yes wireless=IEEE 802.11b
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 0e:15:42:df:c5:1f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
dominick@dominick-laptop:~$

---

### Post by italianoman421 on 2009-05-12
Was this the right info I needed to supply to figure out possible reasons for constant freezing?

---

### Post by db8200 on 2009-06-08
Hello italianoman421,

I think we have to share information about this problem. I own an Inspiron 8200 since 2002 and since about two years it is freezing randomly.
I always used Mandriva Linux on this computer, and kept it up to date.
Since the problem does not appear systematically, it's hard to know when it appeared.

To describe it well:
after running correctly during (sometimes 5 minutes, sometimes various hours), the computer freezes when an user interaction is done via mouse or keyboard, with the effect of opening or closing a window, or even typing a character.
A version of XFCE Terminal that I was using in early 2009 was great in causing this problem, almost systematically.
The result after freezing is a "normal" screen, exactly as it was before, with nothing moving, mouse freezed, keyboard useless (even for Ctrl+Alt+F1), Num Lock haviing no effect on the LED, and network card not answering to any packet.
The only solution is to shut the laptop down using the power button.

I suspected:
- the RAM. I ran memtest and all was OK. I didn't take the time to remove a RAM module.
- heating problems
- other hardware problems
- the graphics driver. I tried free and propietary drivers, with various settings. Nothing changed.
- the kernel: a change in the kernel could cause this specific hardware to work bad. Maybe setting an option or correcting a piece of code could solve the problem.

Currently I think that it could be caused by the kernel. Maybe I should try an old kernel and/or an old distribution to see how it works. But I will have to let it run and interacting during many hours before to be sure that there is no problem with a given kernel release.

If we find more people having the same problem, it can help us.

Here is the output of lspci on my laptop:
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller

What is your graphics card?

Regards,
db

---

### Post by hackerlife on 2009-06-19
Hey guys, I recently upgraded to Ubuntu 9.04, but am still having the same issues that you are.
What is common between us all is our nvidia geforce2 go card.
What worked for me was disabling it (although this means no 3D effects!!!!)
I am slowly looking for a fix to this issue, but it seems to be the driver.

-Will

---

### Post by tbonedude on 2009-07-22
I was having the same problem with my inspiron 8200.  My hard drive died on me yesterday, so I replaced the drive with a different one, did a clean re-install, and now it no longer randomly freezes.  As a note, it used to freeze randomly for no apparent reason in ubuntu, fedora, and windows.  Not anymore \\:D/ .

---

### Post by SvenAnderson on 2009-11-17
Was there a solution posted to this issue.  I have the same problem with my Dell Inspiron 8200 freezing.  I've tried a variety of window managers and removal of various effects, but I still get persistent freezes that require pushing the power button.

---

### Post by ecojd811 on 2010-07-05
Anyone have a reason for the freeze?  My 8200 has frozen randomly since installing linux on it about 2 years ago.  Currently running Ubuntu 10.04 and it still does from time to time.  The past two times have been within 5 seconds of launching System Monitor?

I dual boot with XP and it has never frozen with Windows.

---

### Post by ecojd811 on 2010-07-05
After some more trial and errors it seems that ANYTIME I start System Monitor and select the Resources tab my Inspiron 8200 will go into a hard freeze.  I clicked on System tab, no problem...  Processes tab, no problem...  File Systems tab, no problem  but within 10 seconds of selecting the Resources tab I get a hard freeze.  Not blaming this app but something that it is doing seems to guarantee a lockup.

Before the last trial I removed the Broadcom network card.

---

### Post by ubusr on 2010-07-05
I don't have an answer for this specific issue.  However, I found a work around for screen freezes on my older Dell that used the built-in Intel graphics chip (82845G/GL), which some on this thread seem to also have:

[http://ubuntuforums.org/showthread.php?t=1524166](http://ubuntuforums.org/showthread.php?t=1524166)

---

### Post by db8200 on 2010-08-04
Hello ubusr,

for me the problem is still unresolved.

But our problem seems not to be related to an Intel graphics chip. I  think it is related to the Nvidia Geforce 2 Go or its driver.
In the thread related to the Intel problem, they were able to connect to  their computer through SSH. In my case, when the computer freezes, no  network access is possible. The only visible thing that keeps working is  the fan. The hard disk is idle.

I don't have time to try an old Linux distribution I was using with this  computer (something like Mandriva 9), but it would be interesting,  because the computer did never freeze as it does now. (but installing  the Nvidia driver was not very easy)

I hope that some solution will appear some day...

db

---

### Post by jruschme on 2011-05-20
I recently inherited an i8200 (1.8ghz, 512mb RAM) and installed 10.04. Same problem.

I'm guessing that noone has found a solution yet. Correct?

While Googling this problem, I noticed this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/21814](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/21814)

Could this be relevant?

John

---

### Post by db8200 on 2011-05-20
Hello,

I didn't find any solution.
The bug report you mention is certainly irrelevant, because I never see my computer "unfreeze". You can wait indefinitely, the screen image will never change, and any action will have no reaction.

Please don't forget to post here if you find a solution, or if you find an old kernel that doesn't produce this bug.

Despite this bug, and although this computer is heavy and becomes hot after a few hours, I still like it (It was my first laptop). It has a solid aspect you don't find often in recent laptops (plastic toys).

db

---

### Post by AlphaLexman on 2011-05-20
Try installing a Dell Laptop Utility:
```
sudo apt-get install i8kutils
```
It can override the built-in fan controls, to keep your machine from overheating.

---

### Post by db8200 on 2011-05-20
Hello AlphaLexman,

i8kutils is installed, but it will not change anything to the fact that this machine is running a processor and a graphic chip that dissipate a lot of heat. The double fan is not very silent.

My most recent computer is an EeePC, and it makes a huge difference in weight and energy consumption.

db

---

### Post by jruschme on 2011-05-20
> **db8200 said:**
> Hello,

I didn't find any solution.
The bug report you mention is certainly irrelevant, because I never see my computer "unfreeze". You can wait indefinitely, the screen image will never change, and any action will have no reaction.

Please don't forget to post here if you find a solution, or if you find an old kernel that doesn't produce this bug.
db

The bug report references another one which was a problem with powernowd (no longer used in Ubuntu, I think). In the second bug report, it was noted that the hang seemed to occur when switching from the fastest CPU speed to a lower one. 

An interesting test (which I'm trying on mine right now) would be to change the cpufreq to "performance" (fastest speed) and try running for a while. So far, I've had no hangs.

John

---

### Post by cccc on 2011-07-18
Pls try this solution:

[http://ubuntuforums.org/showthread.php?t=1739646#7](http://ubuntuforums.org/showthread.php?t=1739646#7)

---

