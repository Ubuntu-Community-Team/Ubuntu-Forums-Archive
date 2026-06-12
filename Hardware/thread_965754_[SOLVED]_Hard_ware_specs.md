---
title: "[SOLVED] Hard ware specs?"
date: 2008-10-31
forum: Hardware
---

### Post by Yezinki on 2008-10-31
Hi there,

How can I find the hard ware specs   of my Sony machine's web cam & TV Tuner Board?

Hoping to hear from you,

Regards!

Yezinki.

---

### Post by ardvark71 on 2008-10-31
> **Yezinki said:**
> Hi there,

How can I find the hard ware specs   of my Sony machine's web cam & TV Tuner Board?

Hoping to hear from you,

Regards!

Yezinki.

Hi...

One way is to open a terminal and type in...

```
lspci
```

This will usually tell you the brand and model name and number.

Hope this helps. :)

Best Regards..

---

### Post by Yezinki on 2008-11-01
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT
 Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GM
L Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Aud
io Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (r
ev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (r
ev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (r
ev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controll
er #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controll
er #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controll
er #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controll                                                                                                                                                          er #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Control                                                                                                                                                          ler (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (re                                                                                                                                                          v 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (re                                                                                                                                                          v 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Con                                                                                                                                                          troller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Et                                                                                                                                                          hernet Controller (rev 10)
06:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev                                                                                                                                                           01)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394                                                                                                                                                           Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader                                                                                                                                                           (SD/MMC/MS/MS PRO/xD)
**_08:05.0 Multimedia controller: Fujitsu Limited. Unknown device 202a_**

---

### Post by Yezinki on 2008-11-01
Is Fujitsu the manufacturer of the TV Tuner board or the webcam?

Regards,

Yezinki.

---

### Post by ardvark71 on 2008-11-01
> **Yezinki said:**
> Is Fujitsu the manufacturer of the TV Tuner board or the webcam?

Hi...

It could be either. Unfortunately, it appears Ubuntu doesn't have a driver for it, whichever it is. :(

What is the model name and number of your system?

Best Regards...

---

### Post by Yezinki on 2008-11-01
Sony Vaio VGC-LS1.

---

### Post by Yellow Pasque on 2008-11-01
To get more info on that entry:
```
sudo update-pciids
sudo lshw -C multimedia
```

---

### Post by Yezinki on 2008-11-01
--22:43:15--  [http://pciids.sourceforge.net/v2.2/pci.ids.bz2](http://pciids.sourceforge.net/v2.2/pci.ids.bz2)
           => `/usr/share/misc/pci.ids.gz.new'
Resolving pciids.sourceforge.net... 216.34.181.96
Connecting to pciids.sourceforge.net|216.34.181.96|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 145,753 (142K) [application/x-bzip2]

100%[====================================>] 145,753        9.51K/s    ETA 00:00

22:43:34 (8.17 KB/s) - `/usr/share/misc/pci.ids.gz.new' saved [145753/145753]

Done.
~$ sudo lshw -C multimedia
  *-multimedia
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  *-multimedia UNCLAIMED
       description: Multimedia controller
       product: Fujitsu Limited.
       vendor: Fujitsu Limited.
       physical id: 5
       bus info: pci@0000:08:05.0
       version: 00
       width: 32 bits
       clock: 33MHz

---

### Post by ardvark71 on 2008-11-01
Hi...

I'm not able to get the chipset specs for your model, even from Sony's website...

[http://esupport.sony.com/US/perl/model-documents.pl?mdl=VGCLS1](http://esupport.sony.com/US/perl/model-documents.pl?mdl=VGCLS1)

You might want to give Sony a call and see if they will give you the chipset model and number for both of these devices and use Google to see if their are any known workarounds.

You might have to dual boot, if you aren't already, to get these features (in Windows.)

Best Regards...

---

### Post by Yezinki on 2008-11-01
Hi there,

Thanks.

Chipset is Intel 945 GM mobile express series.

Regards!

Yezinki.

---

### Post by Yellow Pasque on 2008-11-01
It appears your TV tuner is Fujitsu, but no driver is currently loaded for it.
Your webcam is probably a USB device that will show with 
```
lsusb
```

---

### Post by Yezinki on 2008-11-01
Thanks but its not a usb but an integrated cam.

---

### Post by Yellow Pasque on 2008-11-01
EDIT: Sorry, double post

---

### Post by Yezinki on 2008-11-01
[B]~$ lsusb
Bus 005 Device 003: ID 0ac8:c002 Z-Star Microelectronics Corp.
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 054c:024b Sony Corp.
Bus 003 Device 001: ID 0000:0000
[/B]

---

### Post by Yezinki on 2008-11-01
I read on Z stars website that they manufactured cams for Sony computers.

Regards,

Yezinki.

---

### Post by Yellow Pasque on 2008-11-01
It looks like your camera isn't supported, but if you make a request to the UVC developer mailing list, it may be easy for them to add: [http://linux-uvc.berlios.de/#devices](http://linux-uvc.berlios.de/#devices)

I'm unsure where to point you for the tv tuner.

---

### Post by Yezinki on 2008-11-01
Thanks again,

1. I really appreciate your help/assistance in finding at least the hard ware specs of TV Tuner board & the webcam?

2. Does the link charge for making a device driver?

3. I am ready to pay & I need a driver for my cam, TV Board, & SD/MMC, Memory Stick Pro drives for Linux.

4. What would be the best thing to do.......OEMS are of no help....they think Linux is for stupid  people who have nothing better to do  lol??

Hoping to hear ,

Regards,

Yezinki.

---

### Post by ardvark71 on 2008-11-01
> **Yezinki said:**
> Thanks again,

1. I really appreciate your help/assistance in finding at least the hard ware specs of TV Tuner board & the webcam?

2. Does the link charge for making a device driver?

3. I am ready to pay & I need a driver for my cam, TV Board, & SD/MMC, Memory Stick Pro drives for Linux.

4. What would be the best thing to do.......OEMS are of no help....they think Linux is for stupid  people who have nothing better to do  lol??

Hi...

You can contact them to see if they would make and include drivers for your devices but in case they aren't able to right away, a dual boot or WUBI setup, if you don't already have one and/or if you want to continue using Ubuntu, is probably your best option.

Best Regards...

---

### Post by Yezinki on 2008-11-01
Thanks alot for your assistance.

1. I shall start new threads for Linux compatible usb TV Tuner Boards, Web cams, SD/MMC drive & Dual booting.

2. Can I install Ubuntu & add various useful Linux applications to it e.g Remastersys back up, Kopete, KDE 3.5.

The only thing that I don't like about Ubuntu is lay out, top task bar, desktop background ........

3. I have Vista running on my Dell XPS 1710 & want a single Linux distro that full fill my requirements on this Sony vaio VGC-LS1.

Any how thanks again,

Regards,

Yezinki.

---

### Post by ardvark71 on 2008-11-02
> **Yezinki said:**
> Thanks alot for your assistance.

1. I shall start new threads for Linux compatible usb TV Tuner Boards, Web cams, SD/MMC drive & Dual booting.

2. Can I install Ubuntu & add various useful Linux applications to it e.g Remastersys back up, Kopete, KDE 3.5.

The only thing that I don't like about Ubuntu is lay out, top task bar, desktop background ........

3. I have Vista running on my Dell XPS 1710 & want a single Linux distro that full fill my requirements on this Sony vaio VGC-LS1.

Hi...

1. This should yield a fair amount of information for you. :) What is also important here is not just the brand and model of the device but the chipset as well. I've read instances of folks having the same brand and model of device but having a different brand and model of chipset with the end result of having very different experiences with the device under Linux. Please be sure to look out for this. ;)

2. Sure. :) You can install KDE applications in either Synaptic or Adept (KDE), however, you should install Kubuntu by opening up a terminal and typing this code...

```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```

There is also a help tutorial on doing this here...

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

Hope this helps. :)

Best Regards...

---

### Post by Yezinki on 2008-11-02
> **ardvark71 said:**
> Hi...

1. This should yield a fair amount of information for you. :) What is also important here is not just the brand and model of the device but the chipset as well. I've read instances of folks having the same brand and model of device but having a different brand and model of chipset with the end result of having very different experiences with the device under Linux. Please be sure to look out for this. ;)

2. Sure. :) You can install KDE applications in either Synaptic or Adept (KDE), however, you should install Kubuntu by opening up a terminal and typing this code...

```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```

There is also a help tutorial on doing this here...

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

Hope this helps. :)

Best Regards...


Hello there,

1. I really appreciate your assistance & the prompt reply.

2. I agree that I got a lot of info about the built in Fujitsu  TV Tuner chip & the Z star Micro electronics the manufacturer of the web cam.

3. If you mean the board chipset its Intel 945 GM mobile express, but don't know the specs of the TV Tuners chipset & cam's chipset.

4. Though have emailed both asking for Linux support drivers........lets see what is there response.

5. Thanks for sending the command & the  link.

6. Now my real question is for which I am thinking of starting another thread is as a newbie in Linux after 15 years with windows, what should be my strategy.

   a. Use Vista on my Dell XPS for professional usage.

   b. Chose between Ubuntu hardy or 8.10 for my Sony desktop??

     Or Dual boot either of the Ubuntu & XP MCE 2005 which came with this Sony machine.......the reason for having XP  MCE on this Sony is that I don't have drivers for the TV Tuner chip, web cam, MMC/SD & Memory stick Pro drives.

    Other than that I have no utility of another window on this Sony desktop.


7. What are your views firstly between Ubuntu 8.4.3 & 8.10 which should I choose to install, secondly should I dual boot that Ubuntu with XP MCE or not??

8. Personally frankly I prefer I OS on a machine, multiple OSs later coz issues for a computer illiterate like me & a newbie to the world of Linux......just my thoughts.

9. So what would you have done in my place regarding this Sony Vaio machine?

10. Could I change the TV Tuner chip to a one that has Linux support?

Hoping to hear your views,

Regards,

Yezinki.

---

### Post by ardvark71 on 2008-11-02
Hi...

You're welcome, always glad to help! :)

I really don't have an opinion of either 8.04 or 8.10 as I have only used the former for a little bit of time during the three weeks I had it installed on a VM, the latter I've not even seen. ;) I prefer how the xorg was set up in previous versions from what I have heard and seen from 8.04.

I have much more experience with 5.10 and 6.06. ;)

In terms of a strategy and what I would have done if I had your system? If I were to build a Linux system for myself that would be compatible in every way or as much as possible with Linux (and If I had the extra money to spend,) I would first compose a list of everything I wanted included in this system, in terms of processing power, motherboard capabilities and chipsets, graphics, sound, card readers, networking and wireless capabilities, etc., and then I would go about researching the best possible linux compatible devices (either natively in the OS or easy to obtain, up to date drivers) that were available as a standalone item available at a retail outlet, either online or at a store and I would purchase these components and either build the system myself from scratch or have someone who is qualified and skilled to do it for you. :)

As far as graphics go, Nvidia, as a whole, seems to be the best choice in Linux support.

Or, if you would rather not take this particular approach and want a system that's pre-built and ready to go, you can purchase a system that is Linux compatible (and comes configured with Ubuntu) from firms such as this one...

[http://system76.com/](http://system76.com/)

If the your TV tuning device is integrated (onboard) with the motherboard, then I'm afraid no. However, if this system has expansion slots and if it's possible to turn off the feature in the CMOS, then you might be able to find a PCI tuner card that would work. You would need to research this, however.

and...

"8. Personally frankly I prefer I OS on a machine, multiple OSs later coz issues for a computer illiterate like me & a newbie to the world of Linux......just my thoughts."

That's fine. :) But I'm not sure if you will enjoy the fuctionality you desire on your system you are trying to get working with Ubuntu because of the lack of drivers. :(

Best Regards...

---

### Post by Yezinki on 2008-11-02
Thanks again,

I have used Ubuntu hardy on am using Gutsy at the moment.

1. They all pick its wireless lan, wired lan dsl.

2. Infra red KB & mouse.

3. No Graphic card.......uses 128 MB of the 2 GB RAM......Intel Graphic accelerator.

4. Only issue is TV Tuner ,Web cam, SD/MMC & Memory Stick Pro drives which I hardly use......even If I have to........ use the Dell machine's 4 in 1 card reader.

All linux distros run well with no issues other than stated above.

Regards,

Yezinki.

---

### Post by ardvark71 on 2008-11-02
Hi...

In case you missed it (as I included it after I posted,) there is also this option...

[http://system76.com/](http://system76.com/)

:)

Best Regards...

---

### Post by Yezinki on 2008-11-02
Thanks again I did miss it.

My laptop is this: [http://system76.com/product_info.php?cPath=28&products_id=87](http://system76.com/product_info.php?cPath=28&products_id=87)

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-05
Is your TV card a [*_[COLOR="Blue"]Fujitsu Siemens[/COLOR]_*]("http://www.linuxtv.org/wiki/index.php/Fujitsu_Siemens")?

[[COLOR="Blue"]*_**Fujitsu Siemens Activy DVB-S Budget**_*[/COLOR]]("http://www.linuxtv.org/wiki/index.php/Fujitsu_Siemens_Activy_DVB-S_Budget")

[[COLOR="Blue"]***Fujitsu_Siemens_DVB-S_Rev_1.3***[/COLOR]]("http://www.linuxtv.org/wiki/index.php/Fujitsu_Siemens_DVB-S_Rev_1.3")

If it is then it might be supported with the DVB drivers from linuxtv.org

---

### Post by Yezinki on 2008-11-05
**Hello GENIUS LINUX KING!!**

How have you been doing?

Yes its Fujitsu......don't know exactly about being Fujitsu Siemens....any command to know exactly whether its Fujitsu Siemens?

Cam is working great.

Is it possible to cam exchange btw Linux/Ubuntu & windows using Koepte or any software??

Regards,

Yezini.

---

### Post by Yezinki on 2008-11-05
[B]Thank you for communicating with us.


We only have limited notebook that support Linux and we are considering to expand support for open source operating system in the near future. Since the TV Tuner is built into the Sony notebook you can try contacting Sony for further information and assistance for Linux. If you can give us the exact chip name and model of the built in TV Tuner we will be glad to look for a linux driver for that.

You can call us at 1-800-8fujitsu for further assistance. You can use this Service Request Number 190035 as your reference.


Thank you for choosing Fujitsu Computer Systems.


Kind regards,
Ferdz
FCS Mobile 1 Support
Fujitsu Computer Corp.[/B]

---

### Post by Yezinki on 2008-11-05
Looks like this more once one I got it opened......

[http://www.linuxtv.org/wiki/index.php/Fujitsu_Siemens_Activy_DVB-S_Budget](http://www.linuxtv.org/wiki/index.php/Fujitsu_Siemens_Activy_DVB-S_Budget)

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-05
KING its not a Hauppauge DVB-S Rev. 1.3 Card that am sure about.

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-05
> **Yezinki said:**
> **Hello GENIUS LINUX KING!!**

How have you been doing?

Yes its Fujitsu......don't know exactly about being Fujitsu Siemens....any command to know exactly whether its Fujitsu Siemens?

Cam is working great.

Is it possible to cam exchange btw Linux/Ubuntu & windows using Koepte or any software??

Regards,

Yezini.

I have been doing well thanks Yezini.

According to the wiki you only have the following command options to try out.  Its possible that you might not get much more information than you already have.  Can you post the output from these commands?  

```
lspci -v
```
and/or 
```
lspci -vnn
```

---

### Post by Yezinki on 2008-11-05
Output of the 1st command:


ubuntu@ubuntu-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dc300000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at dc380000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at dc3c0000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d8000000-d9ffffff
	Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d6000000-d7ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: da000000-dbffffff
	Prefetchable memory behind bridge: 00000000d4000000-00000000d5ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at dc5c4000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=0c, sec-latency=32
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: dc000000-dc2fffff
	Prefetchable memory behind bridge: 0000000088000000-000000008bffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 18d0 [size=8]
	I/O ports at 18c4 [size=4]
	I/O ports at 18c8 [size=8]
	I/O ports at 18c0 [size=4]
	I/O ports at 18b0 [size=16]
	Memory at dc5c4400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Subsystem: Sony Corporation Device 8205
	Flags: medium devsel, IRQ 10
	I/O ports at 18e0 [size=32]
	Kernel modules: i2c-i801

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, fast devsel, latency 0, IRQ 220
	Memory at d8000000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 2000 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device 0315
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at da000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb, wl

08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at dc216000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=08, secondary=09, subordinate=0c, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 8c000000-8ffff000
	I/O window 0: 00005400-000054ff
	I/O window 1: 00005800-000058ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at dc215000 (32-bit, non-prefetchable) [size=2K]
	Memory at dc210000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at dc214000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

08:05.0 Multimedia controller: Fujitsu Limited. Device 202a
	Subsystem: Sony Corporation Device 81fa
	Flags: medium devsel, IRQ 11
	I/O ports at 5000 [disabled] [size=256]
	Memory at dc000000 (32-bit, non-prefetchable) [disabled] [size=2M]
	Memory at dc200000 (32-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>

ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$

---

### Post by Yezinki on 2008-11-05
**Out put of the 2nd:**


ubuntu@ubuntu-laptop:~$ lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dc300000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at dc380000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at dc3c0000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d8000000-d9ffffff
	Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d6000000-d7ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: da000000-dbffffff
	Prefetchable memory behind bridge: 00000000d4000000-00000000d5ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02) (prog-if 20)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at dc5c4000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=0c, sec-latency=32
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: dc000000-dc2fffff
	Prefetchable memory behind bridge: 0000000088000000-000000008bffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 18d0 [size=8]
	I/O ports at 18c4 [size=4]
	I/O ports at 18c8 [size=8]
	I/O ports at 18c0 [size=4]
	I/O ports at 18b0 [size=16]
	Memory at dc5c4400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: medium devsel, IRQ 10
	I/O ports at 18e0 [size=32]
	Kernel modules: i2c-i801

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (rev 10)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, fast devsel, latency 0, IRQ 220
	Memory at d8000000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 2000 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device [1468:0315]
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at da000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb, wl

08:03.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at dc216000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=08, secondary=09, subordinate=0c, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 8c000000-8ffff000
	I/O window 0: 00005400-000054ff
	I/O window 1: 00005800-000058ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

08:03.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a] (prog-if 10)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at dc215000 (32-bit, non-prefetchable) [size=2K]
	Memory at dc210000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

08:03.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at dc214000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

08:05.0 Multimedia controller [0480]: Fujitsu Limited. Device [10cf:202a]
	Subsystem: Sony Corporation Device [104d:81fa]
	Flags: medium devsel, IRQ 11
	I/O ports at 5000 [disabled] [size=256]
	Memory at dc000000 (32-bit, non-prefetchable) [disabled] [size=2M]
	Memory at dc200000 (32-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>

ubuntu@ubuntu-laptop:~$

---

### Post by linux23dragon on 2008-11-05
Thanks

I'll write up a procedure and test to see how it installs before I post the information.

Hopefully it will work out for you, fingers crossed.

---

### Post by Yezinki on 2008-11-05
Thanks a million **KING of LINUX,**

I really do appreciate your devotion & dedication.

1. Could change the TV Tuner card to another one with Linux support & having ALL versions instead of just NTSC?

2. Can you goggle up a driver for the MMC/SD, Memory stick Pro drives i.e 4 in 1 card reader?

3. Is it possible to excahnge cam btw Ubuntu / Linux & windows?

Take good care,

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-05
While I do this (and it might take me a while), can you install the linux-backports-modules and then reboot.  

```
apt-get install linux-backports-modules-2.6.27-7-generic
```

Please test everything and then report back if all is ok.

EDIT.  

And repost the output from this same command.
```
lspci -vnn
```

---

### Post by Yezinki on 2008-11-05
Sure KING!!

---

### Post by Yezinki on 2008-11-05
Output **KING:**

ubuntu@ubuntu-laptop:~$ sudo apt-get install linux-backports-modules-2.6.27-7-generic
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-backports-modules-2.6.27-7-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1170kB of archives.
After this operation, 3740kB of additional disk space will be used.
Get:1 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main linux-backports-modules-2.6.27-7-generic 2.6.27-7.4 [1170kB]
Fetched 1170kB in 26s (44.7kB/s)                                               
Selecting previously deselected package linux-backports-modules-2.6.27-7-generic.
(Reading database ... 104608 files and directories currently installed.)
Unpacking linux-backports-modules-2.6.27-7-generic (from .../linux-backports-modules-2.6.27-7-generic_2.6.27-7.4_i386.deb) ...
Setting up linux-backports-modules-2.6.27-7-generic (2.6.27-7.4) ...
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic

ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$

---

### Post by linux23dragon on 2008-11-05
> **Yezinki said:**
> Output **KING:**

ubuntu@ubuntu-laptop:~$ sudo apt-get install linux-backports-modules-2.6.27-7-generic
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-backports-modules-2.6.27-7-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1170kB of archives.
After this operation, 3740kB of additional disk space will be used.
Get:1 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) intrepid/main linux-backports-modules-2.6.27-7-generic 2.6.27-7.4 [1170kB]
Fetched 1170kB in 26s (44.7kB/s)                                               
Selecting previously deselected package linux-backports-modules-2.6.27-7-generic.
(Reading database ... 104608 files and directories currently installed.)
Unpacking linux-backports-modules-2.6.27-7-generic (from .../linux-backports-modules-2.6.27-7-generic_2.6.27-7.4_i386.deb) ...
Setting up linux-backports-modules-2.6.27-7-generic (2.6.27-7.4) ...
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic

ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$

Please reboot and then post the output of this command.

```
lspci -vnn
```

I've almost finished writing up the driver procedure

---

### Post by Yezinki on 2008-11-05
Here **KING!!**

ubuntu@ubuntu-laptop:~$ lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dc300000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at dc380000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at dc3c0000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d8000000-d9ffffff
	Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d6000000-d7ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: da000000-dbffffff
	Prefetchable memory behind bridge: 00000000d4000000-00000000d5ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02) (prog-if 20)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at dc5c4000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=0c, sec-latency=32
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: dc000000-dc2fffff
	Prefetchable memory behind bridge: 0000000088000000-000000008bffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 18d0 [size=8]
	I/O ports at 18c4 [size=4]
	I/O ports at 18c8 [size=8]
	I/O ports at 18c0 [size=4]
	I/O ports at 18b0 [size=16]
	Memory at dc5c4400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: medium devsel, IRQ 10
	I/O ports at 18e0 [size=32]
	Kernel modules: i2c-i801

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (rev 10)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, fast devsel, latency 0, IRQ 220
	Memory at d8000000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 2000 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device [1468:0315]
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at da000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb, wl

08:03.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at dc216000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=08, secondary=09, subordinate=0c, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 8c000000-8ffff000
	I/O window 0: 00005400-000054ff
	I/O window 1: 00005800-000058ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

08:03.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a] (prog-if 10)
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at dc215000 (32-bit, non-prefetchable) [size=2K]
	Memory at dc210000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

08:03.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
	Subsystem: Sony Corporation Device [104d:8205]
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at dc214000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

08:05.0 Multimedia controller [0480]: Fujitsu Limited. Device [10cf:202a]
	Subsystem: Sony Corporation Device [104d:81fa]
	Flags: medium devsel, IRQ 11
	I/O ports at 5000 [disabled] [size=256]
	Memory at dc000000 (32-bit, non-prefetchable) [disabled] [size=2M]
	Memory at dc200000 (32-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>

ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$

---

### Post by linux23dragon on 2008-11-05
OK I've done it and possibly fixed the MMC/SD issues as well.

First lets fix the MMC/SD.  You already have a working driver for MMC/SD, but you need to do two more things.


This command will create a MMCSD directory in /media (ie:- /media/MMCSD) and open up your *fstab* file (for editing) using gedit.
  
```
sudo mkdir /media/MMCSD &&
sudo gedit /etc/fstab
```

Once you see the fstab file (in gedit), you need to add the following two lines at the bottom.

Just copy and paste
```
# Auto mount the SD/MMC/MS/MS PRO/xD 
/dev/sdb1     /media/MMCSD     auto     user,auto,exec,rw     0     0
```

Save and exit gedit.  Then re insert the memory card.


Now for your TV card.  If installing the kernel back ports modules did not work.

You might need firmware from the TV card to be loaded to the drivers to work correctly.  Use the following command to see if their are any error messages, and post them here. 

```
dmesg | grep dvb
```


This is the new driver installation from upstream, but still might be subjected to the firmware issues as well.  The firmware issues can be fixed so it is important to use that demesage command so I can see the output before continuing.


Even so, this is how you can install or upgrade the driver:-


Copy and paste the following code into the terminal

```
sudo apt-get install mercurial linux-headers-$(uname -r) build-essential &&
hg clone http://linuxtv.org/hg/v4l-dvb &&
cd v4l-dvb &&
hg update &&
make &&
sudo make install
```

Then reboot.


EDIT:  Of course all of this assumes that the driver supports your TV card

---

### Post by Yezinki on 2008-11-05
[B]ubuntu@ubuntu-laptop:~$ dmesg | grep dvb
ubuntu@ubuntu-laptop:~$ dmesg | grep dvb
ubuntu@ubuntu-laptop:~$ [/B]

The above gave no out put KING!

The 1st one gave & saved in gedit.

**Last one:**

ubuntu@ubuntu-laptop:~$ sudo apt-get install mercurial linux-headers-$(uname -r) build-essential &&
> hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) &&
> cd v4l-dvb &&
> hg update &&
> make &&
> sudo make install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mercurial is already the newest version.
linux-headers-2.6.27-7-generic is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
destination directory: v4l-dvb
requesting all changes
adding changesets

---

### Post by Yezinki on 2008-11-05
[B]dmesg | grep dvb

ubuntu@ubuntu-laptop:~$ dmesg | grep dvb
ubuntu@ubuntu-laptop:~$ 
bash:         : command not found
ubuntu@ubuntu-laptop:~$ 

[/B]

Here **KING LINUX!!**

---

### Post by linux23dragon on 2008-11-05
> **Yezinki said:**
> [B]ubuntu@ubuntu-laptop:~$ dmesg | grep dvb
ubuntu@ubuntu-laptop:~$ dmesg | grep dvb
ubuntu@ubuntu-laptop:~$ [/B]

The above gave no out put KING!

The 1st one gave & saved in gedit.

**Last one:**

ubuntu@ubuntu-laptop:~$ sudo apt-get install mercurial linux-headers-$(uname -r) build-essential &&
> hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) &&
> cd v4l-dvb &&
> hg update &&
> make &&
> sudo make install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mercurial is already the newest version.
linux-headers-2.6.27-7-generic is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
destination directory: v4l-dvb
requesting all changes
adding changesets

That dose not look complete it still might be downloading,  give it time :)

---

### Post by Yezinki on 2008-11-05
Back from reboot **KING!!**

---

### Post by Yezinki on 2008-11-05
[B]sudo apt-get install mercurial linux-headers-$(uname -r) build-essential &&
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) &&
cd v4l-dvb &&
hg update &&
make &&
sudo make install[/B]



This out put looks incomplete since I missed to copy the first one.

I typed the command again & that's why the output looks like this.

**FYI KING:**

---

### Post by linux23dragon on 2008-11-05
> **Yezinki said:**
> Back from reboot **KING!!**

So the sd/mmc card works ok?
The webcam still functions?

Did the new driver compile and install?

Any luck with the firmware loading (dmesg | grep dvb) ?

---

### Post by Yezinki on 2008-11-05
**Yes KING LINUX.......**

1. SD/MMC function so does the CAM........GREAT!!

2. No luck with the command
[B]
ubuntu@ubuntu-laptop:~$ dmesg | grep dvb
ubuntu@ubuntu-laptop:~$ 
bash:     : command not found
ubuntu@ubuntu-laptop:~$ 
[/B]

3. Shall I have to keep updating the kernels??

Take care** GENIUS!**

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-05
I mean kernels for the web cam & SD/MMC etc?

Regards!
[B]
KING LINUX.

I appreciate your dedication, temperament to bear with me,
[/B]
Shall keep bugging you at times,

Yezinki.

---

### Post by linux23dragon on 2008-11-05
> **Yezinki said:**
> I mean kernels for the web cam & SD/MMC etc?

Regards!
[B]
KING LINUX.

I appreciate your dedication, temperament to bear with me,
[/B]
Shall keep bugging you at times,

Yezinki.

You only need to worry about the webcam driver if you get a kernel update.

In regards to your TV capture card? It is starting to become a guessing game.  I really need to know the chip details, so far I suspect that you need the firmware for your TV card.

Can you copy and then attach your kernel.log?

The following code will copy the kern.log to your home directory.

```
cp /var/log/kern.log ~ 
```

Is there any reference of the card specs in your user book or documentations?
EDIT Is it also possible to attach a photo of the chip set and or TV tuner as well (even close up shots)?

---

### Post by Yezinki on 2008-11-05
> **linux23dragon said:**
> You only need to worry about the webcam driver if you get a kernel update.

In regards to your TV capture card? It is starting to become a guessing game.  I really need to know the chip details, so far I suspect that you need the firmware for your TV card.

Can you copy and then attach your kernel.log?

The following code will copy the kern.log to your home directory.

```
cp /var/log/kern.log ~ 
```

Is there any reference of the card specs in your user book or documentations?
EDIT Is it also possible to attach a photo of the chip set and or TV tuner as well (even close up shots)?

**Hi KING of Linux!**

1. Copy where Terminal...........how to attach to kernel log?

2. I'll ask the pc tech to come open the desktop cause its got 40 plus small screws & take pics & details of the TV Tuner card & post them.

3. How will I know that I gotta kernel update ......if the cam stops working??

4. Can you suggest any PCI with Linux support, All Systems, TV Tuner board to replace this?

5. Last question can one cam exchange btw Linux & windows if yes how?

Regards,

Yezinki.

PS: Sony support gives no info about the TV Tuner board........just NTSC.

---

### Post by Yezinki on 2008-11-05
> **linux23dragon said:**
> OK I've done it and possibly fixed the MMC/SD issues as well.

First lets fix the MMC/SD.  You already have a working driver for MMC/SD, but you need to do two more things.


This command will create a MMCSD directory in /media (ie:- /media/MMCSD) and open up your *fstab* file (for editing) using gedit.
  
```
sudo mkdir /media/MMCSD &&
sudo gedit /etc/fstab
```

Once you see the fstab file (in gedit), you need to add the following two lines at the bottom.

Just copy and paste
```
# Auto mount the SD/MMC/MS/MS PRO/xD 
/dev/sdb1     /media/MMCSD     auto     user,auto,exec,rw     0     0
```

**Save and exit gedit.  Then re insert the memory card.**


Now for your TV card.  If installing the kernel back ports modules did not work.

You might need firmware from the TV card to be loaded to the drivers to work correctly.  Use the following command to see if their are any error messages, and post them here. 

```
dmesg | grep dvb
```


This is the new driver installation from upstream, but still might be subjected to the firmware issues as well.  The firmware issues can be fixed so it is important to use that demesage command so I can see the output before continuing.


Even so, this is how you can install or upgrade the driver:-


Copy and paste the following code into the terminal

```
sudo apt-get install mercurial linux-headers-$(uname -r) build-essential &&
hg clone http://linuxtv.org/hg/v4l-dvb &&
cd v4l-dvb &&
hg update &&
make &&
sudo make install
```

Then reboot.


EDIT:  Of course all of this assumes that the driver supports your TV card


**While running the command for SD/MMC.......card be inserted first than taken out  after the out put is saved & than reinserted??**

Regards!

Yezinki.

---

### Post by linux23dragon on 2008-11-05
> **Yezinki said:**
> **Hi KING of Linux!**

1. Copy where Terminal...........how to attach to kernel log?



Look for the paper clip when you create a new message.  The log file is located in your user folder (After you used the copy (cp /var/log/kern.log ~) command).


> **Yezink]
2. I'll ask the pc tech to come open the desktop cause its got 40 plus small screws & take pics & details of the TV Tuner card & post them.
[/quote]

Unless the tech can give you the details over the phone.  Even better, ask for an email response with attached photos and TV tuner specs/details. 

[QUOTE=Yezink]
3. How will I know that I gotta kernel update ......if the cam stops working??
[/quote]

The Update Manager will detail what packages will be updated.  So a kernel upgrade will be listed before it is installed.  Of course if the webcam stops working after an upgrade, then you can reinstall the driver. 

[QUOTE=Yezink]
4. Can you suggest any PCI with Linux support, All Systems, TV Tuner board to replace this?
[/quote]

I recommend looking at the [*_[COLOR="Blue"]Supported_Hardware[/COLOR]_*]("http://www.linuxtv.org/wiki/index.php/Supported_Hardware") at the linuxTV site.  Just look for the PCI cards for now.  I also recommend searching for **Linux ATSC PCI TV Tuner** reviews as well.  


[QUOTE=Yezink]
5. Last question can one cam exchange btw Linux & windows if yes how?
[/quote]

Yes.  The software will handle streaming video and audio automaticly  said:**
> 
PS: Sony support gives no info about the TV Tuner board........just NTSC.

lol, yep.  Very helpful.  See if you can get them to email the all the chip set details to you, even if it means that they are to read all of the writing on the IC (main controller) itself.  That will really help.

---

### Post by linux23dragon on 2008-11-05
> **Yezinki said:**
> **While running the command for SD/MMC.......card be inserted first than taken out  after the out put is saved & than reinserted??**

Regards!

Yezinki.

No, I was assuming that the card might be already inserted into the PC.

The card can be in or out of the PC.  It does not matter.  It will work just the same.

---

### Post by Yezinki on 2008-11-05
[B]ubuntu@ubuntu-laptop:~$ cp /var/log/kern.log ~
ubuntu@ubuntu-laptop:~$ 
bash:         : command not found
ubuntu@ubuntu-laptop:~$ 
[/B]

No Output **KING LINUX!**

---

### Post by linux23dragon on 2008-11-05
> **Yezinki said:**
> [B]ubuntu@ubuntu-laptop:~$ cp /var/log/kern.log ~
ubuntu@ubuntu-laptop:~$ 
bash:         : command not found
ubuntu@ubuntu-laptop:~$ 
[/B]

No Output **KING LINUX!**

No output needed.  The file has been copied.

Try this.  It is the same command with output letting you know where the file is copied too.

```
cp -v /var/log/kern.log ~
```

---

### Post by Yezinki on 2008-11-05
This is the out put **KING **done twice as you see:

[B]ubuntu@ubuntu-laptop:~$ cp -v /var/log/kern.log ~
`/var/log/kern.log' -> `/home/ubuntu/kern.log'
ubuntu@ubuntu-laptop:~$ cp -v /var/log/kern.log ~
`/var/log/kern.log' -> `/home/ubuntu/kern.log'
ubuntu@ubuntu-laptop:~$ 
[/B]

---

### Post by linux23dragon on 2008-11-05
> **Yezinki said:**
> This is the out put **KING **done twice as you see:

[B]ubuntu@ubuntu-laptop:~$ cp -v /var/log/kern.log ~
`/var/log/kern.log' -> `/home/ubuntu/kern.log'
ubuntu@ubuntu-laptop:~$ cp -v /var/log/kern.log ~
`/var/log/kern.log' -> `/home/ubuntu/kern.log'
ubuntu@ubuntu-laptop:~$ 
[/B]

Yes the command is pasted twice.  Are you using the middle mouse button to paste the command into the terminal?

---

### Post by Yezinki on 2008-11-05
I shall get all the detailed info about the TV card/board/chip & let you know **[COLOR="DarkRed"]KING of LINUX[/COLOR]**!

What streaming software are you referring to to exchange cam btw Ubuntu & windows?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-05
No not using the scroll.....pasted it twice to recheck.

---

### Post by linux23dragon on 2008-11-05
> **Yezinki said:**
> I shall get all the detailed info about the TV card/board/chip & let you know **[COLOR="DarkRed"]KING of LINUX[/COLOR]**!

What streaming software are you referring to to exchange cam btw Ubuntu & windows?

Regards,

Yezinki.

Any application that installs on both Windows and Linux and uses the webcam like kopete, aMSN.  And I think VLC as well.

Oh yea, Skype as well

---

### Post by linux23dragon on 2008-11-05
> **Yezinki said:**
> No not using the scroll.....pasted it twice to recheck.

lol.   Ok, cool :)

---

### Post by Yezinki on 2008-11-05
KING what's aMSN & VLC??

---

### Post by linux23dragon on 2008-11-05
> **Yezinki said:**
> KING what's aMSN & VLC??

aMSN is like kopete using the msn protocol.

And Skype is another application you can use, by the way ;)

VLC is a video player, but you can also stream video across the network to another PC as well.

---

### Post by Yezinki on 2008-11-05
[B][COLOR="DarkRed"]KING of LINUX I[/COLOR] really admire your depth of knowledge which BTW envy too lol, your dedication, temperament, hard work.........no words to express.
[/B]
Wanna swap professions lol.

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-05
When I use web cam in Skype the colors are wavy.....not at all as good as Ekiga.

---

### Post by linux23dragon on 2008-11-05
> **Yezinki said:**
> [B][COLOR="DarkRed"]KING of LINUX I[/COLOR] really admire your depth of knowledge which BTW envy too lol, your dedication, temperament, hard work.........no words to express.
[/B]
Wanna swap professions lol.

Regards,

Yezinki.

I'm a Electronic Service and Test technician lol 

I just found the download for [[COLOR="Blue"]***ekiga***[/COLOR]]("http://wiki.ekiga.org/index.php/Windows_Users") for windows users.  so you can use Ekiga as well.


EDIT:  I have also just found out that you can use Ekiga to talk to [*[COLOR="Blue"]_Windows_Messenger_5.1_[/COLOR]*]("http://wiki.ekiga.org/index.php/Connecting_Windows_Messenger_5.1_to_ekiga.net").  I Learn something new every day

---

### Post by Yezinki on 2008-11-05
> **linux23dragon said:**
> I'm a Electronic Service and Test technician lol 

I just found the download for [[COLOR="Blue"]***ekiga***[/COLOR]]("http://wiki.ekiga.org/index.php/Windows_Users") for windows users.  so you can use Ekiga as well.

Not a issue**[COLOR="DarkRed"] KING.[/COLOR]**........love to swapp any ways lol.

**[COLOR="Purple"]You are the Ultimate.[/COLOR]**

Take good care,

Thanks again,

Shall keep you informed,

Regards!

Yezinki.

---

### Post by Yezinki on 2008-11-05
I have been learning something new every 5 mins since last 22 years lol...........

---

### Post by Yezinki on 2008-11-05
Hi** KING LINUX** have a look at these kernel updates should I install them??

Regards,


Yezinki.

---

### Post by linux23dragon on 2008-11-05
> **Yezinki said:**
> Hi** KING LINUX** have a look at these kernel updates should I install them??

Regards,


Yezinki.

Yes you can :)

You can install any kernel update.  If the webcam does not work afterwards, then you know what to do (just reinstall the webcam driver).

---

### Post by linux23dragon on 2008-11-05
opps,  double post

When are you going to send a copy of your kernel log (located in your user directory (/home/ubuntu))?

---

### Post by Yezinki on 2008-11-05
Thanks **[COLOR="DarkRed"]KING LINUX![/COLOR]**

1. The Cam only at the moment is functioning with Ekiga, but not with aMSN, VLC, or Skype?

2. Since I shall be getting the back panel opened, I shall post the pics, details of the TV Tuner chip/board which is a NTC PCI & the internal optical drive, both which I want to replace.

3. You shall get all their info , voltage requirements etc. like the usb optical drives requires 5.2V.

My best Regards,

Take care,

Yezinki.

---

### Post by Yezinki on 2008-11-05
**[COLOR="DarkRed"]KING[/COLOR]** how do I post the kernel log, it wont paste or attach, error too large size??

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-05
**[FONT="Arial"][SIZE="3"][COLOR="DarkRed"]KING LINUX[/COLOR][/SIZE][/FONT]** for your expert thoughts.....aMSN settings assistant.

---

### Post by Yezinki on 2008-11-05
**[SIZE="5"][COLOR="DarkRed"]KING LINUX[/COLOR][/SIZE]** where do I post that 180 pages kernel log.........kindly PM.

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-06
> **Yezinki said:**
> Thanks **[COLOR="DarkRed"]KING LINUX![/COLOR]**

1. The Cam only at the moment is functioning with Ekiga, but not with aMSN, VLC, or Skype?


Only one application can use the webcam at one time.

[QUOTE=Yezinki]
2. Since I shall be getting the back panel opened, I shall post the pics, details of the TV Tuner chip/board which is a NTC PCI & the internal optical drive, both which I want to replace.
[/quote]

ok. cool.  What's wrong with the Optical drive?


[QUOTE=Yezinki]
3. You shall get all their info , voltage requirements etc. like the usb optical drives requires 5.2V.

My best Regards,

Take care,

Yezinki.[/QUOTE]

Thanks.

---

### Post by linux23dragon on 2008-11-06
> **Yezinki said:**
> **[FONT="Arial"][SIZE="3"][COLOR="DarkRed"]KING LINUX[/COLOR][/SIZE][/FONT]** for your expert thoughts.....aMSN settings assistant.

That appears to see the attached and working webcam.  But it looks like you also have kopete running too.

---

### Post by Yezinki on 2008-11-06
> **linux23dragon said:**
> Only one application can use the webcam at one time.



ok. cool.  What's wrong with the Optical drive?




Thanks.


Hello **[FONT="Arial"][SIZE="5"][COLOR="DarkRed"]LINUX KING![/COLOR][/SIZE][/FONT]**

1. I agree that only 1 application can use the cam......but even when I quit Ekiga & start aMSN it shows a blank screen........because the Tcl/Tk drivers of aMSN need to be updated??

2. Its a 40 pin slim slot loading DVD-RAM drive.....very picky about media......I want to install a DVDRW drive in its place....at the moment I have a usb Sony DRX-S70U optical drive which is great.....but unfortunately in Set up / BIOS their is no option for a usb boot optical drive?

3. I want the TV Tuner changed to a ALL systems i.e SECAM, NTSC, PAL A/B one too.

I shall post their pics & details.

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-06
> **linux23dragon said:**
> That appears to see the attached and working webcam.  But it looks like you also have kopete running too.


I have Ekiga, Pidgin, aMSN & Skype........no Kopete.

Regards!

---

### Post by Yezinki on 2008-11-06
**[SIZE="5"][FONT="Arial"][COLOR="DarkRed"]Hey LINUX KING!![/COLOR][/FONT][/SIZE]**

Look for yourself.........MMC.........

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-06
It appears that linux dose not support this TV card. 

```
08:05.0 Multimedia controller [0480]: Fujitsu Limited. Device [10cf:202a]
Subsystem: Sony Corporation Device [104d:81fa]
Flags: medium devsel, IRQ 11
I/O ports at 5000 [disabled] [size=256]
Memory at dc000000 (32-bit, non-prefetchable) [disabled] [size=2M]
Memory at dc200000 (32-bit, non-prefetchable) [disabled] [size=64K]
Capabilities: <access denied>
```




This is the only kernel log information you have on this card.

```
Nov  5 15:47:31 ubuntu-laptop kernel: [    0.550208] PCI: 0000:08:05.0 reg 10 io port: [5000, 50ff] 
Nov  5 15:47:31 ubuntu-laptop kernel: [    0.550217] PCI: 0000:08:05.0 reg 14 32bit mmio: [dc000000, dc1fffff] 
Nov  5 15:47:31 ubuntu-laptop kernel: [    0.550226] PCI: 0000:08:05.0 reg 18 32bit mmio: [dc200000, dc20ffff]
```

So yea, it might be a good idea to look for another TV tuner.

---

### Post by linux23dragon on 2008-11-06
> **Yezinki said:**
> **[SIZE="5"][FONT="Arial"][COLOR="DarkRed"]Hey LINUX KING!![/COLOR][/FONT][/SIZE]**

Look for yourself.........MMC.........

Regards,

Yezinki.

Ok cool

I also see a Memory Card folder in Computer.  Is it the same MMCSD drive?

---

### Post by Yezinki on 2008-11-06
> **linux23dragon said:**
> It appears that linux dose not support this TV card. 

```
08:05.0 Multimedia controller [0480]: Fujitsu Limited. Device [10cf:202a]
Subsystem: Sony Corporation Device [104d:81fa]
Flags: medium devsel, IRQ 11
I/O ports at 5000 [disabled] [size=256]
Memory at dc000000 (32-bit, non-prefetchable) [disabled] [size=2M]
Memory at dc200000 (32-bit, non-prefetchable) [disabled] [size=64K]
Capabilities: <access denied>
```




This is the only kernel log information you have on this card.

```
Nov  5 15:47:31 ubuntu-laptop kernel: [    0.550208] PCI: 0000:08:05.0 reg 10 io port: [5000, 50ff] 
Nov  5 15:47:31 ubuntu-laptop kernel: [    0.550217] PCI: 0000:08:05.0 reg 14 32bit mmio: [dc000000, dc1fffff] 
Nov  5 15:47:31 ubuntu-laptop kernel: [    0.550226] PCI: 0000:08:05.0 reg 18 32bit mmio: [dc200000, dc20ffff]
```

So yea, it might be a good idea to look for another TV tuner.
[FONT="Arial"][B][SIZE="5"][COLOR="DarkRed"]
Hi KING LINUX![/COLOR][/SIZE][/B][/FONT]

1. Not a problem.........I wanted to replace my PCI TV tuner card.....I shall post its pics & details.....could you later suggest any PCI TV Tuner card, with linux support & ALL systems?

2. You seen the memory card folder, yes there is a MMC drive....if it;s that you mean......or suggest a command to double check.

3. Now why is the cam running only on Ekiga?

4. Driver Agent/ Phoenix technologies who built the BIOS for Sony &  this desktop says its out dated, since I have a subscription with them....when they asked for the details to send me a link to get the newer BIOS....got reluctant .......I don't know why??

Best Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-06
[B]Hi there,

It says my BIOS is outdated but cant find the newer one despite the scan.

Hoping to hear from you,

Regards!


Please run the BIOS AGENT PLUS scan, and then log in.

 

Then click on the BIOS download icon, and fill in the form and submit it.

 

The BIOS will be sent to you within 24 hours of doing that.
[/B]

---

### Post by linux23dragon on 2008-11-06
> **Yezinki said:**
> [FONT="Arial"][B][SIZE="5"][COLOR="DarkRed"]
Hi KING LINUX![/COLOR][/SIZE][/B][/FONT]

1. Not a problem.........I wanted to replace my PCI TV tuner card.....I shall post its pics & details.....could you later suggest any PCI TV Tuner card, with linux support & ALL systems?


You might need to ask in TV tuner forums for that information, or start another thread 


> **Yezinki]
2. You seen the memory card folder, yes there is a MMC drive....if it said:**
> 

Open both folders and see if the contents are the same.

[QUOTE=Yezinki]
3. Now why is the cam running only on Ekiga?


I do not know.  Could it be to do with the brightness settings?


[QUOTE=Yezinki]
4. Driver Agent/ Phoenix technologies who built the BIOS for Sony &  this desktop says its out dated, since I have a subscription with them....when they asked for the details to send me a link to get the newer BIOS....got reluctant .......I don't know why??

Best Regards,

Yezinki.[/QUOTE]

Try a google search for an updated version.  Use your computer name and model (and also type in  BIOS) as the search string.

---

### Post by Yezinki on 2008-11-06
For your view KING!

---

### Post by linux23dragon on 2008-11-06
> **Yezinki said:**
> [B]Hi there,

It says my BIOS is outdated but cant find the newer one despite the scan.

Hoping to hear from you,

Regards!


Please run the BIOS AGENT PLUS scan, and then log in.

 

Then click on the BIOS download icon, and fill in the form and submit it.

 

The BIOS will be sent to you within 24 hours of doing that.
[/B]

So you have waited 24 hours?

---

### Post by linux23dragon on 2008-11-06
> **Yezinki said:**
> For your view KING!

Nice.  Its good to see that it works as expected.

---

### Post by Yezinki on 2008-11-06
Same contents**[FONT="Arial"][SIZE="5"][COLOR="DarkRed"] KING LINUX![/COLOR][/SIZE][/FONT]**

---

### Post by Yezinki on 2008-11-06
Yes I waited & when they came to know its a Sony for which they made the BIOS they refused.........stupid driver agent / Phoenix technologies takes $s out of CC & give poor service.

---

### Post by linux23dragon on 2008-11-06
> **Yezinki said:**
> Same contents**[FONT="Arial"][SIZE="5"][COLOR="DarkRed"] KING LINUX![/COLOR][/SIZE][/FONT]**

Well, at lest it now auto mounts for you.

---

### Post by Yezinki on 2008-11-06
on aMSN my patient was using windows I could see him but got an error message on my cam.

**"Your web cam uses a combination of pallete / resolution that this  extension does not support yet."**

---

### Post by Yezinki on 2008-11-06
For your view!

---

### Post by Yezinki on 2008-11-06
aMSN error!

---

### Post by linux23dragon on 2008-11-06
> **Yezinki said:**
> aMSN error!

The driver for your webcam is very new, and you just might be the only one who has tested the driver operation.  So expect some functions to not yet work yet. They will be implemented in time. Perhaps it might be good to talk to the driver developer about it, so he knows the driver is working.  He can help you in regards to functionality.  

Edit: You webcam is listed on this [*_[COLOR="Blue"]**list**[/COLOR]_*]("http://moinejf.free.fr/webcam.html") 

This is written in the patches.README

*Users are welcome to use, test and report any issues via the mailing [**[I]_[COLOR="Blue"]lists[/COLOR]_***]("http://www.linuxtv.org/lists.php") or via the Kernel's bugzilla, available at:
	[http://bugzilla.kernel.org](http://bugzilla.kernel.org)[/I]

EDIT: I noticed that you also selected the low resolution check box in the web cam preferences.

Does the same thing happen with Kopete?  Kopete can use MSN as well.

---

### Post by linux23dragon on 2008-11-06
> **Yezinki said:**
> For your view!

Your swap space is really big.  I have never used any more than 512MB myself.  Have you noticed that your not even using any swap space yet?

ext3 is ok.  I use XFS myself.  XFS a faster file system in both system use and system recovery (if you have a brown out or power cut).

XFS is also (in my opinion) safer to use as it has proven to have a better file recovery rate and I have never yet seen any file corruption in the last five years, no matter what happens to my PC.

And of course it has a very large file size support as well.

But there is no reason for you to reinstall just to have XFS.  EXT3 has been getting better over time since I had last used it.  So it should serve you well.

---

### Post by Yezinki on 2008-11-06
Hi **[FONT="Arial"][SIZE="5"][COLOR="DarkRed"]KING LINUX![/COLOR][/SIZE][/FONT]**

[FONT="Arial"]Hope you are doing great.

1. Firstly as you pointed out the big swap size....that could be reduced without reinstall........I agree that 512 MB is ample since I don't use hibernation....& have 2 GB of physical ram @ 667 MHZ.

2. Though to change the file system from ext3 to XFS, I would need a reinstall, which eventually I shall do once I get familiar with Ubuntu.

3. Personally I prefer 1 OS on a machine....I'd like Ubuntu on Sony & have Vista on   my Dell XPS for my professional use.

4. Being new to Ubuntu I cannot afford to give all of my time to learning & working on Ubuntu so I still have Vista on the other. Once I do get good at Linux than eventually shall have Ubuntu on both.

5. If it were you how would you partition the 250 GB drive & the file system for a single OS i.e Ubuntu?

6. Thanks for sending the links, but I have a blind trust in your abilities, no wonder I call you the uncrowned LINUX KING.

7. aMSN not being able to use the cam apart from Ekiga.....kindly have a look at this link suggesting which to install or what binaries Tcl/Tk to upgrade??

    a. [http://www.amsn-project.net/linux-downloads.php](http://www.amsn-project.net/linux-downloads.php)

    b. [http://packages.ubuntu.com/search?keywords=search](http://packages.ubuntu.com/search?keywords=search)

    c. [http://www.amsn-project.net/forums/viewforum.php?f=2](http://www.amsn-project.net/forums/viewforum.php?f=2)

    d. [http://www.amsn-project.net/forums/viewtopic.php?t=4432](http://www.amsn-project.net/forums/viewtopic.php?t=4432)


8. In one of the posts I was going through, I checked my connectivity for the cam........& I think that is the reason that my cam doesn't function....error displayed which I am attaching too is that I am fire walled or behind a router.

9. I use zoom adsl modem X6....... [http://www.zoom.com/products/adsl_overview.html#5590](http://www.zoom.com/products/adsl_overview.html#5590) X6...is the modem's firewall or Ubuntu 8.10s?

10. How do I connect this Sony machine using wifi......it's a BCM 802.11g PCI-E Adapter?

11. Lastly my machine is reading the MMC drives & opening its files/folders but won't either give options to format the card nor would open individual files....file format issue?

Hoping to hear as always,

My best regards,

Yezinki.[/FONT]

---

### Post by linux23dragon on 2008-11-06
> **Yezinki said:**
> Hi **[FONT="Arial"][SIZE="5"][COLOR="DarkRed"]KING LINUX![/COLOR][/SIZE][/FONT]**

[FONT="Arial"]Hope you are doing great.

1. Firstly as you pointed out the big swap size....that could be reduced without reinstall........I agree that 512 MB is ample since I don't use hibernation....& have 2 GB of physical ram @ 667 MHZ.

2. Though to change the file system from ext3 to XFS, I would need a reinstall, which eventually I shall do once I get familiar with Ubuntu.

3. Personally I prefer 1 OS on a machine....I'd like Ubuntu on Sony & have Vista on   my Dell XPS for my professional use.

4. Being new to Ubuntu I cannot afford to give all of my time to learning & working on Ubuntu so I still have Vista on the other. Once I do get good at Linux than eventually shall have Ubuntu on both.

5. If it were you how would you partition the 250 GB drive & the file system for a single OS i.e Ubuntu?

6. Thanks for sending the links, but I have a blind trust in your abilities, no wonder I call you the uncrowned LINUX KING.

7. aMSN not being able to use the cam apart from Ekiga.....kindly have a look at this link suggesting which to install or what binaries Tcl/Tk to upgrade??

    a. [http://www.amsn-project.net/linux-downloads.php](http://www.amsn-project.net/linux-downloads.php)

    b. [http://packages.ubuntu.com/search?keywords=search](http://packages.ubuntu.com/search?keywords=search)

    c. [http://www.amsn-project.net/forums/viewforum.php?f=2](http://www.amsn-project.net/forums/viewforum.php?f=2)

    d. [http://www.amsn-project.net/forums/viewtopic.php?t=4432](http://www.amsn-project.net/forums/viewtopic.php?t=4432)


8. In one of the posts I was going through, I checked my connectivity for the cam........& I think that is the reason that my cam doesn't function....error displayed which I am attaching too is that I am fire walled or behind a router.

9. I use zoom adsl modem X6....... [http://www.zoom.com/products/adsl_overview.html#5590](http://www.zoom.com/products/adsl_overview.html#5590) X6...is the modem's firewall or Ubuntu 8.10s?

10. How do I connect this Sony machine using wifi......it's a BCM 802.11g PCI-E Adapter?

11. Lastly my machine is reading the MMC drives & opening its files/folders but won't either give options to format the card nor would open individual files....file format issue?

Hoping to hear as always,

My best regards,

Yezinki.[/FONT]

Hi Yezinki

I'll write up some details for you later today (after I come back from work).  

Your wifi should just work as is if a working driver is already installed.  You can tell if the wifi is working by left clicking on the network connection icon in the top right of your desktop.  You should see your Wifi access point strength bar.  

Please report if that is the case.  I'll post later on today .

---

### Post by Yezinki on 2008-11-06
**Your wifi should just work as is if a working driver is already installed. You can tell if the wifi is working by left clicking on the network connection icon in the top right of your desktop. You should see your Wifi access point strength bar.**

Hello KING LINUX!

1. I see the network connection & by left clicking I see it checked but no bars?

2. What about aMSN issues did you get a clue?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-06
KING LINUX,

Have a look at my adsl modem's web console.......Fire wall......do you think I need to make any changes as according to aMSN connectivity results?

In windows both MSN & Yahoo function with out an issue with the same configuration?

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-07
[QUOTE=Yezinki]
5. If it were you how would you partition the 250 GB drive & the file system for a single OS i.e Ubuntu?
[/quote]

This is how I partition my own hard drive on my own Desktop PC.

ext3 and XFS are file systems I use in the following partitions:-


sda1 /boot ext3 200MB
sda2 /usr  XFS  20GB
sda3 /var  XFS  5GB
sda4 ->*logical drive*<-
sda5 /     XFS  1GB <- root partition
sda6 /tmp  XFS  13GB
sda7    SWAP    512MB <- swap space
sda8 /home XFS  The Partition size?  As big as you can for /home.


******_Optional partition_******

sda9 /usr/local XFS 20GB <-Only for games or other 3rd party software.

***Note :- The root partition will give you a false  error report about its size (during the installation setup stage).  This error message can be ignored, as it is assumes that you have all the other directory s within that same partition.  Which is not the case in this example.***


[QUOTE=Yezinki]
7. aMSN not being able to use the cam apart from Ekiga.....kindly have a look at this link suggesting which to install or what binaries Tcl/Tk to upgrade??

    a. [http://www.amsn-project.net/linux-downloads.php](http://www.amsn-project.net/linux-downloads.php)

    b. [http://packages.ubuntu.com/search?keywords=search](http://packages.ubuntu.com/search?keywords=search)

    c. [http://www.amsn-project.net/forums/viewforum.php?f=2](http://www.amsn-project.net/forums/viewforum.php?f=2)

    d. [http://www.amsn-project.net/forums/viewtopic.php?t=4432](http://www.amsn-project.net/forums/viewtopic.php?t=4432)
[/quote]

OK it is possible that its to do with the tcl/tk 8.5 libs.  I might look into compiling aMSN against tcl/tk 8.4 just to see if that is the case.

I'll work on that this weekend.  That will be fun.  


[QUOTE=Yezinki]
8. In one of the posts I was going through, I checked my connectivity for the cam........& I think that is the reason that my cam doesn't function....error displayed which I am attaching too is that I am fire walled or behind a router.

9. I use zoom adsl modem X6....... [http://www.zoom.com/products/adsl_overview.html#5590](http://www.zoom.com/products/adsl_overview.html#5590) X6...is the modem's firewall or Ubuntu 8.10s?[/quote]

I don't think its the modem, it possibly is the Ubuntu firewall.  I'll be testing this out for a work around as well.  I remember doing that some time ago in the past.  I know you don't need to bring down the firewall.  You only just need to add a rule to iptables.

I'll also write this up in the weekend. 


[QUOTE=Yezinki]
10. How do I connect this Sony machine using wifi......it's a BCM 802.11g PCI-E Adapter?[/QUOTE]

Your Kernel log says that the wifi card is working ok.

```

Nov  5 15:47:31 ubuntu-laptop kernel: [   11.349137] cfg80211: Using static regulatory domain info 
Nov  5 15:47:31 ubuntu-laptop kernel: [   11.349142] cfg80211: Regulatory domain: US 
Nov  5 15:47:31 ubuntu-laptop kernel: [   11.349144] ^I(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
Nov  5 15:47:31 ubuntu-laptop kernel: [   11.349148] ^I(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm) 
Nov  5 15:47:31 ubuntu-laptop kernel: [   11.349151] ^I(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm) 
Nov  5 15:47:31 ubuntu-laptop kernel: [   11.349155] ^I(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm) 
Nov  5 15:47:31 ubuntu-laptop kernel: [   11.349158] ^I(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm) 
Nov  5 15:47:31 ubuntu-laptop kernel: [   11.349161] ^I(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm) 
Nov  5 15:47:31 ubuntu-laptop kernel: [   11.349164] ^I(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm) 
Nov  5 15:47:31 ubuntu-laptop kernel: [   11.349168] cfg80211: Calling CRDA for country: US 
Nov  5 15:47:31 ubuntu-laptop kernel: [   11.716773] b43-phy0: Broadcom 4311 WLAN found 
Nov  5 15:47:31 ubuntu-laptop kernel: [   11.784591] phy0: Selected rate control algorithm 'pid' 
Nov  5 15:47:31 ubuntu-laptop kernel: [   11.864901] Broadcom 43xx driver loaded [ Features: PMLR, Firmware-ID: FW13 ]
```



[QUOTE=Yezinki]
11. Lastly my machine is reading the MMC drives & opening its files/folders but won't either give options to format the card nor would open individual files....file format issue?
[/QUOTE]

You cannot format a mounted flash drive (or MMC drive).  You can install GParted to format any drive if you need to.

I don't think you have a file format issue, more of a permission issue. I might be able to fix that as well on the weekend.  It should be easy (fstab or user group).

---

### Post by linux23dragon on 2008-11-07
[QUOTE=Yezinki]
1. I see the network connection & by left clicking I see it checked but no bars?
[/QUOTE]

Ah so the wireless access point (modem) has an antenna?  Is it out of range?

See if you can get the modem closer to the PC.

It seems that you can connect to the Wifi network, but it has a very low signal strength.

---

### Post by linux23dragon on 2008-11-07
> **Yezinki said:**
> KING LINUX,

Have a look at my adsl modem's web console.......Fire wall......do you think I need to make any changes as according to aMSN connectivity results?

In windows both MSN & Yahoo function with out an issue with the same configuration?

Regards,

Yezinki.

Yea the modem is ok. You should enable the firewall.

---

### Post by Yezinki on 2008-11-07
> **linux23dragon said:**
> Ah so the wireless access point (modem) has an antenna?  Is it out of range?

See if you can get the modem closer to the PC.

It seems that you can connect to the Wifi network, but it has a very low signal strength.


Hello **[FONT="Arial"][SIZE="5"][COLOR="DarkRed"]KING LINUX![/COLOR][/SIZE][/FONT]**

How was work must be busy .........I had my hands full too with the patients.

Thanks for answering the queries.

Access point does have an antenna & is hardly 6 inches away from the desktop.

NO I cannot connect to the wifi .....only wired connection works.

No bars......

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-07
**[FONT="Arial"][SIZE="5"][COLOR="Red"]KING LINUX[/COLOR][/SIZE][/FONT]**

Could you care to make a partition strategy plan for Ubuntu only & a dual boot of XP MCE & Ubuntu, on   the 250 GB HD.

Personally would like a single OS i.e Ubuntu only.....but want to get familiar with it first......

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-07
```
[B]This is how I partition my own hard drive on my own Desktop PC.

ext3 and XFS are file systems I use in the following partitions:-


sda1 /boot ext3 200MB
sda2 /usr XFS 20GB
sda3 /var XFS 5GB
sda4 ->logical drive<-
sda5 / XFS 1GB <- root partition
sda6 /tmp XFS 13GB
sda7 SWAP 512MB <- swap space
sda8 /home XFS The Partition size? As big as you can for /home.


***Optional partition***

sda9 /usr/local XFS 20GB <-Only for games or other 3rd party software.
[/B]
```

Hello **[SIZE="5"][COLOR="Red"]KING LINUX![/COLOR][/SIZE]**

How do you partition your desktop's HD?

Do you use Manual partitioning option while doing a clean install or G parted?

What's the logic behind  boot, usr, var, tmp, home partitions & pros of XFS file system?

Since you experiment new  things alot, do you image your drive/OS once you make a clean install....if yes what imaging utility do you use?

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-07
> **Yezinki said:**
> Hello **[FONT="Arial"][SIZE="5"][COLOR="DarkRed"]KING LINUX![/COLOR][/SIZE][/FONT]**

How was work must be busy .........I had my hands full too with the patients.

Thanks for answering the queries.

Access point does have an antenna & is hardly 6 inches away from the desktop.

NO I cannot connect to the wifi .....only wired connection works.

No bars......

Regards,

Yezinki.

Six inches is a bit too close try placing the modem 2 meters or more away from the desktop PC.

Is the WiFi enabled within the modem (wireless settings)?

---

### Post by linux23dragon on 2008-11-07
> **Yezinki said:**
> **[FONT="Arial"][SIZE="5"][COLOR="Red"]KING LINUX[/COLOR][/SIZE][/FONT]**

Could you care to make a partition strategy plan for Ubuntu only & a dual boot of XP MCE & Ubuntu, on   the 250 GB HD.

Personally would like a single OS i.e Ubuntu only.....but want to get familiar with it first......

Regards,

Yezinki.

You have already seen the Ubuntu only partition method, but if you want windows on the same drive (with backup possibilities) then read on. 

I just use the Ubuntu installation disk to partition the hard drive first (even install Ubuntu).  But afterwards install Windows in (formating both C:/ and D:/ drives with windows). Then reinstall ubuntu.  Reinstalling Ubuntu is just to ensure you have grub installed in your master boot record.  I can install the master boot record without reinstalling ubuntu myself, but it might be a bit too complicated to show you on how that is done ATM. 

You might need to edit the ***/boot/grub/menu.lst*** file to make it easier to duel boot one or the other Operating systems.  Windows is meant to be able to duel boot any OS as well, but I have not seen it in operation myself yet. 

You can also run windows in a virtual machine while running Ubuntu (two systems running at the same time on one PC).  I've done that before as you can see [[COLOR="Blue"]_***here***_[/COLOR]]("http://adam.com.au/linux23d/linux23d/Screenshot.png").  So that is another option you have as well.  




This is how you can partition your hard drive for your own Desktop PC if you also need Xp/Vista installed (duel boot system), using Ubuntu installation disk to partition the drive.

ext3 and XFS are file systems I use in the following partitions:-

sda1 C:/  NTFS ~50GB to 100GB <-- Windows formatted
sda2 D:/  NTFS ~50GB to 100GB <-- Windows formatted (for windows backup image) Must be equal size to C:/ drive
sda3 /boot ext3 200MB
sda4 ->logical drive<-
sda5 / XFS 1GB <- root partition
sda6 /usr XFS 20GB
sda7 /var XFS 5GB
sda8 /tmp XFS 13GB
sda9 SWAP 512MB <- swap space
sda10 /home XFS The Partition size? As big as you can for /home.

Master boot record must be installed on sda (or sda0)


***Note :- During the partitioning setup (With Ubuntu). The root partition will give you a false error report about its size (during the installation setup stage). This error message can be ignored, as it is assumes that you have all the other directory s within that same partition. Which is not the case in this example.***

---

### Post by linux23dragon on 2008-11-07
[QUOTE=Yezinki]
How do you partition your desktop's HD?

Do you use Manual partitioning option while doing a clean install or G parted?
[/quote]

I use manual the partitioning mode while installing Ubuntu.

[QUOTE=Yezinki]
What's the logic behind  boot, usr, var, tmp, home partitions & pros of XFS file system?
[/quote]

I just do that for basic hard drive integrity, maintenance and performance benefits.  It can come down to understanding how file systems work, (and the benefits of partitioning) to see what I mean by all of that.  

Please read this article on the [[COLOR="Blue"]*_**XFS File system benefits**_*[/COLOR]]("http://www.ibm.com/developerworks/library/l-fs9.html")

But hopefully you get the basic idea.

[QUOTE=Yezinki]
Since you experiment new  things alot, do you image your drive/OS once you make a clean install....if yes what imaging utility do you use?
[/QUOTE]

I have never had the need to image my OS.  I have backed up my own home drive on to DVD, and that's about it.  I would recommend backing up your email and bookmarks via the actual clients used (for example Firefox and evolution have such a backup/restore utility).

---

### Post by Yezinki on 2008-11-07
> **linux23dragon said:**
> Six inches is a bit too close try placing the modem 2 meters or more away from the desktop PC.

Is the WiFi enabled within the modem (wireless settings)?


Hi **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUS KING![/COLOR][/SIZE][/FONT]**

I will place it a bit farther as you said but works fine with windows...@ 54 MB/s.

Yes the wifi is enabled....Encryption WPA-2.

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-07
> **Yezinki said:**
> Hi **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUS KING![/COLOR][/SIZE][/FONT]**

I will place it a bit farther as you said but works fine with windows...@ 54 MB/s.

Yes the wifi is enabled....Encryption WPA-2.

Regards,

Yezinki.

I'll look into it after I figure out the aMSN installation.

In the mean time, try to search for any info about ***Broadcom 43xx 8.10 wifi***.  Its possible that there may already be a solution for you on the ubuntu forums.

Regards
Dave

---

### Post by Yezinki on 2008-11-07
You are one [FONT="Arial"]**[SIZE="5"][COLOR="Red"]GENIUS MAN LINUX KING![/COLOR][/SIZE]**[/FONT]

1. Firstly let me appreciate, admire your depth of knowledge.

2. I tried once some time ago to dual boot XP MCE & Ubuntu Hardy......it did OK...first installed XP MCE, than using Acronis Disk Director created a Logical D NTFS......50 GB was C Primary & 100 GB D Logical.......I was left with 100 GB approx FREE space....than installed Hardy 20 GB for /, 70 GB for /home & rest swap.........file system ext 3.

3. Man your style is really too good & very professional.

4. sda 1-10 are named automatically....a little confusing lol for a noob like me?

5. Wish I am able to partition as you do....I will need to practise first on  my desktop?

6. If am successful might even try it on XPS laptop.

7. If I try & am stuck than shall ask for your assistance using XPS laptop running Vista at the moment.

8. The issue with Sony(DELL too) XP MCE DVD is that in BIOS it has a setting to read only C as HD, D as SD/MMC & E as optical drive.......when installing XP MCE it deletes/formats all of HD......The settings in the BIOS or some deal btw Sony & MS while installing XP MCE it does not give the option of partitioning the HD as compared to the retail version of XP......so if I dual boot I shall have to modify the strategy ......like said earlier Install XP MCE using Sony's OEM DVD....than using Acronis partition the drive into a Logical D & format it.....rename drives...in windows now it shall be C & D HD, E for SD/MMC & F for optical......than install Ubuntu.....but all drive letters sda's will be messed up.....so probably forget about a dual boot ......thanks to BIOS & Sony's OEM XP MCE DVD.......this OEM will not run even in vbox, since the key/code is in the BIOS......so back to square 1........Ubuntu on Sony  & Vista on Dell.

9. I am again impressed by desktop back ground......you certainly are the KING.......have all the qualities.

10 I appreciate your confidence which I like in pros, that you experiment so much still don't image your OS........you are one smart man.

11. HD size is 250 GB but on ground it's 232 GB just telling you.

12. The OEM issue I am facing give it a thought....other wise I shall go for a single boot.

13. Since it would be my first time, if I get stuck I wont be able to message you from this machine but from laptop with no screen shots.

14. You describe /usr is that the same as /?  & what is var & temp for?

15. I again appreciate your taking out the time to make a plan for dual boot for Sony.

16 . I shall have a look at  the single boot plan  & your reply to this before i start any thing.

17. PC tech came last evening but was busy with patients in my office so he went back...I desperately want to take pics, details of the TV Tuner just to let you know so that you can technically recommend to replace it with which brand etc.

My best Regards,

Yezinki.

16.

---

### Post by Yezinki on 2008-11-07
Hi **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUX KING![/COLOR][/SIZE][/FONT]**

Can't find the partition strategy plan for a single OS, Ubuntu only for the Sony's 250 GB drive?

The one you posted earlier, is yours desk top's drive plan??

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-07
[B]his is how I partition my own hard drive on my own Desktop PC.

ext3 and XFS are file systems I use in the following partitions:-


sda1 /boot ext3 200MB
sda2 /usr XFS 20GB
sda3 /var XFS 5GB
sda4 ->logical drive<-
sda5 / XFS 1GB <- root partition
sda6 /tmp XFS 13GB
sda7 SWAP 512MB <- swap space
sda8 /home XFS The Partition size? As big as you can for /home.


***Optional partition***

sda9 /usr/local XFS 20GB <-Only for games or other 3rd party software.
[/B]

Oh sorry got it.....Thanks any ways!

---

### Post by Yezinki on 2008-11-07
Hi **[FONT="Arial"][SIZE="5"][COLOR="Red"]LNUX KING![/COLOR][/SIZE][/FONT]**


While reading the plans for a single or a dual boot a few question came in my mind?

1. sda 1,2,3 are Primary Partitions?

2. sda 4 is Logical contains 5-10.

3. Why 1 GB for root & the logic of root?

4. Default /,  is sda 2 or 6 where Ubuntu is installed?

5. What the utility of sda 3 or 7  /var 3-5 GB?

6.  & this sda 6 Or 8 /tmp / XFS 13 GB?

7. You make a Boot 200 MB on both single & dual boot.......its utilization?

8. In dual boot why should C & D NTFS be of equal sizes?

9. Is  /boot/grub/menu.lst file, present in both single & dual boot & where does it reside?

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-08
Hi Yezinki

I've written up a script to install aMSN using tcl/tk 8.4.  The current Ubuntu-8.10 uses tcl/tk 8.5 (which does look nicer).  Helpfully, it will confirm if tcl/tk is causing the *back view* webcam issues or not.

It won't fix the firewall issues.  I'm yet to post the iptable rules to fix that.

The following code will remove the current aMSN (already installed), and install the correct development packages to build against tcl/tk8.4. 

When the new aMSN build is finished, it will copy a new amsn_0.97.2-1.deb onto your desktop.  You only need to double click on the package to install it on your system.   

```
sudo apt-get purge amsn amsn-data tcl8.5-dev tk8.5-dev &&
sudo apt-get install build-essential dpkg-dev tcl8.4 tcl8.4-dev tk8.4 tk8.4-dev libpng12-0 libpng12-dev libjpeg62 libjpeg62-dev libsnack2-dev debhelper &&
wget http://internode.dl.sourceforge.net/sourceforge/amsn/amsn-0.97.2.tar.bz2 &&
tar xf amsn-0.97.2.tar.bz2 &&
cd amsn-0.97.2 &&
./configure &&
make deb &&
cp distrib/DEB/amsn_0.97.2-1.deb ~/Desktop/
```

To remove the new aMSN new package, the following code should do the trick.

 ```
sudo apt-get purge amsn
```

Next post should help with the wifi issues.  Fingers crossed.

Edit: I can do the same thing with aMSN with tcl/tk 8.5 as well.  Just need to use a different *configure* command, Id say.

---

### Post by Yezinki on 2008-11-08
ubuntu@ubuntu-laptop:~$ sudo apt-get purge amsn amsn-data tcl8.5 tcl8.5-dev tk8.5 tk8.5-dev &&
> sudo apt-get install build-essential dpkg-dev tcl8.4 tcl8.4-dev tk8.4 tk8.4-dev libpng12-0 libpng12-dev libjpeg62 libjpeg62-dev libsnack2-dev &&
> wget [http://internode.dl.sourceforge.net/sourceforge/amsn/amsn-0.97.2.tar.bz2](http://internode.dl.sourceforge.net/sourceforge/amsn/amsn-0.97.2.tar.bz2) &&
> tar xf amsn-0.97.2.tar.bz2 &&
> cd amsn-0.97.2 &&
> ./configure &&
> make deb &&
> cp distrib/DEB/amsn_0.97.2-1.deb ~/Desktop/
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package amsn is not installed, so not removed
Package amsn-data is not installed, so not removed
Package tcl8.5-dev is not installed, so not removed
Package tk8.5-dev is not installed, so not removed
The following packages were automatically installed and are no longer required:
  tcl-tls
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  tcl8.5* tk8.5*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 7692kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 126429 files and directories currently installed.)
Removing tk8.5 ...
Purging configuration files for tk8.5 ...
Removing tcl8.5 ...
Purging configuration files for tcl8.5 ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
dpkg-dev is already the newest version.
tcl8.4 is already the newest version.
tcl8.4-dev is already the newest version.
tk8.4 is already the newest version.
tk8.4-dev is already the newest version.
libpng12-0 is already the newest version.
libpng12-dev is already the newest version.
libjpeg62 is already the newest version.
libjpeg62-dev is already the newest version.
libsnack2-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  tcl-tls
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--2008-11-08 10:24:23--  [http://internode.dl.sourceforge.net/sourceforge/amsn/amsn-0.97.2.tar.bz2](http://internode.dl.sourceforge.net/sourceforge/amsn/amsn-0.97.2.tar.bz2)
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3431430 (3.3M) [application/x-tar]
Saving to: `amsn-0.97.2.tar.bz2.1'

100%[=====================================================================================================================================================================>] 3,431,430   59.8K/s   in 58s     

2008-11-08 10:25:22 (58.0 KB/s) - `amsn-0.97.2.tar.bz2.1' saved [3431430/3431430]

checking for prefix by checking for wish... /usr/bin/wish
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking tcl build dir... using tcl library in /usr/lib/tcl8.4
checking tk build dir... using tk library in /usr/lib/tk8.4
checking for main in -lstdc++... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for png_read_info in -lpng... yes
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking for jpeg_CreateDecompress in -ljpeg... yes
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking jerror.h usability... yes
checking jerror.h presence... yes
checking for jerror.h... yes
checking for ftello... yes
checking for fseeko... yes
checking for getpt... yes
checking for strcasestr... yes
checking for memmem... yes
checking for dlopen... no
checking for pthread_create in -lpthread... yes
checking if mmx should be used... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating utils/linux/capture/config.h
config.status: utils/linux/capture/config.h is unchanged

compile time options summary
============================

    X11          : yes
    Tcl		 : 8.4
    TK 		 : 8.4
    DEBUG        : no
    STATIC       : no

mkdir -p ./distrib/DEB
sed "s/#VERSION#/0.97.2-1/" debian/changelog.in > debian/changelog
sed "s/#TCL_VERSION#/8.4/" debian/control.in > debian/control.tmp
sed "s/#TK_VERSION#/8.4/" debian/control.tmp > debian/control
rm debian/control.tmp
fakeroot debian/rules clean
make[1]: Entering directory `/home/ubuntu/amsn-0.97.2'
dh_testdir
make[1]: dh_testdir: Command not found
make[1]: *** [clean] Error 127
make[1]: Leaving directory `/home/ubuntu/amsn-0.97.2'
make: *** [deb] Error 2
ubuntu@ubuntu-laptop:~/amsn-0.97.2$ 

[B]
Had to paste the command twice.......no package yet KING?[/B]

---

### Post by Yezinki on 2008-11-08
KING how do I install the new aMSN?

Regards!

Yezinki.

---

### Post by Yezinki on 2008-11-08
ubuntu@ubuntu-laptop:~$ sudo apt-get purge amsn amsn-data tcl8.5-dev tk8.5-dev &&
> sudo apt-get install build-essential dpkg-dev tcl8.4 tcl8.4-dev tk8.4 tk8.4-dev libpng12-0 libpng12-dev libjpeg62 libjpeg62-dev libsnack2-dev &&
> wget [http://internode.dl.sourceforge.net/sourceforge/amsn/amsn-0.97.2.tar.bz2](http://internode.dl.sourceforge.net/sourceforge/amsn/amsn-0.97.2.tar.bz2) &&
> tar xf amsn-0.97.2.tar.bz2 &&
> cd amsn-0.97.2 &&
> ./configure &&
> make deb &&
> cp distrib/DEB/amsn_0.97.2-1.deb ~/Desktop/
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package amsn is not installed, so not removed
Package amsn-data is not installed, so not removed
Package tcl8.5-dev is not installed, so not removed
Package tk8.5-dev is not installed, so not removed
The following packages were automatically installed and are no longer required:
  tcl-tls
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
dpkg-dev is already the newest version.
tcl8.4 is already the newest version.
tcl8.4-dev is already the newest version.
tk8.4 is already the newest version.
tk8.4-dev is already the newest version.
libpng12-0 is already the newest version.
libpng12-dev is already the newest version.
libjpeg62 is already the newest version.
libjpeg62-dev is already the newest version.
libsnack2-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  tcl-tls
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--2008-11-08 10:30:31--  [http://internode.dl.sourceforge.net/sourceforge/amsn/amsn-0.97.2.tar.bz2](http://internode.dl.sourceforge.net/sourceforge/amsn/amsn-0.97.2.tar.bz2)
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3431430 (3.3M) [application/x-tar]
Saving to: `amsn-0.97.2.tar.bz2.2'

100%[=====================================================================================================================================================================>] 3,431,430   49.2K/s   in 59s     

2008-11-08 10:31:31 (56.8 KB/s) - `amsn-0.97.2.tar.bz2.2' saved [3431430/3431430]

checking for prefix by checking for wish... /usr/bin/wish
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking tcl build dir... using tcl library in /usr/lib/tcl8.4
checking tk build dir... using tk library in /usr/lib/tk8.4
checking for main in -lstdc++... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for png_read_info in -lpng... yes
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking for jpeg_CreateDecompress in -ljpeg... yes
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking jerror.h usability... yes
checking jerror.h presence... yes
checking for jerror.h... yes
checking for ftello... yes
checking for fseeko... yes
checking for getpt... yes
checking for strcasestr... yes
checking for memmem... yes
checking for dlopen... no
checking for pthread_create in -lpthread... yes
checking if mmx should be used... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating utils/linux/capture/config.h
config.status: utils/linux/capture/config.h is unchanged

compile time options summary
============================

    X11          : yes
    Tcl		 : 8.4
    TK 		 : 8.4
    DEBUG        : no
    STATIC       : no

mkdir -p ./distrib/DEB
sed "s/#VERSION#/0.97.2-1/" debian/changelog.in > debian/changelog
sed "s/#TCL_VERSION#/8.4/" debian/control.in > debian/control.tmp
sed "s/#TK_VERSION#/8.4/" debian/control.tmp > debian/control
rm debian/control.tmp
fakeroot debian/rules clean
make[1]: Entering directory `/home/ubuntu/amsn-0.97.2'
dh_testdir
make[1]: dh_testdir: Command not found
make[1]: *** [clean] Error 127
make[1]: Leaving directory `/home/ubuntu/amsn-0.97.2'
make: *** [deb] Error 2
ubuntu@ubuntu-laptop:~/amsn-0.97.2$

---

### Post by linux23dragon on 2008-11-08
> **Yezinki said:**
> KING how do I install the new aMSN?

Regards!

Yezinki.

Sorry, I forgot to mention that you need to remove the tar ball (***amsn-0.97.2.tar.bz2***) and the decompressed directory if you are to run the script more than once.

When I tested that script on my own system it worked.  So I might of forgotten a package that might need to be installed on your PC.  As it is already installed on mine. 


I think I have found a solution to the wifi but I will try two methods to fix it.

One is trying out kernel back ports modules and the other is loading the ipw2200 kernel module.

---

### Post by linux23dragon on 2008-11-08
I have added a package in this revised script for aMSN


```
sudo apt-get purge amsn amsn-data tcl8.5 tcl8.5-dev tk8.5 tk8.5-dev &&
sudo apt-get install build-essential dpkg-dev tcl8.4 tcl8.4-dev tk8.4 tk8.4-dev libpng12-0 libpng12-dev libjpeg62 libjpeg62-dev libsnack2-dev debhelper &&
wget http://internode.dl.sourceforge.net/sourceforge/amsn/amsn-0.97.2.tar.bz2 &&
tar xf amsn-0.97.2.tar.bz2 &&
cd amsn-0.97.2 &&
./configure &&
make deb &&
cp distrib/DEB/amsn_0.97.2-1.deb ~/Desktop/
```

I've tested it on my own pc.  Please test.  Hopfully you will now have all of the dependences.


Update on the WiFi card.  Back in the days when the Dell 1520 came out, the firmware needed to be installed.  today it look like you might need to add the line *ipw2200* into /etc/modules.

This will command will open up the */etc/modules* file.  just add ipw2200 at the end of the file.  Then save and exit gedit, and reboot.
```
sudo gedit /etc/modules
```

Edit.  Please check that the driver is not blacklisted in */etc/modprobe.d/blacklist* as well.

---

### Post by linux23dragon on 2008-11-08
[QUOTE=Yezinki]

1. Firstly let me appreciate, admire your depth of knowledge.
[/quote]


Thanks Yezinki 

My depth of knowledge started with [COLOR="Blue"]www.linuxfromscratch.org[/COLOR] and then [COLOR="Blue"]www.diy-linux.org
[/COLOR]
It was the only way to learn Linux OS design, for me. 

[QUOTE=Yezinki]
4. sda 1-10 are named automatically....a little confusing lol for a noob like me?
[/quote]

It will become easier when you try to manually set up the partitions your self.   

[QUOTE=Yezinki]
5. Wish I am able to partition as you do....I will need to practise first on  my desktop?
[/quote]

Yes, its the only way to learn. play :) 

[QUOTE=Yezinki]
6. If am successful might even try it on XPS laptop.
[/quote]

cool

[QUOTE=Yezinki]
7. If I try & am stuck than shall ask for your assistance using XPS laptop running Vista at the moment.
[/quote]

Lots of people may have already posted about setting up Ubuntu with this laptop.  

It would be easer to support you if I actually had one myself to test with.  That is how I wrote up a how too for the [[COLOR="Blue"]_***Dell 1520***_[/COLOR]]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=501195").

[QUOTE=Yezinki]
8. The issue with Sony(DELL too) XP MCE DVD is that in BIOS it has a setting to read only C as HD, D as SD/MMC & E as optical drive.......when installing XP MCE it deletes/formats all of HD......The settings in the BIOS or some deal btw Sony & MS while installing XP MCE it does not give the option of partitioning the HD as compared to the retail version of XP......so if I dual boot I shall have to modify the strategy ......like said earlier Install XP MCE using Sony's OEM DVD....than using Acronis partition the drive into a Logical D & format it.....rename drives...in windows now it shall be C & D HD, E for SD/MMC & F for optical......than install Ubuntu.....but all drive letters sda's will be messed up.....so probably forget about a dual boot ......thanks to BIOS & Sony's OEM XP MCE DVD.......this OEM will not run even in vbox, since the key/code is in the BIOS......so back to square 1........Ubuntu on Sony  & Vista on Dell.
[/quote] 

That is typical with custom hardware.  I myself would work on it to death (if I had one) until it worked the way I liked it too (if possible).

 

[QUOTE=Yezinki]
9. I am again impressed by desktop back ground......you certainly are the KING.......have all the qualities.
[/quote]

Believe it or not.  It is a Vista wall paper that was downloaded of the web, before Vista was released.  Most of the wall papers sucked, but some were nice to the eye.

I have to remember were I got it from.  It was two years ago or so.

The rest of the theme was from gnome-look.org.

You can see the same theme in my very own custom built linux system on my [[COLOR="Blue"]_***Personal Web page***_[/COLOR]]("http://www.adam.com.au/linux23d/")

[QUOTE=Yezinki]
11. HD size is 250 GB but on ground it's 232 GB just telling you.
[/quote]

Cool, you only need to adjust the windows partition size to compensate.


[QUOTE=Yezinki]
14. You describe /usr is that the same as /?  & what is var & temp for?
[/quote]

/usr resides in / but I had just put them in separate partitions.  I did that to keep the application and system libs and basic tools seperate from each other. 

It has its servicing advantages.  Especially if your building your own Linux system, using LFS or DIY-linux books. 

The seperate /tmp directory is very important.  You really need to make sure that you have enough hard drive space for burning double sided DVDs or recording streaming Audio and Video at any one time.

The /var partion is also often written to.  But at lest you can control were the data is written, and you know how much hard drive space is dedicated to applications (garanteed).  So it is yet another useful servicing tool you can use.  

If you were to use your desktop as a server, then you would need the /var directory to be much larger than 4-5 GB. And depending on the server type or setup, can reduce the /home directory size.

So in the end, you are in control on how your data is used on your hard drive.


[QUOTE=Yezinki]
16 . I shall have a look at  the single boot plan  & your reply to this before i start any thing.
[/quote]

Sure thing.


[QUOTE=Yezinki]
17. PC tech came last evening but was busy with patients in my office so he went back...I desperately want to take pics, details of the TV Tuner just to let you know so that you can technically recommend to replace it with which brand etc.
16.[/QUOTE]

It would be interesting to see.  Perhaps you can also let the developers know about it (if it looks like it can work with current drivers).

Never know your luck.

---

### Post by Yezinki on 2008-11-08
I have rebooted but what do I add here KING.......

---

### Post by Yezinki on 2008-11-08
KING LINUX aMSN still displays in preferences> connectivity that I am fire walled........??

---

### Post by Yezinki on 2008-11-08
**[FONT="Arial"][SIZE="5"][COLOR="Red"]WOW LINUX KING!![/COLOR][/SIZE][/FONT]**

What a web page.........

If it was in my hands i'd make the Global/Chief Moderator for ALL sub forums of Ubuntu.

Thanks,

**[FONT="Arial"][SIZE="6"][COLOR="Black"]You are No 1 the BEST I have ever met.........[/COLOR][/SIZE][/FONT]**

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-08
Awesome pics of the Pyramids.......

Would you make my web page lol.........

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-08
> **Yezinki said:**
> Hi **[FONT="Arial"][SIZE="5"][COLOR="Red"]LNUX KING![/COLOR][/SIZE][/FONT]**


While reading the plans for a single or a dual boot a few question came in my mind?

1. sda 1,2,3 are Primary Partitions?

2. sda 4 is Logical contains 5-10.

3. Why 1 GB for root & the logic of root?

4. Default /,  is sda 2 or 6 where Ubuntu is installed?

5. What the utility of sda 3 or 7  /var 3-5 GB?

6.  & this sda 6 Or 8 /tmp / XFS 13 GB?

7. You make a Boot 200 MB on both single & dual boot.......its utilization?

8. In dual boot why should C & D NTFS be of equal sizes?

9. Is  /boot/grub/menu.lst file, present in both single & dual boot & where does it reside?

Regards,

Yezinki.



For your comments please when ever..........

Regards,

Yezinki.

**PS: I can see the windows using guys cam but mine wont work??**

---

### Post by Yezinki on 2008-11-08
Similar issue with Koepte.......

---

### Post by linux23dragon on 2008-11-08
> **Yezinki said:**
> Similar issue with Koepte.......

Hit the options tab and un-check *correct colors * and *Adjust Brightness/contrast*.  Then click the apply button. you might need to restart kopete.

---

### Post by Yezinki on 2008-11-08
Cam works GREAT only in Ekiga......now this a zoom in pic not a normal sized one... lol.......

---

### Post by linux23dragon on 2008-11-08
> **Yezinki said:**
> KING LINUX aMSN still displays in preferences> connectivity that I am fire walled........??

we need to make the webcam work first.  Then the firewall rules after.

---

### Post by Yezinki on 2008-11-08
Still same........:(

---

### Post by linux23dragon on 2008-11-08
[QUOTE=Yezinki]
While reading the plans for a single or a dual boot a few question came in my mind?

1. sda 1,2,3 are Primary Partitions?
[/quote]

Correct


[QUOTE=Yezinki]
2. sda 4 is Logical contains 5-10.
[/quote]

Correct

[QUOTE=Yezinki]
3. Why 1 GB for root & the logic of root?
[/quote]

For support reasons.  if you look at any support forum, how too or news article, they always have root as the 5th partition per example.  

[QUOTE=Yezinki]
4. Default /,  is sda 2 or 6 where Ubuntu is installed?
[/quote]

The default ubutu installation is in / (root).  The other partitions reside in root.

[QUOTE=Yezinki]
5. What the utility of sda 3 or 7  /var 3-5 GB?
[/quote]

I'm not sure what you mean by utility.  

*/var* holds logs and package management data and server files.  The size of var is safer if you choose around 3-5GB.
*SWAP* is there just in case you run out of ram.  When you setup swap you will see why I just write SWAP. 

[QUOTE=Yezinki]
6.  & this sda 6 Or 8 /tmp / XFS 13 GB?
[/quote]

/tmp is 13GB whch is a safe size for burnning double sided DVDs.

Root should only be 1GB in size with this setup.

[QUOTE=Yezinki]
7. You make a Boot 200 MB on both single & dual boot.......its utilization?
[/quote]

Correct, You will not need any more space for /boot.  It is in a separate partition for support reasons also.  The most useful example is that you can wipe out your distro (on the other partitions and you still can boot to another OS installed on your system using the same boot manager.  And of course other systems can only touch /boot.  Not any other part of your hard drive (as the partitions are not mounted or easily accessible).

I can go on too 

[QUOTE=Yezinki]
8. In dual boot why should C & D NTFS be of equal sizes?
[/quote]
I have seen packages like ghost that expect the image drive to bee the same size as the working drive. 


[QUOTE=Yezinki]
9. Is  /boot/grub/menu.lst file, present in both single & dual boot & where does it reside?
[/quote]

Each operating system will have is own /boot location.  But you would want to use the same boot loader to dual boot.  So you will use the same */boot/grub/menu.lst* file for both Windows and any other Linux OS system.  

I have done that before.  But you need to manually do that by hand.
If you just using Windows and Ubuntu, then that should be a automatic setup for you.

But it can depend.

Best practise is to install windows first and then Linux.  That should (with most distributions) automate the boot loader correctly to setup dual boot for you.

---

### Post by linux23dragon on 2008-11-08
> **Yezinki said:**
> Still same........:(

Then it is possibly a bug in kopete or the driver.  Remember that your driver is newish.

---

### Post by Yezinki on 2008-11-08
I agree LINUX KING......

What about aMSN......it displays firewalled behind a router?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-08
Hypothetically if one only has Ubuntu linux distro & wants to reinstall it for some reason.....which partition should it go in?

/root?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-08
It displays this message when I click on the Debian aMSN package to install KING?

---

### Post by Yezinki on 2008-11-08
After installation,,,,,,

---

### Post by linux23dragon on 2008-11-08
> **Yezinki said:**
> After installation,,,,,,

Yep that worked.  excellent.

---

### Post by Yezinki on 2008-11-08
Now KING 2 issues are left to be dealt with.........

1. aMSN error.

2. Wifi 

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-08
> **Yezinki said:**
> Hypothetically if one only has Ubuntu linux distro & wants to reinstall it for some reason.....which partition should it go in?

/root?

Regards,

Yezinki.

Yes.

But if you have partitioned the drive like in my examples. Then you would need to pick the same partitions you had already maped out before, during the partitioning stage.

The only indication on what each partition is? Is only indicated by the partition numbering system (sda2 sda3 ....).  So it is a very good idea to keep a list (jst like the partition list I have posted), that details what each partition number is.

---

### Post by linux23dragon on 2008-11-08
> **Yezinki said:**
> Now KING 2 issues are left to be dealt with.........

1. aMSN error.

2. Wifi 

Regards,

Yezinki.

So the instructions I wrote for the wifi did not work out for you?

See [***_[COLOR="Blue"]Here[/COLOR]_***]("http://ubuntuforums.org/showpost.php?p=6128930&postcount=122")

---

### Post by linux23dragon on 2008-11-08
> **Yezinki said:**
> It displays this message when I click on the Debian aMSN package to install KING?

That's normal, because it is listed in the deb packages listings.  So you can ignore that message.

---

### Post by Yezinki on 2008-11-08
Hi **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUX KING[/COLOR][/SIZE][/FONT]**............


See for yourself wifi connected all 5 Blue bars........

Regards!

Yezinki.

---

### Post by Yezinki on 2008-11-08
aMSN still shows that I am firewalled or behind a router???????

---

### Post by linux23dragon on 2008-11-08
> **Yezinki said:**
> aMSN still shows that I am firewalled or behind a router???????

Yea. I'm looking into that now.

---

### Post by linux23dragon on 2008-11-08
I found a [***_[COLOR="Blue"]useful link[/COLOR]_***]("http://neosmart.net/wiki/display/EBCD/Ubuntu") for dual booting Vista and Ubuntu.


I have found a aMSN firewall solution [[COLOR="Blue"]_***here***_[/COLOR]]("http://amsn.sourceforge.net/devwiki/tiki-index.php?page=Webcam+In+aMSN#firewalled").

---

### Post by Yezinki on 2008-11-08
Can this link be used for XP too?

---

### Post by Yezinki on 2008-11-08
Personally I like your method of a dual boot......more  professional.

---

### Post by Yezinki on 2008-11-08
> **linux23dragon said:**
> I found a [***_[COLOR="Blue"]useful link[/COLOR]_***]("http://neosmart.net/wiki/display/EBCD/Ubuntu") for dual booting Vista and Ubuntu.


I have found a aMSN firewall solution [[COLOR="Blue"]_***here***_[/COLOR]]("http://amsn.sourceforge.net/devwiki/tiki-index.php?page=Webcam+In+aMSN#firewalled").

**[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUX KING[/COLOR][/SIZE][/FONT]**

Thanks for the link.

In Zoom  web console > Ports I see only HTTP & Telnet.....but the link says about TCP & UDP?

What should I do now?

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-08
> **Yezinki said:**
> **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUX KING[/COLOR][/SIZE][/FONT]**

Thanks for the link.

In Zoom  web console > Ports I see only HTTP & Telnet.....but the link says about TCP & UDP?

What should I do now?

Regards,

Yezinki.

Yea true.  It looks like you don't have all the configuration options as expected.   Do you have the firewall enabled in your router?

I'm not sure if enabling the firewall will give you more options to choose from.


I've attached a screen shot of my own router settings.  TCP & UDP is one of three options you can choose from (TCP or UDP or TCP and  UDP).

---

### Post by Yezinki on 2008-11-08
Hi **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUX KING![/COLOR][/SIZE][/FONT]**


1. Zoom webconsole is displayed by typing 10.0.0.2 in your browser.

2. If you could  kindly have a look whether I have the option of TCP/UDP  or not?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-08
Hi again [FONT="Arial"]**[SIZE="5"][COLOR="Red"]LINUX KING![/COLOR][/SIZE]**[/FONT]


 A few  queries as to partitioning is concerned, please clarify.....whether installing single OS or a dual boot.....
[B]
I just use the Ubuntu installation disk to partition the hard drive first (even install Ubuntu). But afterwards install Windows in (formating both C:/ and D:/ drives with windows). Then reinstall ubuntu. Reinstalling Ubuntu is just to ensure you have grub installed in your master boot record. I can install the master boot record without reinstalling ubuntu myself, but it might be a bit too complicated to show you on how that is done ATM.

You might need to edit the /boot/grub/menu.lst file to make it easier to duel boot one or the other Operating systems. Windows is meant to be able to duel boot any OS as well, but I have not seen it in operation myself yet.

You can also run windows in a virtual machine while running Ubuntu (two systems running at the same time on one PC). I've done that before as you can see here. So that is another option you have as well.




This is how you can partition your hard drive for your own Desktop PC if you also need Xp/Vista installed (duel boot system), using Ubuntu installation disk to partition the drive.

ext3 and XFS are file systems I use in the following partitions:-

sda1 C:/ NTFS ~50GB to 100GB <-- Windows formatted
sda2 D:/ NTFS ~50GB to 100GB <-- Windows formatted (for windows backup image) Must be equal size to C:/ drive
sda3 /boot ext3 200MB
sda4 ->logical drive<-
sda5 / XFS 1GB <- root partition
sda6 /usr XFS 20GB
sda7 /var XFS 5GB
sda8 /tmp XFS 13GB
sda9 SWAP 512MB <- swap space
sda10 /home XFS The Partition size? As big as you can for /home.

Master boot record must be installed on sda (or sda0)[/B]


1. You use Ubuntu CD to partition...using GParted utility?

2. For me as an end user do I need the partition var?

3. When is sda3/boot ext3 created?

4. What is sda9/tmp XFS for?

5. Where does this file edit the /boot/grub/menu.lst file ,reside?

6. As you said earlier that if there is a need to reinstall Ubuntu & one has all these partitions noted, than the it should be installed in sda6/usr XFS 20 GB?

7. Default /, is yours sda6/usr?

8. Lastly do explain the utility of var & tmp?

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-09
[QUOTE=Yezinki]
1. Zoom webconsole is displayed by typing 10.0.0.2 in your browser.
[/quote]

That is correct.  Your router uses the 10.0.0.2 address, and uses a unique web server page only available to your router.

 
My router uses the 192.168.1.1 address, and has a completely different inbuilt web server page. 


[QUOTE=Yezinki]
2. If you could  kindly have a look whether I have the option of TCP/UDP  or not?
[/QUOTE]

 

Just downloading your [***_[COLOR="Blue"]User manual[/COLOR]_***]("http://www.zoom.com/documentation/adsl/5590CF_UserGuide_Eng.pdf") now

Have a look at page 46.

---

### Post by Yezinki on 2008-11-09
Advanced Setup....

---

### Post by linux23dragon on 2008-11-09
[QUOTE=Yezinki]
A few  queries as to partitioning is concerned, please clarify.....whether installing single OS or a dual boot.....
[/quote]

This partition setup is for dual booting Windows and Ubuntu only.

[QUOTE=Yezinki]
1. You use Ubuntu CD to partition...using GParted utility?
[/quote]

I used the Ubuntu CD to partition my drive.


[QUOTE=Yezinki]
2. For me as an end user do I need the partition var?
[/quote]

No, but you can have /var as a separate partition if you know how it can benefit you.

So that is manly a option for advanced players.

I have /var as a separate partition because the system writes to it nearly as constantly as /tmp and /home gets written too.

Other people might need maintain /var even more, to the point of been able to extend or move to another partition size altogether.  So it all depends on how and/or what the system is been used for.

So having /var as a separate partition is a good way of monitoring its actual used volume size. 



[QUOTE=Yezinki]
3. When is sda3/boot ext3 created?
[/quote]

It will be created by the user when they first install Unbuntu (using the Ubuntu CD).

[QUOTE=Yezinki]
4. What is sda9/tmp XFS for?
[/quote]

/tmp is used by the X server, Desktops and other low level service applications that is needed by the end user.  /tmp is also used while recording or editing streaming video, audio and recording DVDs.

Having a separate partition size of 13GB ensures you will always have the space available for those application operations.  Also the same is true about common write access to hard drive (like /var).  

Also when you download files of the net, they will be cached in /tmp also. 
   
[QUOTE=Yezinki]
5. Where does this file edit the /boot/grub/menu.lst file ,reside?
[/quote]

If your going by the same file system setup I have posted (dual boot) it resides in sda3

The menu.lst file resides in /boot/grub/.  The menu.lst file can be edited by most console or graphical text editors, assuming you have root access.   


[QUOTE=Yezinki]
6. As you said earlier that if there is a need to reinstall Ubuntu & one has all these partitions noted, than the it should be installed in sda6/usr XFS 20 GB?
[/quote]

You will need to manually pick the same partitions you created to reinstall Ubuntu.  But the benefit here is that you won't need to reformat say, your /home drive.  This preserving the user content.  you will need to select and choose the file system used, but there is no need to format /home.

[QUOTE=Yezinki]
7. Default /, is yours sda6/usr?
[/quote]

The default / (root drive) is always sda5 or hda5.  The /usr partition (sda6) will reside or be mounted in / (root) 

[QUOTE=Yezinki]
8. Lastly do explain the utility of var & tmp?
[/QUOTE]

I've explained the /tmp function see above.   The /var directory is used for cahing, backups and system temporary files as well as security functions.  It can also be used as web server space as well.

However most of the server software should now reside in the /srv directory.  (witch also should be a separate partition (if used) for easy volume size monitoring).
 

Other questions answered about this subject is now linked [[COLOR="Blue"]***_here_***[/COLOR]]("http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=6129347&postcount=134") post #134

---

### Post by Yezinki on 2008-11-09
Thanks **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUS KING![/COLOR][/SIZE][/FONT]**

1. for the in depth clarification.

2. aMSN, no solution for my modem?

3. I called the pc tech & he should be coming, shall post the pics/details of the TV Tuner.

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-09
Will a reinstall of Ubuntu/format........ of /root...also change the desktop & other settings if yes...how to get them back....since the /home & other partitions would be preserved?

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-09
> **Yezinki said:**
> Thanks **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUS KING![/COLOR][/SIZE][/FONT]**

1. for the in depth clarification.

2. aMSN, no solution for my modem?

3. I called the pc tech & he should be coming, shall post the pics/details of the TV Tuner.

Regards,

Yezinki.

See if the computer tech can setup your router.  It is hard to help when I have never worked with your router.  There seems to be lots of options to check out.

---

### Post by linux23dragon on 2008-11-09
> **Yezinki said:**
> Will a reinstall of Ubuntu/format........ of /root...also change the desktop & other settings if yes...how to get them back....since the /home & other partitions would be preserved?


Nup, all user settings and files are safe in /home (if you don't format /home).  So it does not matter if you format / (root)

EDIT: That is assuming that you home is in a different partition.  Otherwise back up home on DVD

---

### Post by Yezinki on 2008-11-09
Thanks **[FONT="Arial"][SIZE="5"]LINUX KING![/SIZE][/FONT]**[COLOR="Red"][/COLOR]

1. Will check with him regarding the modem TCP/UDP.

2. So a reinstall & format of /root only, wont change the settings.. as you say they are safe in /home, how do you bring your previous desktop/ settings back on the new install.

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-09
> **Yezinki said:**
> Thanks **[FONT="Arial"][SIZE="5"]LINUX KING![/SIZE][/FONT]**[COLOR="Red"][/COLOR]

1. Will check with him regarding the modem TCP/UDP.

2. So a reinstall & format of /root only, wont change the settings.. as you say they are safe in /home, how do you bring your previous desktop/ settings back on the new install.

Regards,

Yezinki.


As long as the root partion is in a different partition to /home, then yes. of course you still can use /home as part of your new installation.  Just don't format it (/home).

If the new install won't allow you to use the same user name (from the previous install), then you can copy over the hidden files to your new user account (after setting the new ownership of the directorys/files).

Applications like evolution and Firefox have a backup/restore tools (mentioned earlier).  Those applications can only restore user settings in that manner.

---

### Post by Yezinki on 2008-11-09
[B]# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=cd3e4739-4ca0-422c-ad5a-6d7d45d769ac ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cd3e4739-4ca0-422c-ad5a-6d7d45d769ac

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash quiet

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		cd3e4739-4ca0-422c-ad5a-6d7d45d769ac
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cd3e4739-4ca0-422c-ad5a-6d7d45d769ac ro splash quiet 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		cd3e4739-4ca0-422c-ad5a-6d7d45d769ac
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cd3e4739-4ca0-422c-ad5a-6d7d45d769ac ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		cd3e4739-4ca0-422c-ad5a-6d7d45d769ac
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST[/B]

---

### Post by Yezinki on 2008-11-09
Hi **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUX KING[/COLOR][/SIZE][/FONT]**.........

Is this the grub menus lst you earlier mentioned........present at the moment in > File system/drive > boot > grub.

This is to be modified for XP MCE & Ubuntu dual boot...like how?

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-09
> **Yezinki said:**
> Hi **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUX KING[/COLOR][/SIZE][/FONT]**.........

Is this the grub menus lst you earlier mentioned........present at the moment in > File system/drive > boot > grub.

This is to be modified for XP MCE & Ubuntu dual boot...like how?

Regards,

Yezinki.

This version of menu.lst can be used for duel booting windows and Linux.
```

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color green/black light-green/black

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=cd3e4739-4ca0-422c-ad5a-6d7d45d769ac ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cd3e4739-4ca0-422c-ad5a-6d7d45d769ac

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash quiet

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-7-generic
uuid cd3e4739-4ca0-422c-ad5a-6d7d45d769ac
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=cd3e4739-4ca0-422c-ad5a-6d7d45d769ac ro splash quiet
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid cd3e4739-4ca0-422c-ad5a-6d7d45d769ac
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=cd3e4739-4ca0-422c-ad5a-6d7d45d769ac ro single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
uuid cd3e4739-4ca0-422c-ad5a-6d7d45d769ac
kernel /boot/memtest86+.bin
quiet

title Windows 95/98/NT/2000
root (hd0,0)
makeactive
chainloader +1


### END DEBIAN AUTOMAGIC KERNELS LIST

```

However, the default OS that will be booting will be Windows (after 15 seconds).  You can change any of the default settings as you like.

Edit: Creating the file is the first step

---

### Post by Yezinki on 2008-11-09
Thanks **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUX KING![/COLOR][/SIZE][/FONT]**


1. I feel will have to dual boot on this machine, Sony's OEM Recovery DVD for XP MCE wont run in vbox.

2. XP DVD hangs at a certain point which I fail to understand.

3. Vista installed OK.....but do I need to use the KB for every thing...the moment I bring the machine's mouse gives the error of capturing?

So kindly just have re look at the partition plan & care to edit the grub menu list (for XP MCE & Ubuntu dual boot) for this Sony 232 GB HD.

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-09
Vista........

---

### Post by linux23dragon on 2008-11-09
> **Yezinki said:**
> Vista........

Ah, my eyes. lol

---

### Post by Yezinki on 2008-11-09
why KING??

---

### Post by Yezinki on 2008-11-09
1.Vbox is still running, Vista installed but i have to use the KB?

2. At times I feel forget Sony's XP MCE & just single OS Ubuntu on this , thanks to you ....found all the drivers.

What are your personal views.......don't you agree Ubuntu on this & Vista on XPS 1710...

Regards,

Yezinki.[B][FONT="Arial"][SIZE="5"][COLOR="Red"]

BTW you are the BEST[/COLOR][/SIZE][/FONT][/B]

---

### Post by Yezinki on 2008-11-09
More shots....

---

### Post by Yezinki on 2008-11-09
LINUX KING...

What am I doing wrong in vbox?

It got installed but wont let me use the mouse nor connect to the net?

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-09
> **Yezinki said:**
> why KING??

Just playing around.

---

### Post by linux23dragon on 2008-11-09
> **Yezinki said:**
> 1.Vbox is still running, Vista installed but i have to use the KB?

2. At times I feel forget Sony's XP MCE & just single OS Ubuntu on this , thanks to you ....found all the drivers.

What are your personal views.......don't you agree Ubuntu on this & Vista on XPS 1710...

Regards,

Yezinki.[B][FONT="Arial"][SIZE="5"][COLOR="Red"]

BTW you are the BEST[/COLOR][/SIZE][/FONT][/B]

It a good combination for people who are new to Linux.  I used to dual boot when I first tried Linux.  But now I'm manly all Linux, becuse I can run lots of windows programs using WINE

---

### Post by linux23dragon on 2008-11-09
> **Yezinki said:**
> LINUX KING...

What am I doing wrong in vbox?

It got installed but wont let me use the mouse nor connect to the net?

Regards,

Yezinki.

You are not doing anything wrong.  The system can only use the mouse and keyboard on one working OS at a time.

I'm sure you can get sound and USB to work in virtual box.  Might need to add a line to the fstab file

Edit.  I have updated the menu.lst file code from my previous post Yezinki.

---

### Post by Yezinki on 2008-11-09
Hi KING,

Whats the command to check whether Ubuntu's firewall is ON & running,

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-09
> **Yezinki said:**
> Hi KING,

Whats the command to check whether Ubuntu's firewall is ON & running,

Regards,

Yezinki.

```
sudo ufw status
```

If it is not loaded, then iptables is not running.

I have yet again rewritten the menu.lst file for dual booting.

---

### Post by Yezinki on 2008-11-09
[B]ubuntu@ubuntu-laptop:~$ sudo ufw status
[sudo] password for ubuntu: 
Status: not loaded
ubuntu@ubuntu-laptop:~$ [/B]


KING what does this mean???

---

### Post by linux23dragon on 2008-11-09
> **Yezinki said:**
> [B]ubuntu@ubuntu-laptop:~$ sudo ufw status
[sudo] password for ubuntu: 
Status: not loaded
ubuntu@ubuntu-laptop:~$ [/B]


KING what does this mean???

The ufw is not running iptables I think.  You can run this command to run ufw:-

```
sudo ufw enable
```

Then restart the PC.  You might need to restart your router as well as the system may not connect to it.

I'll test that and see if that is the case.

---

### Post by linux23dragon on 2008-11-09
> **linux23dragon said:**
> The ufw is not running iptables I think.  You can run this command to run ufw:-

```
sudo ufw enable
```

Then restart the PC.  You might need to restart your router as well as the system may not connect to it.

I'll test that and see if that is the case.

Tested and working well for me :)

You only need to see the kernel log to confirm it.

**EDIT:** you can see why I now have a dedicated partition for /var.  The kernel log will get very large in size the longer the PC is connected to the net. 

[B][I]Nov  9 21:33:24 linux23dragon-desktop kernel: [   72.370336] [UFW BLOCK INPUT]: IN=ath0 OUT= MAC=00:1b:11:bb:ed:73:00:60:64:16:f4:ab:08:00:45:40:00:bc:00:00:40:00:40:11:b6:9d:c0:a8:01:01:c0:a8:01:02:08:00:c5:28:00:a8:81:9a:b2:e4:81:80:00:01:00:01:00:03:00:03:03:6e:74:70:06:75:62:75:6e:74:75:03:63:6f:6d:00:00:01:00:01:c0:0c:00:01:00:01:00:00:00:cb:00:04:5b:bd SRC=192.168.1.1 DST=192.168.1.2 LEN=188 TOS=0x00 PREC=0x40 TTL=64 ID=0 DF PROTO=UDP SPT=2048 DPT=50472 LEN=168 
Nov  9 21:33:37 linux23dragon-desktop kernel: [   85.289873] [UFW BLOCK INPUT]: IN=ath0 OUT= MAC=00:1b:11:bb:ed:73:00:60:64:16:f4:ab:08:00:45:40:00:ce:00:00:40:00:40:11:b6:8b:c0:a8:01:01:c0:a8:01:02:08:00:8e:ad:00:ba:9e:18:dd:82:81:80:00:01:00:02:00:03:00:03:05:73:74:61:72:74:06:75:62:75:6e:74:75:03:63:6f:6d:00:00:01:00:01:c0:0c:00:01:00:01:00:00:00:75:00:04 SRC=192.168.1.1 DST=192.168.1.2 LEN=206 TOS=0x00 PREC=0x40 TTL=64 ID=0 DF PROTO=UDP SPT=2048 DPT=36525 LEN=186 
Nov  9 21:33:50 linux23dragon-desktop kernel: [   98.684314] [UFW BLOCK INPUT]: IN=ath0 OUT= MAC=00:1b:11:bb:ed:73:00:60:64:16:f4:ab:08:00:45:40:01:66:00:00:40:00:40:11:b5:f3:c0:a8:01:01:c0:a8:01:02:08:00:b5:26:01:52:5e:19:f9:c7:81:80:00:01:00:05:00:07:00:05:0e:73:75:67:67:65:73:74:71:75:65:72:69:65:73:06:67:6f:6f:67:6c:65:03:63:6f:6d:00:00:01:00:01:c0:0c:00 SRC=192.168.1.1 DST=192.168.1.2 LEN=358 TOS=0x00 PREC=0x40 TTL=64 ID=0 DF PROTO=UDP SPT=2048 DPT=46374 LEN=338 
Nov  9 21:33:54 linux23dragon-desktop kernel: [  102.176357] [UFW BLOCK INPUT]: IN=ath0 OUT= MAC=00:1b:11:bb:ed:73:00:60:64:16:f4:ab:08:00:45:40:01:50:00:00:40:00:40:11:b6:09:c0:a8:01:01:c0:a8:01:02:08:00:c0:fd:01:3c:2e:c8:7d:bf:81:80:00:01:00:05:00:07:00:05:03:77:77:77:06:67:6f:6f:67:6c:65:03:63:6f:6d:00:00:01:00:01:c0:0c:00:05:00:01:00:09:37:bd:00:08:03:77 SRC=192.168.1.1 DST=192.168.1.2 LEN=336 TOS=0x00 PREC=0x40 TTL=64 ID=0 DF PROTO=UDP SPT=2048 DPT=49405 LEN=316 
Nov  9 21:33:59 linux23dragon-desktop kernel: [  107.649785] [UFW BLOCK INPUT]: IN=ath0 OUT= MAC=00:1b:11:bb:ed:73:00:60:64:16:f4:ab:08:00:45:40:01:6f:00:00:40:00:40:11:b5:ea:c0:a8:01:01:c0:a8:01:02:08:00:e4:c5:01:5b:f3:c8:b0:2d:81:80:00:01:00:06:00:07:00:05:03:77:77:77:06:67:6f:6f:67:6c:65:03:63:6f:6d:02:61:75:00:00:01:00:01:c0:0c:00:05:00:01:00:05:32:6c:00 SRC=192.168.1.1 DST=192.168.1.2 LEN=367 TOS=0x00 PREC=0x40 TTL=64 ID=0 DF PROTO=UDP SPT=2048 DPT=58565 LEN=347 
Nov  9 21:34:07 linux23dragon-desktop kernel: [  114.846183] type=1503 audit(1226228647.136:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6250/net/" pid=6250 profile="/usr/sbin/cupsd"
Nov  9 21:34:08 linux23dragon-desktop kernel: [  115.877485] type=1503 audit(1226228648.169:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6254/net/" pid=6254 profile="/usr/sbin/cupsd"
Nov  9 21:34:08 linux23dragon-desktop kernel: [  115.879122] type=1503 audit(1226228648.169:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6254 profile="/usr/sbin/cupsd"
Nov  9 21:34:08 linux23dragon-desktop kernel: [  115.880472] type=1503 audit(1226228648.169:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6254 profile="/usr/sbin/cupsd"
Nov  9 21:34:08 linux23dragon-desktop kernel: [  115.881831] type=1503 audit(1226228648.173:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6254 profile="/usr/sbin/cupsd"
Nov  9 21:34:08 linux23dragon-desktop kernel: [  115.883119] type=1503 audit(1226228648.173:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6254 profile="/usr/sbin/cupsd"
Nov  9 21:34:08 linux23dragon-desktop kernel: [  115.884414] type=1503 audit(1226228648.173:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6254 profile="/usr/sbin/cupsd"
Nov  9 21:34:08 linux23dragon-desktop kernel: [  115.885740] type=1503 audit(1226228648.177:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6254 profile="/usr/sbin/cupsd"
Nov  9 21:34:08 linux23dragon-desktop kernel: [  115.887041] type=1503 audit(1226228648.177:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6254 profile="/usr/sbin/cupsd"
Nov  9 21:34:08 linux23dragon-desktop kernel: [  115.888334] type=1503 audit(1226228648.177:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6254 profile="/usr/sbin/cupsd"
Nov  9 21:34:09 linux23dragon-desktop kernel: [  116.720172] [UFW BLOCK INPUT]: IN=ath0 OUT= MAC=00:1b:11:bb:ed:73:00:60:64:16:f4:ab:08:00:45:40:00:c1:00:00:40:00:40:11:b6:98:c0:a8:01:01:c0:a8:01:02:08:00:82:ec:00:ad:b5:ec:76:e5:81:80:00:01:00:01:00:03:00:03:0c:75:62:75:6e:74:75:66:6f:72:75:6d:73:03:6f:72:67:00:00:01:00:01:c0:0c:00:01:00:01:00:00:00:8c:00:04 SRC=192.168.1.1 DST=192.168.1.2 LEN=193 TOS=0x00 PREC=0x40 TTL=64 ID=0 DF PROTO=UDP SPT=2048 DPT=33516 LEN=173 
Nov  9 21:34:55 linux23dragon-desktop kernel: [  162.743920] [UFW BLOCK INPUT]: IN=ath0 OUT= MAC=00:1b:11:bb:ed:73:00:60:64:16:f4:ab:08:00:45:40:00:3c:24:79:40:00:40:06:92:af:c0:a8:01:01:c0:a8:01:02:08:02:27:0b:9b:49:d6:71:00:00:00:00:a0:02:16:d0:1b:12:00:00:02:04:05:b4:04:02:08:0a:00:00:f2:08:00:00:00:00:01:03:03:00:21:ba:d2:b5:90:fa:60:3a:00:00:00:00:00:00 SRC=192.168.1.1 DST=192.168.1.2 LEN=60 TOS=0x00 PREC=0x40 TTL=64 ID=9337 DF PROTO=TCP SPT=2050 DPT=9995 WINDOW=5840 RES=0x00 SYN URGP=0 
Nov  9 21:34:58 linux23dragon-desktop kernel: [  165.742293] [UFW BLOCK INPUT]: IN=ath0 OUT= MAC=00:1b:11:bb:ed:73:00:60:64:16:f4:ab:08:00:45:40:00:3c:24:7a:40:00:40:06:92:ae:c0:a8:01:01:c0:a8:01:02:08:02:27:0b:9b:49:d6:71:00:00:00:00:a0:02:16:d0:19:e6:00:00:02:04:05:b4:04:02:08:0a:00:00:f3:34:00:00:00:00:01:03:03:00:e2:d4:e7:af:cb:d2:4d:33:00:00:00:00:00:00 SRC=192.168.1.1 DST=192.168.1.2 LEN=60 TOS=0x00 PREC=0x40 TTL=64 ID=9338 DF PROTO=TCP SPT=2050 DPT=9995 WINDOW=5840 RES=0x00 SYN URGP=0 
Nov  9 21:35:04 linux23dragon-desktop kernel: [  171.740454] [UFW BLOCK INPUT]: IN=ath0 OUT= MAC=00:1b:11:bb:ed:73:00:60:64:16:f4:ab:08:00:45:40:00:3c:24:7b:40:00:40:06:92:ad:c0:a8:01:01:c0:a8:01:02:08:02:27:0b:9b:49:d6:71:00:00:00:00:a0:02:16:d0:17:8e:00:00:02:04:05:b4:04:02:08:0a:00:00:f5:8c:00:00:00:00:01:03:03:00:24:3a:79:5c:e1:8f:c6:e6:00:00:00:00:00:00 SRC=192.168.1.1 DST=192.168.1.2 LEN=60 TOS=0x00 PREC=0x40 TTL=64 ID=9339 DF PROTO=TCP SPT=2050 DPT=9995 WINDOW=5840 RES=0x00 SYN URGP=0 
Nov  9 21:35:16 linux23dragon-desktop kernel: [  183.741074] [UFW BLOCK INPUT]: IN=ath0 OUT= MAC=00:1b:11:bb:ed:73:00:60:64:16:f4:ab:08:00:45:40:00:3c:24:7c:40:00:40:06:92:ac:c0:a8:01:01:c0:a8:01:02:08:02:27:0b:9b:49:d6:71:00:00:00:00:a0:02:16:d0:12:de:00:00:02:04:05:b4:04:02:08:0a:00:00:fa:3c:00:00:00:00:01:03:03:00:53:f3:df:68:9a:e9:10:bc:32:37:39:38:39:22 SRC=192.168.1.1 DST=192.168.1.2 LEN=60 TOS=0x00 PREC=0x40 TTL=64 ID=9340 DF PROTO=TCP SPT=2050 DPT=9995 WINDOW=5840 RES=0x00 SYN URGP=0 
Nov  9 21:35:18 linux23dragon-desktop kernel: [  185.946303] [UFW BLOCK INPUT]: IN=ath0 OUT= MAC=00:1b:11:bb:ed:73:00:60:64:16:f4:ab:08:00:45:40:01:65:00:00:40:00:40:11:b5:f4:c0:a8:01:01:c0:a8:01:02:08:00:c4:e7:01:51:fd:ac:2e:d2:81:80:00:01:00:05:00:07:00:05:0c:73:61:66:65:62:72:6f:77:73:69:6e:67:07:63:6c:69:65:6e:74:73:06:67:6f:6f:67:6c:65:03:63:6f:6d:00:00 SRC=192.168.1.1 DST=192.168.1.2 LEN=357 TOS=0x00 PREC=0x40 TTL=64 ID=0 DF PROTO=UDP SPT=2048 DPT=50407 LEN=337 
Nov  9 21:35:40 linux23dragon-desktop kernel: [  207.742261] [UFW BLOCK INPUT]: IN=ath0 OUT= MAC=00:1b:11:bb:ed:73:00:60:64:16:f4:ab:08:00:45:40:00:3c:24:7d:40:00:40:06:92:ab:c0:a8:01:01:c0:a8:01:02:08:02:27:0b:9b:49:d6:71:00:00:00:00:a0:02:16:d0:09:7e:00:00:02:04:05:b4:04:02:08:0a:00:01:03:9c:00:00:00:00:01:03:03:00:94:af:cc:65:73:74:d7:08:e7:fa:04:00:00:00 SRC=192.168.1.1 DST=192.168.1.2 LEN=60 TOS=0x00 PREC=0x40 TTL=64 ID=9341 DF PROTO=TCP SPT=2050 DPT=9995 WINDOW=5840 RES=0x00 SYN URGP=0[/I][/B]

---

### Post by Yezinki on 2008-11-09
KING the issue is the built in cam........

See the results when I attached Logitech quick cam Pro 9000.

2 cams running simultaneously one with Ekiga & other with aMSN.

aMSN isn't picking up the built in cam???

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-09
TCP/UDP......isnt the issue.....the issue is that aMSN does not support the built in cam.........why **[FONT="Arial"][SIZE="5"][COLOR="Red"]KING LINUX[/COLOR][/SIZE][/FONT]**????

---

### Post by linux23dragon on 2008-11-09
> **Yezinki said:**
> why KING??

I suspect that the driver is too new and does not support all of the webcams features yet.

In time the developers will implement all the features.  I doubt that the developers know that the driver works at all for this webcam model currently.

---

### Post by linux23dragon on 2008-11-09
> **linux23dragon said:**
> This version of menu.lst can be used for duel booting windows and Linux.
```

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
***default 3***

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
***timeout 15***

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
***#hiddenmenu***

# Pretty colours
***color green/black light-green/black***

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=cd3e4739-4ca0-422c-ad5a-6d7d45d769ac ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cd3e4739-4ca0-422c-ad5a-6d7d45d769ac

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash quiet

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-7-generic
uuid cd3e4739-4ca0-422c-ad5a-6d7d45d769ac
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=cd3e4739-4ca0-422c-ad5a-6d7d45d769ac ro splash quiet
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid cd3e4739-4ca0-422c-ad5a-6d7d45d769ac
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=cd3e4739-4ca0-422c-ad5a-6d7d45d769ac ro single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
uuid cd3e4739-4ca0-422c-ad5a-6d7d45d769ac
kernel /boot/memtest86+.bin
quiet
[I][B]
title Windows 95/98/NT/2000
root (hd0,0)
makeactive
chainloader +1[/B][/I]


### END DEBIAN AUTOMAGIC KERNELS LIST

```

However, the default OS that will be booting will be Windows (after 15 seconds).  You can change any of the default settings as you like.

Edit: Creating the file is the first step

OK you only need to use the above code to modify your menu.lst file.  I have Bold and Italic the lines to show you what is needed to be modified  

To edit the menu.lst file we going to use gedit.  we will back up the old menu.lst.

```
[B][I]sudo cp -a /boot/grub/menu.lst /boot/grub/menu.lst-backup &&
gksudo gedit /boot/grub/menu.lst[/I][/B]
```

After editing the menu.lst file, save and exit gedit.

---

### Post by linux23dragon on 2008-11-09
I have found a good VirtualBox support page for Ubuntu-8.04.  I suspect it will work ok for Ubuntu-8.10.

**EDIT**. I was wrong.  It appears there is no kernel support for 8.10 as yet. I just tried it out 

**EDIT 2 ** Found one on the virtualbox [***[COLOR="Blue"]wiki site[/COLOR]***]("http://www.virtualbox.org/wiki/Linux_Downloads")

It will get most if not all your devices (USB, soundcard and network) running in Vista.   

I have not used it myself yet, just a brief look at what is configured.

EDIT:- I have noticed that they do mention about Dependency problems and how to fix them.  They use a different kernel version ***virtualbox-ose-modules-2.6.22-14-generic***, that is used in Ubuntu-8.04.  That might be resolved in Ubuntu-8.10.  



Is your laptop 64bit and runs a 64bit version of Ubuntu-8.10?

---

### Post by Yezinki on 2008-11-09
Hello**[FONT="Arial"][SIZE="5"][COLOR="Red"] KING LINUX,[/COLOR][/SIZE][/FONT]**

How do you see this partition startergy for a  single OS suggested by a IT friend:

1. /boot ext 140 MB. Primary.

2. /usr XFS 12 GB.  Primary.

3. /var XFS 20 GB. Primary.

4. /home XFS 130 GB....Logical> Extended

5. /opt XFS 20 GB.

6. /root XFS 20 GB

7./tmp 5 GB.

8. /swap.......

As per him if I have the need to reinstall, shall have to format ALL except /home & /opt??

Any clues why  the built in cam wont work with aMSN....nothing to do with ports as you saw quick cam pro 9000 works so spontaneously?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-09
Do you use 32 bit or 64 bit Ubuntu....if yes where from did you down load it?

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-09
> **Yezinki said:**
> Hello**[FONT="Arial"][SIZE="5"][COLOR="Red"] KING LINUX,[/COLOR][/SIZE][/FONT]**

How do you see this partition startergy for a  single OS suggested by a IT friend:

1. /boot ext 140 MB. Primary.

2. /usr XFS 12 GB.  Primary.

3. /var XFS 20 GB. Primary.

4. /home XFS 130 GB....Logical> Extended

5. /opt XFS 20 GB.

6. /root XFS 20 GB

7./tmp 5 GB.

8. /swap.......


lol,  That's sort of how I partitioned my own LFS system (back in the old learning days), but some of the partition sizes are ether too small or too large in size.

Some things to note based from experience.

1. /root is not the same as / because /root is the directory that resides in /  

2. /tmp size (5GB) is too small in size.  Its OK when you don't need to record DVD's.  

3. /boot can use the better ext3 file system.  But the partition size is ok.

4. I have never seen Ubuntu or any other Linux distribution use the /opt.  It is very handy to have if your building your own LFS system, since you have control of the application prefix.

I normally build and install KDE, Gnome, X  server and other desktops in the /opt directory.  So the size of 20GB for /opt is reasonable.

 
5. The other partitions are reasonable as well if you were to build
 your own system.  The partition numbering seem to be just numbers of partitions I take it?



[QUOTE=Yezinki]
As per him if I have the need to reinstall, shall have to format ALL except /home & /opt??
[/quote]

Correct, if you have the need to save files in /opt

[QUOTE=Yezinki]
Any clues why  the built in cam wont work with aMSN....nothing to do with ports as you saw quick cam pro 9000 works so spontaneously?
[/quote]


I suspect it is to do with both the driver and aMSN.   The driver is really new and is not been tested with many applications.  If you started amsn in the terminal you will see other log information that will possibly give you hints on what's happening between them.  I'd also look at system and kernel logs as well.

If I had your notebook I an tell you more about what is happening.  Of course I can ask for the loging information as well.  Thats is if you want to go that far into detail.

Hope that helps

---

### Post by linux23dragon on 2008-11-09
> **Yezinki said:**
> Do you use 32 bit or 64 bit Ubuntu....if yes where from did you down load it?

Regards,

Yezinki.

I have a 64bit Intel core2 duo CPU, which runs 64bit Ubuntu well.
[URL="http://mirror.internode.on.net/pub/ubuntu/releases/intrepid/ubuntu-8.10-desktop-amd64.iso"]
***_[COLOR="Blue"]Download link for Ubuntu-8.10 64bit[/COLOR]_***[/URL]

---

### Post by linux23dragon on 2008-11-09
> **Yezinki said:**
> Hello**[FONT="Arial"][SIZE="5"][COLOR="Red"] KING LINUX,[/COLOR][/SIZE][/FONT]**

How do you see this partition startergy for a  single OS suggested by a IT friend:

1. /boot ext 140 MB. Primary.

2. /usr XFS 12 GB.  Primary.

3. /var XFS 20 GB. Primary.

4. /home XFS 130 GB....Logical> Extended

5. /opt XFS 20 GB.

6. /root XFS 20 GB

7./tmp 5 GB.

8. /swap.......


lol,  That's sort of how I partitioned my own LFS system (back in the old learning days), but some of the partition sizes are ether too small or too large in size.

Some things to note based from experience.

1. /root is not the same as / because /root is the directory that resides in /  

2. /tmp size (5GB) is too small in size.  Its OK when you don't need to record DVD's.  

3. /boot can use the better ext3 file system.  But the partition size is ok.

4. I have never seen Ubuntu or any other Linux distribution use the /opt.  It is very handy to have if your building your own LFS system, since you have control of the application prefix.

I normally build and install KDE, Gnome, X  server and other desktops in the /opt directory.  So the size of 20GB for /opt is reasonable.

 
5. The other partitions are reasonable as well if you were to build
 your own system.  The partition numbering seem to be just numbers of partitions I take it?



[QUOTE=Yezinki]
As per him if I have the need to reinstall, shall have to format ALL except /home & /opt??
[/quote]

Correct, if you have the need to save files in /opt

[QUOTE=Yezinki]
Any clues why  the built in cam wont work with aMSN....nothing to do with ports as you saw quick cam pro 9000 works so spontaneously?
[/quote]


I suspect it is to do with both the driver and aMSN.   The driver is really new and is not been tested with many applications.  If you started amsn in the terminal you will see other log information that will possibly give you hints on what's happening between them.  I'd also look at system and kernel logs as well.

If I had your notebook I an tell you more about what is happening.  Of course I can ask for the loging information as well.  Thats is if you want to go that far into detail.

Hope that helps

---

### Post by Yezinki on 2008-11-10
Hi **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUX KING![/COLOR][/SIZE][/FONT]**

1. I have total faith in yours expertise only. ;)

2. Yes the partitioning Nos are just the no of paritions.

3. What is your FINAL plan for a single OS on this Sony 232 GB HD with Ubuntu only?

4. Since he use Red Hat Server.....could not find LV volumes in Ubuntu....what's that?

5. He feels I should have /opt too??

6. what exactly do you mean by this " If I had your notebook I an tell you more about what is happening. Of course I can ask for the loging information as well. Thats is if you want to go that far into detail."

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-10
Oh I dont have a 64 bit CPU so wont run well on a 32 bit CPU?

---

### Post by Yezinki on 2008-11-10
**[FONT="Arial"][SIZE="5"][COLOR="Red"]linux23dragon KING LINUX is No 1[/COLOR][/SIZE][/FONT]**

Your Avatar is super too............

---

### Post by Yezinki on 2008-11-10
[B]```
If I had your notebook I an tell you more about what is happening. Of course I can ask for the loging information as well. Thats is if you want to go that far into detail.

```[/B]

Go ahead what do you need??

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-10
> **Yezinki said:**
> Oh I dont have a 64 bit CPU so wont run well on a 32 bit CPU?

Correct.  64bit Ubuntu won't work with a 32bit CPU

---

### Post by linux23dragon on 2008-11-10
[QUOTE=Yezinki] What is your FINAL plan for a single OS on this Sony 232 GB HD with Ubuntu only?[/quote]

I'll write that up when I get home from work later on today.

[QUOTE=Yezinki] 
4. Since he use Red Hat Server.....could not find LV volumes in Ubuntu....what's that?[/quote]

LV is [***_[COLOR="Blue"] Logical Volume[/COLOR]_***]("http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux)")

[QUOTE=Yezinki]
5. He feels I should have /opt too??
[/quote]

Why?  It won't get used with Ubuntu.  Ask him how he uses it.

Remember, your running a desktop.

[QUOTE=Yezinki]
6. what exactly do you mean by this " If I had your notebook I an tell you more about what is happening. Of course I can ask for the loging information as well. Thats is if you want to go that far into detail."
[/QUOTE]

Just letting you know that we have a way to confirm what I suspect about the web cam operation.

---

### Post by linux23dragon on 2008-11-10
> **Yezinki said:**
> [B]```
If I had your notebook I an tell you more about what is happening. Of course I can ask for the loging information as well. Thats is if you want to go that far into detail.

```[/B]

Go ahead what do you need??

Regards,

Yezinki.


I'll write up a procedure for you when I get home

---

### Post by Yezinki on 2008-11-10
Thanks LINUX KING!

what do you need to confirm web cam about web cam operation....go ahead.

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-10
KING cant you take remote access of my machine????????

---

### Post by linux23dragon on 2008-11-10
> **Yezinki said:**
> KING cant you take remote access of my machine????????

lol, That's an idea.  I have never tried it before.  I'll see how to go about it when I get home.

---

### Post by Yezinki on 2008-11-10
That would be great...........I have total faith in your abilities LINUX KING!!

---

### Post by Yezinki on 2008-11-10
There is always a first time to every thing........lol.

---

### Post by linux23dragon on 2008-11-10
> **Yezinki said:**
> 
3. What is your FINAL plan for a single OS on this Sony 232 GB HD with Ubuntu only?


This is the Ubuntu only (single OS) file system setup.

```
[B]
sda1  /boot  ext3  200MB          |
sda2  /usr   XFS   20GB           | <-- Primary Partitions 
sda3  /var   XFS   5GB            |
sda4  ->*Extension Partition*<-
sda5  /      XFS   1GB           ||      
sda6  /tmp   XFS   13GB          || <-- Logical drives
sda7  /SWAP  N/A   512MB         ||
sda8  /home  XFS   192GB         ||
[/B]
```

---

### Post by Yezinki on 2008-11-10
Thanks**[FONT="Arial"][SIZE="5"][COLOR="Red"] LINUX KING[/COLOR][/SIZE][/FONT]** for taking the time out to make a final plan.

Wanna try remote access?

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-10
> **Yezinki said:**
> Thanks**[FONT="Arial"][SIZE="5"][COLOR="Red"] LINUX KING[/COLOR][/SIZE][/FONT]** for taking the time out to make a final plan.

Wanna try remote access?

Regards,

Yezinki.


Well ok.  But I have never done it via the internet before.  I have been looking up for some info.  Not easy, but then again I have not tryed it out as is yet.

Do you know how yourself?

---

### Post by Yezinki on 2008-11-10
LINUX KING,

I have no idea either......just know about it because at times Dell support used to take remote access of my laptop using a software citrix I think...

Regards,

Yezinki

---

### Post by Yezinki on 2008-11-10
other option is to ask me what you want to do.......commands........i shall keep sending you their outputs??

---

### Post by linux23dragon on 2008-11-10
> **Yezinki said:**
> other option is to ask me what you want to do.......commands........i shall keep sending you their outputs??

That will be better I think.  It appears that you need to adjust your login manager (see attached. *Note:- not correctly configured for remote access*.) 


Using the console method is easer.

Open up the terminal and type *amsn* 

Then just observe any out put in that terminal.  Hopefully you will see something get written out if something goes wrong.

---

### Post by Yezinki on 2008-11-10
[B]ubuntu@ubuntu-laptop:~$ amsn 
Playing WAVE '/usr/share/amsn/skins/default/sounds/newemail.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo


[/B]

---

### Post by Yezinki on 2008-11-10
Here what do I need to correct?

---

### Post by linux23dragon on 2008-11-10
> **Yezinki said:**
> [B]ubuntu@ubuntu-laptop:~$ amsn 
Playing WAVE '/usr/share/amsn/skins/default/sounds/newemail.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo


[/B]

Cool, that's a good message.  

I'll google around a bit and see what I can find about the webcam issue.
This will hopefully confirm  what I suspect.

---

### Post by Yezinki on 2008-11-10
Saw this error when trying to start aMSN??

---

### Post by linux23dragon on 2008-11-10
> **Yezinki said:**
> Here what do I need to correct?

Correct.  But I still need to learn a bit about it.

Have a look at [[COLOR="Blue"]***_this_***[/COLOR]]("https://help.ubuntu.com/community/VNC")

---

### Post by linux23dragon on 2008-11-10
> **Yezinki said:**
> Saw this error when trying to start aMSN??

Is that the aMSN that was compiled on your PC (Built against tlc/tk8.4)?

---

### Post by Yezinki on 2008-11-10
Yes.

---

### Post by linux23dragon on 2008-11-10
> **Yezinki said:**
> Yes.

We did seem to have better luck with the pre-built aMSN (Built against tcl/tk8.5 libs)

Perhaps we could build amsn against tcl/tk8.5 libs or just see if we can adjust the brightness of the Ubuntu version of amsn.

It does seem to be a brightness control issue.

---

### Post by linux23dragon on 2008-11-10
> **linux23dragon said:**
> We did seem to have better luck with the pre-built aMSN (Built against tcl/tk8.5 libs)

Perhaps we could build amsn against tcl/tk8.5 libs or just see if we can adjust the brightness of the Ubuntu version of amsn.

It does seem to be a brightness control issue.

I tried to build amsn against tcl/tk8.5 with no luck.  So the best thing to do is use the Ubuntu version.

```

sudo apt-get purge amsn tcl8.4 tcl8.4-dev tk8.4 tk8.4-dev &&
sudo apt-get install amsn tcl8.5 tk8.5
```

---

### Post by linux23dragon on 2008-11-10
The developers have updated the webcam drivers.  You can try them out if you like :)

---

### Post by linux23dragon on 2008-11-10
I have written to the developers in regards to your webcam operation and amsn.

---

### Post by Yezinki on 2008-11-10
> **Yezinki said:**
> Saw this error when trying to start aMSN??


Still same error even after running the new code.........aMSN now wont even run??

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-10
**[PHP]I tried to build amsn against tcl/tk8.5 with no luck. So the best thing to do is use the Ubuntu version.[/PHP]**

Whats the Ubuntu version & where can it be downloaded from?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-10
Do I need to completely  unintsall the previous aMSN version if yes than how?

---

### Post by Yezinki on 2008-11-10
> **linux23dragon said:**
> This is the Ubuntu only (single OS) file system setup.

```
[B]
sda1  /boot  ext3  200MB          |
sda2  /usr   XFS   20GB           | <-- Primary Partitions 
sda3  /var   XFS   5GB            |
sda4  ->*Extension Partition*<-
sda5  /      XFS   1GB           ||      
sda6  /tmp   XFS   13GB          || <-- Logical drives
sda7  /SWAP  N/A   512MB         ||
sda8  /home  XFS   192GB         ||
[/B]
```


Hi **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUX KING![/COLOR][/SIZE][/FONT]**

Sorry to have bothered you again.

1. I would like you to have relook at the dual boot plan you made earlier & post it, for this 232 GB HD.

2. The reason being that the Sony OEM DVD deletes all partitions.

3. I shall install XP MCE first on HD Primary C NTFS.

4. Than use Acronis Disk director to partition it into a Primary C & Logical D NTFS.

5. SD/MMC will be named E & optical as F.

6. Than install Ubuntu according to your plan.

7. Dont know what drive letters shall be after that....I mean sda's?

8. Kindly post the edited grub menu lst too.

The reason being Cam drivers issues & the PCI TV tuner card & its infra red device which picks up signals from the remote if the need to watch TV.

PC tech shall come & shall post the details/pics of the card to replace.

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-10
> **linux23dragon said:**
> This version of menu.lst can be used for duel booting windows and Linux.
```

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color green/black light-green/black

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=cd3e4739-4ca0-422c-ad5a-6d7d45d769ac ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cd3e4739-4ca0-422c-ad5a-6d7d45d769ac

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash quiet

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-7-generic
uuid cd3e4739-4ca0-422c-ad5a-6d7d45d769ac
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=cd3e4739-4ca0-422c-ad5a-6d7d45d769ac ro splash quiet
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid cd3e4739-4ca0-422c-ad5a-6d7d45d769ac
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=cd3e4739-4ca0-422c-ad5a-6d7d45d769ac ro single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
uuid cd3e4739-4ca0-422c-ad5a-6d7d45d769ac
kernel /boot/memtest86+.bin
quiet

title Windows 95/98/NT/2000
root (hd0,0)
makeactive
chainloader +1


### END DEBIAN AUTOMAGIC KERNELS LIST

```

However, the default OS that will be booting will be Windows (after 15 seconds).  You can change any of the default settings as you like.

Edit: Creating the file is the first step


Is this the Final edited grub menu lst for a dual boot??

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-10
[B]```
This is how you can partition your hard drive for your own Desktop PC if you also need Xp/Vista installed (duel boot system), using Ubuntu installation disk to partition the drive.

ext3 and XFS are file systems I use in the following partitions:-

sda1 C:/ NTFS ~50GB to 100GB <-- Windows formatted
sda2 D:/ NTFS ~50GB to 100GB <-- Windows formatted (for windows backup image) Must be equal size to C:/ drive
sda3 /boot ext3 200MB
sda4 ->logical drive<-
sda5 / XFS 1GB <- root partition
sda6 /usr XFS 20GB
sda7 /var XFS 5GB
sda8 /tmp XFS 13GB
sda9 SWAP 512MB <- swap space
sda10 /home XFS The Partition size? As big as you can for /home.

Master boot record must be installed on sda (or sda0)


Note :- During the partitioning setup (With Ubuntu). The root partition will give you a false error report about its size (during the installation setup stage). This error message can be ignored, as it is assumes that you have all the other directory s within that same partition. Which is not the case in this example.
```[/B]

1.Is this the final plan for a dual boot XP/Ubuntu on 232 GB HD?

2. sda numbering might change?

3. When do I edit the grub menu lst?

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-10
> **Yezinki said:**
> Is this the Final edited grub menu lst for a dual boot??

Regards,

Yezinki.


It is for the current installation you have.  But if you repartition your hard drive, the uuid numbers may be different.

Post the new menu.lst file after you reinstall Ubuntu and I'll show you the final edit for your new installation.

---

### Post by linux23dragon on 2008-11-10
> **Yezinki said:**
> Still same error even after running the new code.........aMSN now wont even run??

Regards,

Yezinki.

Can you reinstall aMSN using synaptic package manager please?

Please Make sure ***amsn-data*** is installed.

---

### Post by linux23dragon on 2008-11-10
> **Yezinki said:**
> **[PHP]I tried to build amsn against tcl/tk8.5 with no luck. So the best thing to do is use the Ubuntu version.[/PHP]**

Whats the Ubuntu version & where can it be downloaded from?

Regards,

Yezinki.

The current ubuntu version is:-

***amsn 0.97.2~debian-0ubuntu3***

---

### Post by linux23dragon on 2008-11-10
> **Yezinki said:**
> Do I need to completely  unintsall the previous aMSN version if yes than how?


This should remove the version of amsn you built yourself on your system:-
```

sudo apt-get purge amsn tcl8.4 tcl8.4-dev tk8.4 tk8.4-dev

```

---

### Post by linux23dragon on 2008-11-10
> **Yezinki said:**
> 
1. I would like you to have relook at the dual boot plan you made earlier & post it, for this 232 GB HD.

I'm currently at work again lol. I'll post it in 8 or 9 hours from now.

> **Yezinki said:**
> 
2. The reason being that the Sony OEM DVD deletes all partitions.


This is not good, but I suspect it is typical for an OEM version of XP.  

The OEM version of Windows XP does not seem to be flexible at all.  Do you have a copy of corporate edition of Windows XP?


> **Yezinki said:**
> 
3. I shall install XP MCE first on HD Primary C NTFS.

Yes.  You do need to install windows first. I hope you can reduce the partition size. 

> **Yezinki said:**
> 
4. Than use Acronis Disk director to partition it into a Primary C & Logical D NTFS.

Its worth a try.

> **Yezinki said:**
> 
5. SD/MMC will be named E & optical as F.

I suspect that is how windows will lable them drives.  It should not effect Linux operations in regards. 


> **Yezinki said:**
> 
6. Than install Ubuntu according to your plan.

Yes.

> **Yezinki said:**
> 
7. Dont know what drive letters shall be after that....I mean sda's?

Windows should only take sda1.  As stated, I'll write up the partition tables for such an installation.


> **Yezinki said:**
> 
8. Kindly post the edited grub menu lst too.


It might be safer to re post the new menu.last file from the new Ubuntu installation.  As it will have different partition uuid's

 
> **Yezinki said:**
> 
PC tech shall come & shall post the details/pics of the card to replace.


Cool :)

---

### Post by Yezinki on 2008-11-10
[B]```
1. I would like you to have relook at the dual boot plan you made earlier & post it, for this 232 GB HD.

2. The reason being that the Sony OEM DVD deletes all partitions.

3. I shall install XP MCE first on HD Primary C NTFS.

4. Than use Acronis Disk director to partition it into a Primary C & Logical D NTFS.

5. SD/MMC will be named E & optical as F.

6. Than install Ubuntu according to your plan.

7. Dont know what drive letters shall be after that....I mean sda's?

8. Kindly post the edited grub menu lst too.

The reason being Cam drivers issues & the PCI TV tuner card & its infra red device which picks up signals from the remote if the need to watch TV.

```[/B]

I have tried this before with XP MCE & Ubuntu Hardy......don't recall what sdas were?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-10
[B]```

Quote:
Originally Posted by Yezinki View Post
4. Than use Acronis Disk director to partition it into a Primary C & Logical D NTFS.
Its worth a try.

Quote:
Originally Posted by Yezinki View Post
5. SD/MMC will be named E & optical as F.
I suspect that is how windows will lable them drives. It should not effect Linux operations in regards.


```[/B]

As stated have done it once before.

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-10
aMSN is their in the Synaptic but wont install.....displays error that a file is broken or corrupted .....try fixing it manually.

How do I install it  from the net?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-10
**[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUX KING[/COLOR][/SIZE][/FONT]** am confused at times whether to do a single or a dual boot:

The reasons for going for a dual boot are:

1. Cam driver.

2. SD/MMC card formatting & ability of windows to read its files.

3. Infra red USB TV TUNER Transceiver.

4. Access to watch TV on the machine.

Personally I prefer a single OS on a machine.....don't have the expertise nor the time for correcting errors etc of dual OSs.....lol

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> 
1. I would like you to have relook at the dual boot plan you made earlier & post it, for this 232 GB HD.



```

sda1    C:/      NTFS     60GB            |
sda2    D:/      NTFS     60GB            | <-- Primary partition
sda3    /boot    ext3     200MB           |
sda4    ->Extended Partition<-
sda5    /        XFS      1GB            ||
sda6    /usr     XFS      20GB           ||
sda7    /var     XFS      5GB            || <-- Logical drives
sda8    /tmp     XFS      13GB           ||
sda9    SWAP              512MB          ||
sda10   /home    XFS      72GB           ||

```

The Master Boot Record (MBR) must be installed on sda (or sda0)

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> [B]```
This is how you can partition your hard drive for your own Desktop PC if you also need Xp/Vista installed (duel boot system), using Ubuntu installation disk to partition the drive.

ext3 and XFS are file systems I use in the following partitions:-

sda1 C:/ NTFS ~50GB to 100GB <-- Windows formatted
sda2 D:/ NTFS ~50GB to 100GB <-- Windows formatted (for windows backup image) Must be equal size to C:/ drive
sda3 /boot ext3 200MB
sda4 ->logical drive<-
sda5 / XFS 1GB <- root partition
sda6 /usr XFS 20GB
sda7 /var XFS 5GB
sda8 /tmp XFS 13GB
sda9 SWAP 512MB <- swap space
sda10 /home XFS The Partition size? As big as you can for /home.

Master boot record must be installed on sda (or sda0)


Note :- During the partitioning setup (With Ubuntu). The root partition will give you a false error report about its size (during the installation setup stage). This error message can be ignored, as it is assumes that you have all the other directory s within that same partition. Which is not the case in this example.
```[/B]

1.Is this the final plan for a dual boot XP/Ubuntu on 232 GB HD?

The final dual boot method is written in this [**_*[COLOR="Blue"]post[/COLOR]*_**]("http://ubuntuforums.org/showpost.php?p=6150100&postcount=236")

> **Yezinki said:**
> 
2. sda numbering might change?


Yes, it will have a change of sda allocations if your meaning the difference between single boot and dual boot setups.    

> **Yezinki said:**
> 
3. When do I edit the grub menu lst?


First install windows and then install Ubuntu.  You then, edit the menu.lst file.

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> [B]```
1. I would like you to have relook at the dual boot plan you made earlier & post it, for this 232 GB HD.

2. The reason being that the Sony OEM DVD deletes all partitions.

3. I shall install XP MCE first on HD Primary C NTFS.

4. Than use Acronis Disk director to partition it into a Primary C & Logical D NTFS.

5. SD/MMC will be named E & optical as F.

6. Than install Ubuntu according to your plan.

7. Dont know what drive letters shall be after that....I mean sda's?

8. Kindly post the edited grub menu lst too.

The reason being Cam drivers issues & the PCI TV tuner card & its infra red device which picks up signals from the remote if the need to watch TV.

```[/B]

I have tried this before with XP MCE & Ubuntu Hardy......don't recall what sdas were?

Regards,

Yezinki.


It is a numbering system that is used by both the device manager and kernel.

Here is a PC with two SATA hard drives and one DVD ROM.  Each hard drive has two partitions each.  The DVD ROM  

***Note :- You can find all the device nodes in the /dev directory***

sda  = Serial Device (hard drive) Zerro
sda1 = Serial Device (hard drive) Zerro  (partiton one)
sda2 = Serial Device (Hard Drive) Zerro  (partition two)


Example two (if you have two hard drives in the same PC)

sdb  = Serial Device (hard drive) One
sdb1 = Serial Device (hard drive) One  (partiton one)
sda2 = Serial Device (hard drive) One  (partiton two)

Example three (this is an example of one DVD player in the same PC)

scd0 = dvd player/burner.
dvd = link to scd
sr0 = link to scd0

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> [B]```

Quote:
Originally Posted by Yezinki View Post
4. Than use Acronis Disk director to partition it into a Primary C & Logical D NTFS.
Its worth a try.

Quote:
Originally Posted by Yezinki View Post
5. SD/MMC will be named E & optical as F.
I suspect that is how windows will lable them drives. It should not effect Linux operations in regards.


```[/B]

As stated have done it once before.

Regards,

Yezinki.

Can you make both C: and D: drives as primary?

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> aMSN is their in the Synaptic but wont install.....displays error that a file is broken or corrupted .....try fixing it manually.

How do I install it  from the net?

Regards,

Yezinki.

That does not sound good.  

Normally you can use Synaptic Package manager to fix broken packages.

I've attached image that shows the location of such a filter in the package manger.   

Is there a window that outputs any information about the detailed error?

Normally the package manger will download amsn of the net for you, but it won't work until we fix this error.

---

### Post by Yezinki on 2008-11-11
Hi KING LINUX.

Just finished taking pics of the TV tuner.....let me transfer & post for your view..........had to open 50 screws of back panel ..you shall see for yourself how compact Sony has made this machine....I have the usb infra red transceiver plugged in too......what is the command for hard ware info?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-11
That does not sound good.

Normally you can use Synaptic Package manager to fix broken packages.

I've attached image that shows the location of such a filter in the package manger.

Is there a window that outputs any information about the detailed error?

Normally the package manger will download amsn of the net for you, but it won't work until we fix this error.
**```

```**

What command should I type?

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUX KING[/COLOR][/SIZE][/FONT]** am confused at times whether to do a single or a dual boot:

The reasons for going for a dual boot are:

1. Cam driver.

2. SD/MMC card formatting & ability of windows to read its files.

3. Infra red USB TV TUNER Transceiver.

4. Access to watch TV on the machine.

Personally I prefer a single OS on a machine.....don't have the expertise nor the time for correcting errors etc of dual OSs.....lol

Regards,

Yezinki.


In time you won't need to configure anything like were doing now.
But it must be worked out before we can have such a privilege.  Then say in six to twelve months time, it should be all automated.

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> Hi KING LINUX.
I have the usb infra red transceiver plugged in too......what is the command for hard ware info?


For PCI devices :-
```
lspci -v
```
For USB devices :-
```
lsusb -v
```

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> 

What command should I type?

I think you only need to type this command.
```
sudo apt-get -f check amsn
```

I myself have always used the GUI to fix broken packages, so I have no idea if the command also fixes the issue.

---

### Post by Yezinki on 2008-11-11
ubuntu@ubuntu-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dc300000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at dc380000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at dc3c0000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d8000000-d9ffffff
	Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d6000000-d7ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: da000000-dbffffff
	Prefetchable memory behind bridge: 00000000d4000000-00000000d5ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at dc5c4000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=0c, sec-latency=32
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: dc000000-dc2fffff
	Prefetchable memory behind bridge: 0000000088000000-000000008bffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 18d0 [size=8]
	I/O ports at 18c4 [size=4]
	I/O ports at 18c8 [size=8]
	I/O ports at 18c0 [size=4]
	I/O ports at 18b0 [size=16]
	Memory at dc5c4400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Subsystem: Sony Corporation Device 8205
	Flags: medium devsel, IRQ 10
	I/O ports at 18e0 [size=32]
	Kernel modules: i2c-i801

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, fast devsel, latency 0, IRQ 220
	Memory at d8000000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 2000 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device 0315
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at da000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb, wl

08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at dc216000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=08, secondary=09, subordinate=0c, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 8c000000-8ffff000
	I/O window 0: 00005400-000054ff
	I/O window 1: 00005800-000058ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at dc215000 (32-bit, non-prefetchable) [size=2K]
	Memory at dc210000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Sony Corporation Device 8205
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at dc214000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

08:05.0 Multimedia controller: Fujitsu Limited. Device 202a
	Subsystem: Sony Corporation Device 81fa
	Flags: medium devsel, IRQ 11
	I/O ports at 5000 [disabled] [size=256]
	Memory at dc000000 (32-bit, non-prefetchable) [disabled] [size=2M]
	Memory at dc200000 (32-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>

ubuntu@ubuntu-laptop:~$

---

### Post by Yezinki on 2008-11-11
bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               7
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0b00  2x 768 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       5
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               7
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0c00  2x 1024 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       6
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               7
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1380  3x 896 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       7
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               7
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 1024 bytes
        bInterval               1
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 003 Device 004: ID 054c:024b Sony Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x054c Sony Corp.
  idProduct          0x024b 
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              2 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode           33 US
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     210
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              2 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode           33 US
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     111
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 002: ID 0609:031d SMK Manufacturing, Inc. eHome Infrared Receiver
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        16
  idVendor           0x0609 SMK Manufacturing, Inc.
  idProduct          0x031d eHome Infrared Receiver
  bcdDevice            0.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               0
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
ubuntu@ubuntu-laptop:~$

---

### Post by Yezinki on 2008-11-11
ubuntu@ubuntu-laptop:~$ sudo apt-get -f check amsn
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu@ubuntu-laptop:~$

---

### Post by Yezinki on 2008-11-11
Synaptic screen shot!

---

### Post by linux23dragon on 2008-11-11
Well this is seems to be your infered device :-


```
Bus 001 Device 002: ID 0609:031d SMK Manufacturing, Inc. eHome Infrared Receiver
Device Descriptor:
bLength 18
bDescriptorType 1
bcdUSB 1.10
bDeviceClass 0 (Defined at Interface level)
bDeviceSubClass 0
bDeviceProtocol 0
bMaxPacketSize0 16
idVendor 0x0609 SMK Manufacturing, Inc.
idProduct 0x031d eHome Infrared Receiver
bcdDevice 0.00
iManufacturer 1
iProduct 2
iSerial 3
bNumConfigurations 1
Configuration Descriptor:
bLength 9
bDescriptorType 2
wTotalLength 32
bNumInterfaces 1
bConfigurationValue 1
iConfiguration 0
bmAttributes 0xa0
(Bus Powered)
Remote Wakeup
MaxPower 100mA
Interface Descriptor:
bLength 9
bDescriptorType 4
bInterfaceNumber 0
bAlternateSetting 0
bNumEndpoints 2
bInterfaceClass 255 Vendor Specific Class
bInterfaceSubClass 255 Vendor Specific Subclass
bInterfaceProtocol 255 Vendor Specific Protocol
iInterface 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x01 EP 1 OUT
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0010 1x 16 bytes
bInterval 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x81 EP 1 IN
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0010 1x 16 bytes
bInterval 0
cannot read device status, Operation not permitted (1)
```

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> Synaptic screen shot!

OK then try this as well :-

```
sudo apt-get -f check amsn-data
```

---

### Post by Yezinki on 2008-11-11
Pics are many & large shall take some time.......:(

---

### Post by Yezinki on 2008-11-11
ubuntu@ubuntu-laptop:~$ sudo apt-get -f check amsn-data
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu@ubuntu-laptop:~$

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> Pics are many & large shall take some time.......:(

That's cool :)

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> ubuntu@ubuntu-laptop:~$ sudo apt-get -f check amsn-data
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu@ubuntu-laptop:~$

Now try

```
sudo apt-get purge amsn amsn-data
```

---

### Post by Yezinki on 2008-11-11
What are your views about the seen pics??

---

### Post by Yezinki on 2008-11-11
Getting this what should I do........

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> What are your views about the seen pics??

It looks to be just the interface board.  I can't see the tuner chips on he board :(

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> Getting this what should I do........

You can say yes or no.  It depends if you like to stream video over to another PC.

---

### Post by Yezinki on 2008-11-11
Ok i see.......i said NO........

---

### Post by Yezinki on 2008-11-11
mknod: `video41-': Read-only file system
makedev video41 c 81 41 root video 0660: failed
rm: cannot remove `video41-': Read-only file system
rm: cannot remove `radio41-': Read-only file system
mknod: `radio41-': Read-only file system
makedev radio41 c 81 105 root video 0660: failed
rm: cannot remove `radio41-': Read-only file system
rm: cannot remove `video42-': Read-only file system
mknod: `video42-': Read-only file system
makedev video42 c 81 42 root video 0660: failed
rm: cannot remove `video42-': Read-only file system
rm: cannot remove `radio42-': Read-only file system
mknod: `radio42-': Read-only file system
makedev radio42 c 81 106 root video 0660: failed
rm: cannot remove `radio42-': Read-only file system
rm: cannot remove `video43-': Read-only file system
mknod: `video43-': Read-only file system
makedev video43 c 81 43 root video 0660: failed
rm: cannot remove `video43-': Read-only file system
rm: cannot remove `radio43-': Read-only file system
mknod: `radio43-': Read-only file system
makedev radio43 c 81 107 root video 0660: failed
rm: cannot remove `radio43-': Read-only file system
rm: cannot remove `video44-': Read-only file system
mknod: `video44-': Read-only file system
makedev video44 c 81 44 root video 0660: failed
rm: cannot remove `video44-': Read-only file system
rm: cannot remove `radio44-': Read-only file system
mknod: `radio44-': Read-only file system
makedev radio44 c 81 108 root video 0660: failed
rm: cannot remove `radio44-': Read-only file system
rm: cannot remove `video45-': Read-only file system
mknod: `video45-': Read-only file system
makedev video45 c 81 45 root video 0660: failed
rm: cannot remove `video45-': Read-only file system
rm: cannot remove `radio45-': Read-only file system
mknod: `radio45-': Read-only file system
makedev radio45 c 81 109 root video 0660: failed
rm: cannot remove `radio45-': Read-only file system
rm: cannot remove `video46-': Read-only file system
mknod: `video46-': Read-only file system
makedev video46 c 81 46 root video 0660: failed
rm: cannot remove `video46-': Read-only file system
rm: cannot remove `radio46-': Read-only file system
mknod: `radio46-': Read-only file system
makedev radio46 c 81 110 root video 0660: failed
rm: cannot remove `radio46-': Read-only file system
rm: cannot remove `video47-': Read-only file system
mknod: `video47-': Read-only file system
makedev video47 c 81 47 root video 0660: failed
rm: cannot remove `video47-': Read-only file system
rm: cannot remove `radio47-': Read-only file system
mknod: `radio47-': Read-only file system
makedev radio47 c 81 111 root video 0660: failed
rm: cannot remove `radio47-': Read-only file system
rm: cannot remove `video48-': Read-only file system
mknod: `video48-': Read-only file system
makedev video48 c 81 48 root video 0660: failed
rm: cannot remove `video48-': Read-only file system
rm: cannot remove `radio48-': Read-only file system
mknod: `radio48-': Read-only file system
makedev radio48 c 81 112 root video 0660: failed
rm: cannot remove `radio48-': Read-only file system
rm: cannot remove `video49-': Read-only file system
mknod: `video49-': Read-only file system
makedev video49 c 81 49 root video 0660: failed
rm: cannot remove `video49-': Read-only file system
rm: cannot remove `radio49-': Read-only file system
mknod: `radio49-': Read-only file system
makedev radio49 c 81 113 root video 0660: failed
rm: cannot remove `radio49-': Read-only file system
rm: cannot remove `video50-': Read-only file system
mknod: `video50-': Read-only file system
makedev video50 c 81 50 root video 0660: failed
rm: cannot remove `video50-': Read-only file system
rm: cannot remove `radio50-': Read-only file system
mknod: `radio50-': Read-only file system
makedev radio50 c 81 114 root video 0660: failed
rm: cannot remove `radio50-': Read-only file system
rm: cannot remove `video51-': Read-only file system
mknod: `video51-': Read-only file system
makedev video51 c 81 51 root video 0660: failed
rm: cannot remove `video51-': Read-only file system
rm: cannot remove `radio51-': Read-only file system
mknod: `radio51-': Read-only file system
makedev radio51 c 81 115 root video 0660: failed
rm: cannot remove `radio51-': Read-only file system
rm: cannot remove `video52-': Read-only file system
mknod: `video52-': Read-only file system
makedev video52 c 81 52 root video 0660: failed
rm: cannot remove `video52-': Read-only file system
rm: cannot remove `radio52-': Read-only file system
mknod: `radio52-': Read-only file system
makedev radio52 c 81 116 root video 0660: failed
rm: cannot remove `radio52-': Read-only file system
rm: cannot remove `video53-': Read-only file system
mknod: `video53-': Read-only file system
makedev video53 c 81 53 root video 0660: failed
rm: cannot remove `video53-': Read-only file system
rm: cannot remove `radio53-': Read-only file system
mknod: `radio53-': Read-only file system
makedev radio53 c 81 117 root video 0660: failed
rm: cannot remove `radio53-': Read-only file system
rm: cannot remove `video54-': Read-only file system
mknod: `video54-': Read-only file system
makedev video54 c 81 54 root video 0660: failed
rm: cannot remove `video54-': Read-only file system
rm: cannot remove `radio54-': Read-only file system
mknod: `radio54-': Read-only file system
makedev radio54 c 81 118 root video 0660: failed
rm: cannot remove `radio54-': Read-only file system
rm: cannot remove `video55-': Read-only file system
mknod: `video55-': Read-only file system
makedev video55 c 81 55 root video 0660: failed
rm: cannot remove `video55-': Read-only file system
rm: cannot remove `radio55-': Read-only file system
mknod: `radio55-': Read-only file system
makedev radio55 c 81 119 root video 0660: failed
rm: cannot remove `radio55-': Read-only file system
rm: cannot remove `video56-': Read-only file system
mknod: `video56-': Read-only file system
makedev video56 c 81 56 root video 0660: failed
rm: cannot remove `video56-': Read-only file system
rm: cannot remove `radio56-': Read-only file system
mknod: `radio56-': Read-only file system
makedev radio56 c 81 120 root video 0660: failed
rm: cannot remove `radio56-': Read-only file system
rm: cannot remove `video57-': Read-only file system
mknod: `video57-': Read-only file system
makedev video57 c 81 57 root video 0660: failed
rm: cannot remove `video57-': Read-only file system
rm: cannot remove `radio57-': Read-only file system
mknod: `radio57-': Read-only file system
makedev radio57 c 81 121 root video 0660: failed
rm: cannot remove `radio57-': Read-only file system
rm: cannot remove `video58-': Read-only file system
mknod: `video58-': Read-only file system
makedev video58 c 81 58 root video 0660: failed
rm: cannot remove `video58-': Read-only file system
rm: cannot remove `radio58-': Read-only file system
mknod: `radio58-': Read-only file system
makedev radio58 c 81 122 root video 0660: failed
rm: cannot remove `radio58-': Read-only file system
rm: cannot remove `video59-': Read-only file system
mknod: `video59-': Read-only file system
makedev video59 c 81 59 root video 0660: failed
rm: cannot remove `video59-': Read-only file system
rm: cannot remove `radio59-': Read-only file system
mknod: `radio59-': Read-only file system
makedev radio59 c 81 123 root video 0660: failed
rm: cannot remove `radio59-': Read-only file system
rm: cannot remove `video60-': Read-only file system
mknod: `video60-': Read-only file system
makedev video60 c 81 60 root video 0660: failed
rm: cannot remove `video60-': Read-only file system
rm: cannot remove `radio60-': Read-only file system
mknod: `radio60-': Read-only file system
makedev radio60 c 81 124 root video 0660: failed
rm: cannot remove `radio60-': Read-only file system
rm: cannot remove `video61-': Read-only file system
mknod: `video61-': Read-only file system
makedev video61 c 81 61 root video 0660: failed
rm: cannot remove `video61-': Read-only file system
rm: cannot remove `radio61-': Read-only file system
mknod: `radio61-': Read-only file system
makedev radio61 c 81 125 root video 0660: failed
rm: cannot remove `radio61-': Read-only file system
rm: cannot remove `video62-': Read-only file system
mknod: `video62-': Read-only file system
makedev video62 c 81 62 root video 0660: failed
rm: cannot remove `video62-': Read-only file system
rm: cannot remove `radio62-': Read-only file system
mknod: `radio62-': Read-only file system
makedev radio62 c 81 126 root video 0660: failed
rm: cannot remove `radio62-': Read-only file system
rm: cannot remove `video63-': Read-only file system
mknod: `video63-': Read-only file system
makedev video63 c 81 63 root video 0660: failed
rm: cannot remove `video63-': Read-only file system
rm: cannot remove `radio63-': Read-only file system
mknod: `radio63-': Read-only file system
makedev radio63 c 81 127 root video 0660: failed
rm: cannot remove `radio63-': Read-only file system
rm: cannot remove `radio': Read-only file system
rm: cannot remove `vtx0-': Read-only file system
mknod: `vtx0-': Read-only file system
makedev vtx0 c 81 192 root video 0660: failed
rm: cannot remove `vtx0-': Read-only file system
rm: cannot remove `vbi0-': Read-only file system
mknod: `vbi0-': Read-only file system
makedev vbi0 c 81 224 root video 0660: failed
rm: cannot remove `vbi0-': Read-only file system
rm: cannot remove `vtx1-': Read-only file system
mknod: `vtx1-': Read-only file system
makedev vtx1 c 81 193 root video 0660: failed
rm: cannot remove `vtx1-': Read-only file system
rm: cannot remove `vbi1-': Read-only file system
mknod: `vbi1-': Read-only file system
makedev vbi1 c 81 225 root video 0660: failed
rm: cannot remove `vbi1-': Read-only file system
rm: cannot remove `vtx2-': Read-only file system
mknod: `vtx2-': Read-only file system
makedev vtx2 c 81 194 root video 0660: failed
rm: cannot remove `vtx2-': Read-only file system
rm: cannot remove `vbi2-': Read-only file system
mknod: `vbi2-': Read-only file system
makedev vbi2 c 81 226 root video 0660: failed
rm: cannot remove `vbi2-': Read-only file system
rm: cannot remove `vtx3-': Read-only file system
mknod: `vtx3-': Read-only file system
makedev vtx3 c 81 195 root video 0660: failed
rm: cannot remove `vtx3-': Read-only file system
rm: cannot remove `vbi3-': Read-only file system
mknod: `vbi3-': Read-only file system
makedev vbi3 c 81 227 root video 0660: failed
rm: cannot remove `vbi3-': Read-only file system
rm: cannot remove `vtx4-': Read-only file system
mknod: `vtx4-': Read-only file system
makedev vtx4 c 81 196 root video 0660: failed
rm: cannot remove `vtx4-': Read-only file system
rm: cannot remove `vbi4-': Read-only file system
mknod: `vbi4-': Read-only file system
makedev vbi4 c 81 228 root video 0660: failed
rm: cannot remove `vbi4-': Read-only file system
rm: cannot remove `vtx5-': Read-only file system
mknod: `vtx5-': Read-only file system
makedev vtx5 c 81 197 root video 0660: failed
rm: cannot remove `vtx5-': Read-only file system
rm: cannot remove `vbi5-': Read-only file system
mknod: `vbi5-': Read-only file system
makedev vbi5 c 81 229 root video 0660: failed
rm: cannot remove `vbi5-': Read-only file system
rm: cannot remove `vtx6-': Read-only file system
mknod: `vtx6-': Read-only file system
makedev vtx6 c 81 198 root video 0660: failed
rm: cannot remove `vtx6-': Read-only file system
rm: cannot remove `vbi6-': Read-only file system
mknod: `vbi6-': Read-only file system
makedev vbi6 c 81 230 root video 0660: failed
rm: cannot remove `vbi6-': Read-only file system
rm: cannot remove `vtx7-': Read-only file system
mknod: `vtx7-': Read-only file system
makedev vtx7 c 81 199 root video 0660: failed
rm: cannot remove `vtx7-': Read-only file system
rm: cannot remove `vbi7-': Read-only file system
mknod: `vbi7-': Read-only file system
makedev vbi7 c 81 231 root video 0660: failed
rm: cannot remove `vbi7-': Read-only file system
rm: cannot remove `vtx8-': Read-only file system
mknod: `vtx8-': Read-only file system
makedev vtx8 c 81 200 root video 0660: failed
rm: cannot remove `vtx8-': Read-only file system
rm: cannot remove `vbi8-': Read-only file system
mknod: `vbi8-': Read-only file system
makedev vbi8 c 81 232 root video 0660: failed
rm: cannot remove `vbi8-': Read-only file system
rm: cannot remove `vtx9-': Read-only file system
mknod: `vtx9-': Read-only file system
makedev vtx9 c 81 201 root video 0660: failed
rm: cannot remove `vtx9-': Read-only file system
rm: cannot remove `vbi9-': Read-only file system
mknod: `vbi9-': Read-only file system
makedev vbi9 c 81 233 root video 0660: failed
rm: cannot remove `vbi9-': Read-only file system
rm: cannot remove `vtx10-': Read-only file system
mknod: `vtx10-': Read-only file system
makedev vtx10 c 81 202 root video 0660: failed
rm: cannot remove `vtx10-': Read-only file system
rm: cannot remove `vbi10-': Read-only file system
mknod: `vbi10-': Read-only file system
makedev vbi10 c 81 234 root video 0660: failed
rm: cannot remove `vbi10-': Read-only file system
rm: cannot remove `vtx11-': Read-only file system
mknod: `vtx11-': Read-only file system
makedev vtx11 c 81 203 root video 0660: failed
rm: cannot remove `vtx11-': Read-only file system
rm: cannot remove `vbi11-': Read-only file system
mknod: `vbi11-': Read-only file system
makedev vbi11 c 81 235 root video 0660: failed
rm: cannot remove `vbi11-': Read-only file system
rm: cannot remove `vtx12-': Read-only file system
mknod: `vtx12-': Read-only file system
makedev vtx12 c 81 204 root video 0660: failed
rm: cannot remove `vtx12-': Read-only file system
rm: cannot remove `vbi12-': Read-only file system
mknod: `vbi12-': Read-only file system
makedev vbi12 c 81 236 root video 0660: failed
rm: cannot remove `vbi12-': Read-only file system
rm: cannot remove `vtx13-': Read-only file system
mknod: `vtx13-': Read-only file system
makedev vtx13 c 81 205 root video 0660: failed
rm: cannot remove `vtx13-': Read-only file system
rm: cannot remove `vbi13-': Read-only file system
mknod: `vbi13-': Read-only file system
makedev vbi13 c 81 237 root video 0660: failed
rm: cannot remove `vbi13-': Read-only file system
rm: cannot remove `vtx14-': Read-only file system
mknod: `vtx14-': Read-only file system
makedev vtx14 c 81 206 root video 0660: failed
rm: cannot remove `vtx14-': Read-only file system
rm: cannot remove `vbi14-': Read-only file system
mknod: `vbi14-': Read-only file system
makedev vbi14 c 81 238 root video 0660: failed
rm: cannot remove `vbi14-': Read-only file system
rm: cannot remove `vtx15-': Read-only file system
mknod: `vtx15-': Read-only file system
makedev vtx15 c 81 207 root video 0660: failed
rm: cannot remove `vtx15-': Read-only file system
rm: cannot remove `vbi15-': Read-only file system
mknod: `vbi15-': Read-only file system
makedev vbi15 c 81 239 root video 0660: failed
rm: cannot remove `vbi15-': Read-only file system
rm: cannot remove `vtx16-': Read-only file system
mknod: `vtx16-': Read-only file system
makedev vtx16 c 81 208 root video 0660: failed
rm: cannot remove `vtx16-': Read-only file system
rm: cannot remove `vbi16-': Read-only file system
mknod: `vbi16-': Read-only file system
makedev vbi16 c 81 240 root video 0660: failed
rm: cannot remove `vbi16-': Read-only file system
rm: cannot remove `vtx17-': Read-only file system
mknod: `vtx17-': Read-only file system
makedev vtx17 c 81 209 root video 0660: failed
rm: cannot remove `vtx17-': Read-only file system
rm: cannot remove `vbi17-': Read-only file system
mknod: `vbi17-': Read-only file system
makedev vbi17 c 81 241 root video 0660: failed
rm: cannot remove `vbi17-': Read-only file system
rm: cannot remove `vtx18-': Read-only file system
mknod: `vtx18-': Read-only file system
makedev vtx18 c 81 210 root video 0660: failed
rm: cannot remove `vtx18-': Read-only file system
rm: cannot remove `vbi18-': Read-only file system
mknod: `vbi18-': Read-only file system
makedev vbi18 c 81 242 root video 0660: failed
rm: cannot remove `vbi18-': Read-only file system
rm: cannot remove `vtx19-': Read-only file system
mknod: `vtx19-': Read-only file system
makedev vtx19 c 81 211 root video 0660: failed
rm: cannot remove `vtx19-': Read-only file system
rm: cannot remove `vbi19-': Read-only file system
mknod: `vbi19-': Read-only file system
makedev vbi19 c 81 243 root video 0660: failed
rm: cannot remove `vbi19-': Read-only file system
rm: cannot remove `vtx20-': Read-only file system
mknod: `vtx20-': Read-only file system
makedev vtx20 c 81 212 root video 0660: failed
rm: cannot remove `vtx20-': Read-only file system
rm: cannot remove `vbi20-': Read-only file system
mknod: `vbi20-': Read-only file system
makedev vbi20 c 81 244 root video 0660: failed
rm: cannot remove `vbi20-': Read-only file system
rm: cannot remove `vtx21-': Read-only file system
mknod: `vtx21-': Read-only file system
makedev vtx21 c 81 213 root video 0660: failed
rm: cannot remove `vtx21-': Read-only file system
rm: cannot remove `vbi21-': Read-only file system
mknod: `vbi21-': Read-only file system
makedev vbi21 c 81 245 root video 0660: failed
rm: cannot remove `vbi21-': Read-only file system
rm: cannot remove `vtx22-': Read-only file system
mknod: `vtx22-': Read-only file system
makedev vtx22 c 81 214 root video 0660: failed
rm: cannot remove `vtx22-': Read-only file system
rm: cannot remove `vbi22-': Read-only file system
mknod: `vbi22-': Read-only file system
makedev vbi22 c 81 246 root video 0660: failed
rm: cannot remove `vbi22-': Read-only file system
rm: cannot remove `vtx23-': Read-only file system
mknod: `vtx23-': Read-only file system
makedev vtx23 c 81 215 root video 0660: failed
rm: cannot remove `vtx23-': Read-only file system
rm: cannot remove `vbi23-': Read-only file system
mknod: `vbi23-': Read-only file system
makedev vbi23 c 81 247 root video 0660: failed
rm: cannot remove `vbi23-': Read-only file system
rm: cannot remove `vtx24-': Read-only file system
mknod: `vtx24-': Read-only file system
makedev vtx24 c 81 216 root video 0660: failed
rm: cannot remove `vtx24-': Read-only file system
rm: cannot remove `vbi24-': Read-only file system
mknod: `vbi24-': Read-only file system
makedev vbi24 c 81 248 root video 0660: failed
rm: cannot remove `vbi24-': Read-only file system
rm: cannot remove `vtx25-': Read-only file system
mknod: `vtx25-': Read-only file system
makedev vtx25 c 81 217 root video 0660: failed
rm: cannot remove `vtx25-': Read-only file system
rm: cannot remove `vbi25-': Read-only file system
mknod: `vbi25-': Read-only file system
makedev vbi25 c 81 249 root video 0660: failed
rm: cannot remove `vbi25-': Read-only file system
rm: cannot remove `vtx26-': Read-only file system
mknod: `vtx26-': Read-only file system
makedev vtx26 c 81 218 root video 0660: failed
rm: cannot remove `vtx26-': Read-only file system
rm: cannot remove `vbi26-': Read-only file system
mknod: `vbi26-': Read-only file system
makedev vbi26 c 81 250 root video 0660: failed
rm: cannot remove `vbi26-': Read-only file system
rm: cannot remove `vtx27-': Read-only file system
mknod: `vtx27-': Read-only file system
makedev vtx27 c 81 219 root video 0660: failed
rm: cannot remove `vtx27-': Read-only file system
rm: cannot remove `vbi27-': Read-only file system
mknod: `vbi27-': Read-only file system
makedev vbi27 c 81 251 root video 0660: failed
rm: cannot remove `vbi27-': Read-only file system
rm: cannot remove `vtx28-': Read-only file system
mknod: `vtx28-': Read-only file system
makedev vtx28 c 81 220 root video 0660: failed
rm: cannot remove `vtx28-': Read-only file system
rm: cannot remove `vbi28-': Read-only file system
mknod: `vbi28-': Read-only file system
makedev vbi28 c 81 252 root video 0660: failed
rm: cannot remove `vbi28-': Read-only file system
rm: cannot remove `vtx29-': Read-only file system
mknod: `vtx29-': Read-only file system
makedev vtx29 c 81 221 root video 0660: failed
rm: cannot remove `vtx29-': Read-only file system
rm: cannot remove `vbi29-': Read-only file system
mknod: `vbi29-': Read-only file system
makedev vbi29 c 81 253 root video 0660: failed
rm: cannot remove `vbi29-': Read-only file system
rm: cannot remove `vtx30-': Read-only file system
mknod: `vtx30-': Read-only file system
makedev vtx30 c 81 222 root video 0660: failed
rm: cannot remove `vtx30-': Read-only file system
rm: cannot remove `vbi30-': Read-only file system
mknod: `vbi30-': Read-only file system
makedev vbi30 c 81 254 root video 0660: failed
rm: cannot remove `vbi30-': Read-only file system
rm: cannot remove `vtx31-': Read-only file system
mknod: `vtx31-': Read-only file system
makedev vtx31 c 81 223 root video 0660: failed
rm: cannot remove `vtx31-': Read-only file system
rm: cannot remove `vbi31-': Read-only file system
mknod: `vbi31-': Read-only file system
makedev vbi31 c 81 255 root video 0660: failed
rm: cannot remove `vbi31-': Read-only file system
rm: cannot remove `video': Read-only file system
rm: cannot remove `vbi': Read-only file system
rm: cannot remove `winradio0-': Read-only file system
mknod: `winradio0-': Read-only file system
makedev winradio0 c 82 0 root video 0660: failed
rm: cannot remove `winradio0-': Read-only file system
rm: cannot remove `winradio1-': Read-only file system
mknod: `winradio1-': Read-only file system
makedev winradio1 c 82 1 root video 0660: failed
rm: cannot remove `winradio1-': Read-only file system
rm: cannot remove `vtx-': Read-only file system
mknod: `vtx-': Read-only file system
makedev vtx c 83 0 root video 0660: failed
rm: cannot remove `vtx-': Read-only file system
rm: cannot remove `vttuner-': Read-only file system
mknod: `vttuner-': Read-only file system
makedev vttuner c 83 16 root video 0660: failed
rm: cannot remove `vttuner-': Read-only file system
 * Starting MythTV server: mythbackend                                   [ OK ] 

Setting up mythtv-backend-master (0.21.0+fixes18722-0ubuntu1) ...
Setting up xutils-dev (1:7.4+3) ...
Setting up libxfce4util4 (4.4.2-3ubuntu2) ...

Setting up libexo-0.3-0 (0.3.4-7ubuntu6) ...

Setting up libxfce4mcs-client3 (4.4.2-3) ...

Setting up libxfce4mcs-manager3 (4.4.2-3) ...

Setting up libxfcegui4-4 (4.4.2-4ubuntu2) ...

Setting up exo-utils (0.3.4-7ubuntu6) ...
Setting up gsfonts-x11 (0.20ubuntu1) ...

Setting up tango-icon-theme (0.8.1-3) ...

Setting up gtk2-engines-mythbuntu (0.4-0ubuntu2) ...
Setting up thunar-data (0.9.0-10ubuntu1) ...
Setting up libthunar-vfs-1-2 (0.9.0-10ubuntu1) ...

Setting up mythbuntu-gdm-theme (0.3-0ubuntu2) ...
Setting up xfce4-utils (4.4.2-8ubuntu6) ...

Setting up mythbuntu-default-settings (0.71-0ubuntu2) ...

Setting up mythtv-frontend (0.21.0+fixes18722-0ubuntu1) ...

Setting up mythtv-theme-projectgrayhem (1:0.21.0-0ubuntu1) ...
Setting up mythtv-theme-projectgrayhem-wide (1:0.21.0-0ubuntu2) ...
Setting up mythtv-theme-mythbuntu (0.20080421) ...

Setting up xfce4-mcs-manager (4.4.2-3ubuntu2) ...

Setting up xfce4-mcs-plugins (4.4.2-4ubuntu3) ...
Setting up xfce4-panel (4.4.2-6ubuntu2) ...

Setting up xfce4-mixer-alsa (1:4.4.2-3ubuntu2) ...
Setting up xfce4-mixer (1:4.4.2-3ubuntu2) ...
Setting up xfce4-session (4.4.2-6ubuntu2) ...

Setting up xfdesktop4-data (4.4.2-7ubuntu3) ...
Setting up xfdesktop4 (4.4.2-7ubuntu3) ...

Setting up xfwm4 (4.4.2-5ubuntu2) ...

Setting up mythbuntu-desktop (0.31) ...
Setting up mythtv-themes (0.21.0-0ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for menu ...

---

### Post by Yezinki on 2008-11-11
ubuntu@ubuntu-laptop:~$ sudo apt-get purge amsn amsn-data
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package amsn is not installed, so not removed
Package amsn-data is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev x11proto-xext-dev x11proto-kb-dev libxi-dev
  libxdmcp-dev libsnack2 xtrans-dev x11proto-core-dev libxt-dev libxext-dev
  x11proto-input-dev libpthread-stubs0-dev libxau-dev libpthread-stubs0 tcl8.5
  tk8.4 tk8.5 libx11-dev libxcb-xlib0-dev libxcb1-dev tcl-tls
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu-laptop:~$

---

### Post by linux23dragon on 2008-11-11
> **linux23dragon said:**
> It looks to be just the interface board.  I can't see the tuner chips on he board :(

The Chip seems to be within the metal shield box on the main PCB.

That might be tricky to open up.

---

### Post by Yezinki on 2008-11-11
1. Input jack.

2. Main system.

3, TV Tuner card.

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> mknod: `video41-': Read-only file system
makedev video41 c 81 41 root video 0660: failed
rm: cannot remove `video41-': Read-only file system
rm: cannot remove `radio41-': Read-only file system
mknod: `radio41-': Read-only file system
makedev radio41 c 81 105 root video 0660: failed
rm: cannot remove `radio41-': Read-only file system
rm: cannot remove `video42-': Read-only file system
mknod: `video42-': Read-only file system
makedev video42 c 81 42 root video 0660: failed
rm: cannot remove `video42-': Read-only file system
rm: cannot remove `radio42-': Read-only file system
mknod: `radio42-': Read-only file system
makedev radio42 c 81 106 root video 0660: failed
rm: cannot remove `radio42-': Read-only file system
rm: cannot remove `video43-': Read-only file system
mknod: `video43-': Read-only file system
makedev video43 c 81 43 root video 0660: failed
rm: cannot remove `video43-': Read-only file system
rm: cannot remove `radio43-': Read-only file system
mknod: `radio43-': Read-only file system
makedev radio43 c 81 107 root video 0660: failed
rm: cannot remove `radio43-': Read-only file system
rm: cannot remove `video44-': Read-only file system
mknod: `video44-': Read-only file system
makedev video44 c 81 44 root video 0660: failed
rm: cannot remove `video44-': Read-only file system
rm: cannot remove `radio44-': Read-only file system
mknod: `radio44-': Read-only file system
makedev radio44 c 81 108 root video 0660: failed
rm: cannot remove `radio44-': Read-only file system
rm: cannot remove `video45-': Read-only file system
mknod: `video45-': Read-only file system
makedev video45 c 81 45 root video 0660: failed
rm: cannot remove `video45-': Read-only file system
rm: cannot remove `radio45-': Read-only file system
mknod: `radio45-': Read-only file system
makedev radio45 c 81 109 root video 0660: failed
rm: cannot remove `radio45-': Read-only file system
rm: cannot remove `video46-': Read-only file system
mknod: `video46-': Read-only file system
makedev video46 c 81 46 root video 0660: failed
rm: cannot remove `video46-': Read-only file system
rm: cannot remove `radio46-': Read-only file system
mknod: `radio46-': Read-only file system
makedev radio46 c 81 110 root video 0660: failed
rm: cannot remove `radio46-': Read-only file system
rm: cannot remove `video47-': Read-only file system
mknod: `video47-': Read-only file system
makedev video47 c 81 47 root video 0660: failed
rm: cannot remove `video47-': Read-only file system
rm: cannot remove `radio47-': Read-only file system
mknod: `radio47-': Read-only file system
makedev radio47 c 81 111 root video 0660: failed
rm: cannot remove `radio47-': Read-only file system
rm: cannot remove `video48-': Read-only file system
mknod: `video48-': Read-only file system
makedev video48 c 81 48 root video 0660: failed
rm: cannot remove `video48-': Read-only file system
rm: cannot remove `radio48-': Read-only file system
mknod: `radio48-': Read-only file system
makedev radio48 c 81 112 root video 0660: failed
rm: cannot remove `radio48-': Read-only file system
rm: cannot remove `video49-': Read-only file system
mknod: `video49-': Read-only file system
makedev video49 c 81 49 root video 0660: failed
rm: cannot remove `video49-': Read-only file system
rm: cannot remove `radio49-': Read-only file system
mknod: `radio49-': Read-only file system
makedev radio49 c 81 113 root video 0660: failed
rm: cannot remove `radio49-': Read-only file system
rm: cannot remove `video50-': Read-only file system
mknod: `video50-': Read-only file system
makedev video50 c 81 50 root video 0660: failed
rm: cannot remove `video50-': Read-only file system
rm: cannot remove `radio50-': Read-only file system
mknod: `radio50-': Read-only file system
makedev radio50 c 81 114 root video 0660: failed
rm: cannot remove `radio50-': Read-only file system
rm: cannot remove `video51-': Read-only file system
mknod: `video51-': Read-only file system
makedev video51 c 81 51 root video 0660: failed
rm: cannot remove `video51-': Read-only file system
rm: cannot remove `radio51-': Read-only file system
mknod: `radio51-': Read-only file system
makedev radio51 c 81 115 root video 0660: failed
rm: cannot remove `radio51-': Read-only file system
rm: cannot remove `video52-': Read-only file system
mknod: `video52-': Read-only file system
makedev video52 c 81 52 root video 0660: failed
rm: cannot remove `video52-': Read-only file system
rm: cannot remove `radio52-': Read-only file system
mknod: `radio52-': Read-only file system
makedev radio52 c 81 116 root video 0660: failed
rm: cannot remove `radio52-': Read-only file system
rm: cannot remove `video53-': Read-only file system
mknod: `video53-': Read-only file system
makedev video53 c 81 53 root video 0660: failed
rm: cannot remove `video53-': Read-only file system
rm: cannot remove `radio53-': Read-only file system
mknod: `radio53-': Read-only file system
makedev radio53 c 81 117 root video 0660: failed
rm: cannot remove `radio53-': Read-only file system
rm: cannot remove `video54-': Read-only file system
mknod: `video54-': Read-only file system
makedev video54 c 81 54 root video 0660: failed
rm: cannot remove `video54-': Read-only file system
rm: cannot remove `radio54-': Read-only file system
mknod: `radio54-': Read-only file system
makedev radio54 c 81 118 root video 0660: failed
rm: cannot remove `radio54-': Read-only file system
rm: cannot remove `video55-': Read-only file system
mknod: `video55-': Read-only file system
makedev video55 c 81 55 root video 0660: failed
rm: cannot remove `video55-': Read-only file system
rm: cannot remove `radio55-': Read-only file system
mknod: `radio55-': Read-only file system
makedev radio55 c 81 119 root video 0660: failed
rm: cannot remove `radio55-': Read-only file system
rm: cannot remove `video56-': Read-only file system
mknod: `video56-': Read-only file system
makedev video56 c 81 56 root video 0660: failed
rm: cannot remove `video56-': Read-only file system
rm: cannot remove `radio56-': Read-only file system
mknod: `radio56-': Read-only file system
makedev radio56 c 81 120 root video 0660: failed
rm: cannot remove `radio56-': Read-only file system
rm: cannot remove `video57-': Read-only file system
mknod: `video57-': Read-only file system
makedev video57 c 81 57 root video 0660: failed
rm: cannot remove `video57-': Read-only file system
rm: cannot remove `radio57-': Read-only file system
mknod: `radio57-': Read-only file system
makedev radio57 c 81 121 root video 0660: failed
rm: cannot remove `radio57-': Read-only file system
rm: cannot remove `video58-': Read-only file system
mknod: `video58-': Read-only file system
makedev video58 c 81 58 root video 0660: failed
rm: cannot remove `video58-': Read-only file system
rm: cannot remove `radio58-': Read-only file system
mknod: `radio58-': Read-only file system
makedev radio58 c 81 122 root video 0660: failed
rm: cannot remove `radio58-': Read-only file system
rm: cannot remove `video59-': Read-only file system
mknod: `video59-': Read-only file system
makedev video59 c 81 59 root video 0660: failed
rm: cannot remove `video59-': Read-only file system
rm: cannot remove `radio59-': Read-only file system
mknod: `radio59-': Read-only file system
makedev radio59 c 81 123 root video 0660: failed
rm: cannot remove `radio59-': Read-only file system
rm: cannot remove `video60-': Read-only file system
mknod: `video60-': Read-only file system
makedev video60 c 81 60 root video 0660: failed
rm: cannot remove `video60-': Read-only file system
rm: cannot remove `radio60-': Read-only file system
mknod: `radio60-': Read-only file system
makedev radio60 c 81 124 root video 0660: failed
rm: cannot remove `radio60-': Read-only file system
rm: cannot remove `video61-': Read-only file system
mknod: `video61-': Read-only file system
makedev video61 c 81 61 root video 0660: failed
rm: cannot remove `video61-': Read-only file system
rm: cannot remove `radio61-': Read-only file system
mknod: `radio61-': Read-only file system
makedev radio61 c 81 125 root video 0660: failed
rm: cannot remove `radio61-': Read-only file system
rm: cannot remove `video62-': Read-only file system
mknod: `video62-': Read-only file system
makedev video62 c 81 62 root video 0660: failed
rm: cannot remove `video62-': Read-only file system
rm: cannot remove `radio62-': Read-only file system
mknod: `radio62-': Read-only file system
makedev radio62 c 81 126 root video 0660: failed
rm: cannot remove `radio62-': Read-only file system
rm: cannot remove `video63-': Read-only file system
mknod: `video63-': Read-only file system
makedev video63 c 81 63 root video 0660: failed
rm: cannot remove `video63-': Read-only file system
rm: cannot remove `radio63-': Read-only file system
mknod: `radio63-': Read-only file system
makedev radio63 c 81 127 root video 0660: failed
rm: cannot remove `radio63-': Read-only file system
rm: cannot remove `radio': Read-only file system
rm: cannot remove `vtx0-': Read-only file system
mknod: `vtx0-': Read-only file system
makedev vtx0 c 81 192 root video 0660: failed
rm: cannot remove `vtx0-': Read-only file system
rm: cannot remove `vbi0-': Read-only file system
mknod: `vbi0-': Read-only file system
makedev vbi0 c 81 224 root video 0660: failed
rm: cannot remove `vbi0-': Read-only file system
rm: cannot remove `vtx1-': Read-only file system
mknod: `vtx1-': Read-only file system
makedev vtx1 c 81 193 root video 0660: failed
rm: cannot remove `vtx1-': Read-only file system
rm: cannot remove `vbi1-': Read-only file system
mknod: `vbi1-': Read-only file system
makedev vbi1 c 81 225 root video 0660: failed
rm: cannot remove `vbi1-': Read-only file system
rm: cannot remove `vtx2-': Read-only file system
mknod: `vtx2-': Read-only file system
makedev vtx2 c 81 194 root video 0660: failed
rm: cannot remove `vtx2-': Read-only file system
rm: cannot remove `vbi2-': Read-only file system
mknod: `vbi2-': Read-only file system
makedev vbi2 c 81 226 root video 0660: failed
rm: cannot remove `vbi2-': Read-only file system
rm: cannot remove `vtx3-': Read-only file system
mknod: `vtx3-': Read-only file system
makedev vtx3 c 81 195 root video 0660: failed
rm: cannot remove `vtx3-': Read-only file system
rm: cannot remove `vbi3-': Read-only file system
mknod: `vbi3-': Read-only file system
makedev vbi3 c 81 227 root video 0660: failed
rm: cannot remove `vbi3-': Read-only file system
rm: cannot remove `vtx4-': Read-only file system
mknod: `vtx4-': Read-only file system
makedev vtx4 c 81 196 root video 0660: failed
rm: cannot remove `vtx4-': Read-only file system
rm: cannot remove `vbi4-': Read-only file system
mknod: `vbi4-': Read-only file system
makedev vbi4 c 81 228 root video 0660: failed
rm: cannot remove `vbi4-': Read-only file system
rm: cannot remove `vtx5-': Read-only file system
mknod: `vtx5-': Read-only file system
makedev vtx5 c 81 197 root video 0660: failed
rm: cannot remove `vtx5-': Read-only file system
rm: cannot remove `vbi5-': Read-only file system
mknod: `vbi5-': Read-only file system
makedev vbi5 c 81 229 root video 0660: failed
rm: cannot remove `vbi5-': Read-only file system
rm: cannot remove `vtx6-': Read-only file system
mknod: `vtx6-': Read-only file system
makedev vtx6 c 81 198 root video 0660: failed
rm: cannot remove `vtx6-': Read-only file system
rm: cannot remove `vbi6-': Read-only file system
mknod: `vbi6-': Read-only file system
makedev vbi6 c 81 230 root video 0660: failed
rm: cannot remove `vbi6-': Read-only file system
rm: cannot remove `vtx7-': Read-only file system
mknod: `vtx7-': Read-only file system
makedev vtx7 c 81 199 root video 0660: failed
rm: cannot remove `vtx7-': Read-only file system
rm: cannot remove `vbi7-': Read-only file system
mknod: `vbi7-': Read-only file system
makedev vbi7 c 81 231 root video 0660: failed
rm: cannot remove `vbi7-': Read-only file system
rm: cannot remove `vtx8-': Read-only file system
mknod: `vtx8-': Read-only file system
makedev vtx8 c 81 200 root video 0660: failed
rm: cannot remove `vtx8-': Read-only file system
rm: cannot remove `vbi8-': Read-only file system
mknod: `vbi8-': Read-only file system
makedev vbi8 c 81 232 root video 0660: failed
rm: cannot remove `vbi8-': Read-only file system
rm: cannot remove `vtx9-': Read-only file system
mknod: `vtx9-': Read-only file system
makedev vtx9 c 81 201 root video 0660: failed
rm: cannot remove `vtx9-': Read-only file system
rm: cannot remove `vbi9-': Read-only file system
mknod: `vbi9-': Read-only file system
makedev vbi9 c 81 233 root video 0660: failed
rm: cannot remove `vbi9-': Read-only file system
rm: cannot remove `vtx10-': Read-only file system
mknod: `vtx10-': Read-only file system
makedev vtx10 c 81 202 root video 0660: failed
rm: cannot remove `vtx10-': Read-only file system
rm: cannot remove `vbi10-': Read-only file system
mknod: `vbi10-': Read-only file system
makedev vbi10 c 81 234 root video 0660: failed
rm: cannot remove `vbi10-': Read-only file system
rm: cannot remove `vtx11-': Read-only file system
mknod: `vtx11-': Read-only file system
makedev vtx11 c 81 203 root video 0660: failed
rm: cannot remove `vtx11-': Read-only file system
rm: cannot remove `vbi11-': Read-only file system
mknod: `vbi11-': Read-only file system
makedev vbi11 c 81 235 root video 0660: failed
rm: cannot remove `vbi11-': Read-only file system
rm: cannot remove `vtx12-': Read-only file system
mknod: `vtx12-': Read-only file system
makedev vtx12 c 81 204 root video 0660: failed
rm: cannot remove `vtx12-': Read-only file system
rm: cannot remove `vbi12-': Read-only file system
mknod: `vbi12-': Read-only file system
makedev vbi12 c 81 236 root video 0660: failed
rm: cannot remove `vbi12-': Read-only file system
rm: cannot remove `vtx13-': Read-only file system
mknod: `vtx13-': Read-only file system
makedev vtx13 c 81 205 root video 0660: failed
rm: cannot remove `vtx13-': Read-only file system
rm: cannot remove `vbi13-': Read-only file system
mknod: `vbi13-': Read-only file system
makedev vbi13 c 81 237 root video 0660: failed
rm: cannot remove `vbi13-': Read-only file system
rm: cannot remove `vtx14-': Read-only file system
mknod: `vtx14-': Read-only file system
makedev vtx14 c 81 206 root video 0660: failed
rm: cannot remove `vtx14-': Read-only file system
rm: cannot remove `vbi14-': Read-only file system
mknod: `vbi14-': Read-only file system
makedev vbi14 c 81 238 root video 0660: failed
rm: cannot remove `vbi14-': Read-only file system
rm: cannot remove `vtx15-': Read-only file system
mknod: `vtx15-': Read-only file system
makedev vtx15 c 81 207 root video 0660: failed
rm: cannot remove `vtx15-': Read-only file system
rm: cannot remove `vbi15-': Read-only file system
mknod: `vbi15-': Read-only file system
makedev vbi15 c 81 239 root video 0660: failed
rm: cannot remove `vbi15-': Read-only file system
rm: cannot remove `vtx16-': Read-only file system
mknod: `vtx16-': Read-only file system
makedev vtx16 c 81 208 root video 0660: failed
rm: cannot remove `vtx16-': Read-only file system
rm: cannot remove `vbi16-': Read-only file system
mknod: `vbi16-': Read-only file system
makedev vbi16 c 81 240 root video 0660: failed
rm: cannot remove `vbi16-': Read-only file system
rm: cannot remove `vtx17-': Read-only file system
mknod: `vtx17-': Read-only file system
makedev vtx17 c 81 209 root video 0660: failed
rm: cannot remove `vtx17-': Read-only file system
rm: cannot remove `vbi17-': Read-only file system
mknod: `vbi17-': Read-only file system
makedev vbi17 c 81 241 root video 0660: failed
rm: cannot remove `vbi17-': Read-only file system
rm: cannot remove `vtx18-': Read-only file system
mknod: `vtx18-': Read-only file system
makedev vtx18 c 81 210 root video 0660: failed
rm: cannot remove `vtx18-': Read-only file system
rm: cannot remove `vbi18-': Read-only file system
mknod: `vbi18-': Read-only file system
makedev vbi18 c 81 242 root video 0660: failed
rm: cannot remove `vbi18-': Read-only file system
rm: cannot remove `vtx19-': Read-only file system
mknod: `vtx19-': Read-only file system
makedev vtx19 c 81 211 root video 0660: failed
rm: cannot remove `vtx19-': Read-only file system
rm: cannot remove `vbi19-': Read-only file system
mknod: `vbi19-': Read-only file system
makedev vbi19 c 81 243 root video 0660: failed
rm: cannot remove `vbi19-': Read-only file system
rm: cannot remove `vtx20-': Read-only file system
mknod: `vtx20-': Read-only file system
makedev vtx20 c 81 212 root video 0660: failed
rm: cannot remove `vtx20-': Read-only file system
rm: cannot remove `vbi20-': Read-only file system
mknod: `vbi20-': Read-only file system
makedev vbi20 c 81 244 root video 0660: failed
rm: cannot remove `vbi20-': Read-only file system
rm: cannot remove `vtx21-': Read-only file system
mknod: `vtx21-': Read-only file system
makedev vtx21 c 81 213 root video 0660: failed
rm: cannot remove `vtx21-': Read-only file system
rm: cannot remove `vbi21-': Read-only file system
mknod: `vbi21-': Read-only file system
makedev vbi21 c 81 245 root video 0660: failed
rm: cannot remove `vbi21-': Read-only file system
rm: cannot remove `vtx22-': Read-only file system
mknod: `vtx22-': Read-only file system
makedev vtx22 c 81 214 root video 0660: failed
rm: cannot remove `vtx22-': Read-only file system
rm: cannot remove `vbi22-': Read-only file system
mknod: `vbi22-': Read-only file system
makedev vbi22 c 81 246 root video 0660: failed
rm: cannot remove `vbi22-': Read-only file system
rm: cannot remove `vtx23-': Read-only file system
mknod: `vtx23-': Read-only file system
makedev vtx23 c 81 215 root video 0660: failed
rm: cannot remove `vtx23-': Read-only file system
rm: cannot remove `vbi23-': Read-only file system
mknod: `vbi23-': Read-only file system
makedev vbi23 c 81 247 root video 0660: failed
rm: cannot remove `vbi23-': Read-only file system
rm: cannot remove `vtx24-': Read-only file system
mknod: `vtx24-': Read-only file system
makedev vtx24 c 81 216 root video 0660: failed
rm: cannot remove `vtx24-': Read-only file system
rm: cannot remove `vbi24-': Read-only file system
mknod: `vbi24-': Read-only file system
makedev vbi24 c 81 248 root video 0660: failed
rm: cannot remove `vbi24-': Read-only file system
rm: cannot remove `vtx25-': Read-only file system
mknod: `vtx25-': Read-only file system
makedev vtx25 c 81 217 root video 0660: failed
rm: cannot remove `vtx25-': Read-only file system
rm: cannot remove `vbi25-': Read-only file system
mknod: `vbi25-': Read-only file system
makedev vbi25 c 81 249 root video 0660: failed
rm: cannot remove `vbi25-': Read-only file system
rm: cannot remove `vtx26-': Read-only file system
mknod: `vtx26-': Read-only file system
makedev vtx26 c 81 218 root video 0660: failed
rm: cannot remove `vtx26-': Read-only file system
rm: cannot remove `vbi26-': Read-only file system
mknod: `vbi26-': Read-only file system
makedev vbi26 c 81 250 root video 0660: failed
rm: cannot remove `vbi26-': Read-only file system
rm: cannot remove `vtx27-': Read-only file system
mknod: `vtx27-': Read-only file system
makedev vtx27 c 81 219 root video 0660: failed
rm: cannot remove `vtx27-': Read-only file system
rm: cannot remove `vbi27-': Read-only file system
mknod: `vbi27-': Read-only file system
makedev vbi27 c 81 251 root video 0660: failed
rm: cannot remove `vbi27-': Read-only file system
rm: cannot remove `vtx28-': Read-only file system
mknod: `vtx28-': Read-only file system
makedev vtx28 c 81 220 root video 0660: failed
rm: cannot remove `vtx28-': Read-only file system
rm: cannot remove `vbi28-': Read-only file system
mknod: `vbi28-': Read-only file system
makedev vbi28 c 81 252 root video 0660: failed
rm: cannot remove `vbi28-': Read-only file system
rm: cannot remove `vtx29-': Read-only file system
mknod: `vtx29-': Read-only file system
makedev vtx29 c 81 221 root video 0660: failed
rm: cannot remove `vtx29-': Read-only file system
rm: cannot remove `vbi29-': Read-only file system
mknod: `vbi29-': Read-only file system
makedev vbi29 c 81 253 root video 0660: failed
rm: cannot remove `vbi29-': Read-only file system
rm: cannot remove `vtx30-': Read-only file system
mknod: `vtx30-': Read-only file system
makedev vtx30 c 81 222 root video 0660: failed
rm: cannot remove `vtx30-': Read-only file system
rm: cannot remove `vbi30-': Read-only file system
mknod: `vbi30-': Read-only file system
makedev vbi30 c 81 254 root video 0660: failed
rm: cannot remove `vbi30-': Read-only file system
rm: cannot remove `vtx31-': Read-only file system
mknod: `vtx31-': Read-only file system
makedev vtx31 c 81 223 root video 0660: failed
rm: cannot remove `vtx31-': Read-only file system
rm: cannot remove `vbi31-': Read-only file system
mknod: `vbi31-': Read-only file system
makedev vbi31 c 81 255 root video 0660: failed
rm: cannot remove `vbi31-': Read-only file system
rm: cannot remove `video': Read-only file system
rm: cannot remove `vbi': Read-only file system
rm: cannot remove `winradio0-': Read-only file system
mknod: `winradio0-': Read-only file system
makedev winradio0 c 82 0 root video 0660: failed
rm: cannot remove `winradio0-': Read-only file system
rm: cannot remove `winradio1-': Read-only file system
mknod: `winradio1-': Read-only file system
makedev winradio1 c 82 1 root video 0660: failed
rm: cannot remove `winradio1-': Read-only file system
rm: cannot remove `vtx-': Read-only file system
mknod: `vtx-': Read-only file system
makedev vtx c 83 0 root video 0660: failed
rm: cannot remove `vtx-': Read-only file system
rm: cannot remove `vttuner-': Read-only file system
mknod: `vttuner-': Read-only file system
makedev vttuner c 83 16 root video 0660: failed
rm: cannot remove `vttuner-': Read-only file system


That was the myth-TV  installing, and seting up permissions for multi media device nodes in /dev for the TV tunner (if installed and has a working driver). 

> **Yezinki said:**
> 
 * Starting MythTV server: mythbackend                                   [ OK ] 

Setting up mythtv-backend-master (0.21.0+fixes18722-0ubuntu1) ...
Setting up xutils-dev (1:7.4+3) ...
Setting up libxfce4util4 (4.4.2-3ubuntu2) ...

Setting up libexo-0.3-0 (0.3.4-7ubuntu6) ...

Setting up libxfce4mcs-client3 (4.4.2-3) ...

Setting up libxfce4mcs-manager3 (4.4.2-3) ...

Setting up libxfcegui4-4 (4.4.2-4ubuntu2) ...

Setting up exo-utils (0.3.4-7ubuntu6) ...
Setting up gsfonts-x11 (0.20ubuntu1) ...

Setting up tango-icon-theme (0.8.1-3) ...

Setting up gtk2-engines-mythbuntu (0.4-0ubuntu2) ...
Setting up thunar-data (0.9.0-10ubuntu1) ...
Setting up libthunar-vfs-1-2 (0.9.0-10ubuntu1) ...

Setting up mythbuntu-gdm-theme (0.3-0ubuntu2) ...
Setting up xfce4-utils (4.4.2-8ubuntu6) ...

Setting up mythbuntu-default-settings (0.71-0ubuntu2) ...

Setting up mythtv-frontend (0.21.0+fixes18722-0ubuntu1) ...

Setting up mythtv-theme-projectgrayhem (1:0.21.0-0ubuntu1) ...
Setting up mythtv-theme-projectgrayhem-wide (1:0.21.0-0ubuntu2) ...
Setting up mythtv-theme-mythbuntu (0.20080421) ...

Setting up xfce4-mcs-manager (4.4.2-3ubuntu2) ...

Setting up xfce4-mcs-plugins (4.4.2-4ubuntu3) ...
Setting up xfce4-panel (4.4.2-6ubuntu2) ...

Setting up xfce4-mixer-alsa (1:4.4.2-3ubuntu2) ...
Setting up xfce4-mixer (1:4.4.2-3ubuntu2) ...
Setting up xfce4-session (4.4.2-6ubuntu2) ...

Setting up xfdesktop4-data (4.4.2-7ubuntu3) ...
Setting up xfdesktop4 (4.4.2-7ubuntu3) ...

Setting up xfwm4 (4.4.2-5ubuntu2) ...

Setting up mythbuntu-desktop (0.31) ...
Setting up mythtv-themes (0.21.0-0ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for menu ...

All seems to be ok.

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> ubuntu@ubuntu-laptop:~$ sudo apt-get purge amsn amsn-data
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package amsn is not installed, so not removed
Package amsn-data is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev x11proto-xext-dev x11proto-kb-dev libxi-dev
  libxdmcp-dev libsnack2 xtrans-dev x11proto-core-dev libxt-dev libxext-dev
  x11proto-input-dev libpthread-stubs0-dev libxau-dev libpthread-stubs0 tcl8.5
  tk8.4 tk8.5 libx11-dev libxcb-xlib0-dev libxcb1-dev tcl-tls
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu-laptop:~$

Try to install amsn now (via Synaptic package manager)

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> 1. Input jack.

2. Main system.

3, TV Tuner card.

Nice looking card.  Can you use macros mode?  The I can't read details on the chips.

---

### Post by Yezinki on 2008-11-11
```
The Chip seems to be within the metal shield box on the main PCB.

That might be tricky to open up.
```


I agree with you.....every thing is covered in foil,plastic & ceramic.......

---

### Post by Yezinki on 2008-11-11
> **linux23dragon said:**
> Nice looking card.  Can you use macros mode?  The I can't read details on the chips.

which pic are you referring to??

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> which pic are you referring to??

All of the close up shots of the TV card itself.

---

### Post by Yezinki on 2008-11-11
Same error........

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> Same error........

Oh that error lol. No problem.

```
mv -v /home/ubuntu/.amsn /home/ubuntu/amsn-corrupted-data
```

---

### Post by Yezinki on 2008-11-11
```
ubuntu@ubuntu-laptop:~$ mv -v /home/ubuntu/.amsn /home/ubuntu/amsn-corrupted-data
`/home/ubuntu/.amsn' -> `/home/ubuntu/amsn-corrupted-data'

```

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> ```
ubuntu@ubuntu-laptop:~$ mv -v /home/ubuntu/.amsn /home/ubuntu/amsn-corrupted-data
`/home/ubuntu/.amsn' -> `/home/ubuntu/amsn-corrupted-data'

```

Excellent.  now you should be able to start amsn

---

### Post by Yezinki on 2008-11-11
At last YES>>>>>>>>>>>> No wonder you are the LINUX KING!!

---

### Post by Yezinki on 2008-11-11
BUT no Cam...........:(

---

### Post by Yezinki on 2008-11-11
which pic were you refering to?? No........###???????

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> BUT no Cam...........:(

The webcam driver is updated at least once or twice a week.  try updating the driver again.  It was updated yesterday and today I think.

The driver comes directly from the developers.

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> which pic were you refering to?? No........###???????

Image320.jpg
Image318.jpg
Image322.jpg

---

### Post by linux23dragon on 2008-11-11
> **linux23dragon said:**
> The webcam driver is updated at least once or twice a week.  try updating the driver again.  It was updated yesterday and today I think.

The driver comes directly from the developers.

Yep it has been worked on.

see this link for gspca driver updates

[http://linuxtv.org/hg/~jfrancois/gspca](http://linuxtv.org/hg/~jfrancois/gspca)

I suspect he will be going more updates as time goes on.  It appears to be a re write

---

### Post by Yezinki on 2008-11-11
Seen all pics?

Whats the site for driver updates?

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> Seen all pics?

Whats the site for driver updates?

Regards,

Yezinki.

Correct.  It is the actual driver development been done on the gspca drivers from the developer himself.

---

### Post by Yezinki on 2008-11-11
Works OK with Ekiga with aMSN has an issue....

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> Works OK with Ekiga with aMSN has an issue....

OK, thats after you updated the driver and rebooted the PC?

---

### Post by Yezinki on 2008-11-11
Yes.

---

### Post by Yezinki on 2008-11-11
KING see for yourself.........Logitech quick cam pro 9000 with aMSN & the other with Ekiga.

Why won't the other work with aMSN??

---

### Post by Yezinki on 2008-11-11
**Logitech shows as [B]v4l2 UVC camera 046d: 0990**

While the built in as **v4l2 USB 2.0 Camera**...in the same aMSN preferences window??[/B]

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> Yes.

OK the best bet is to keep the driver updated.   

Keep an eye out for ***0ac8:c002*** and ***vc032x*** in the Developers [[COLOR="Blue"]***_Summery page_***[/COLOR]]("http://linuxtv.org/hg/~jfrancois/gspca") for updates on your actual webcam driver. 

So far it looks like they are rewriting code so there is no driver duplication issues.

Their is a meant to be webcam tester for amsn as well. It is just a script or small binary program I think.

That might be good to check out, so we can inform the amsn developers if the cam works with their tester or not.

---

### Post by Yezinki on 2008-11-11
USB cam's channel shows vcO32x while Logitech shows as Camera 1??

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> **Logitech shows as [B]v4l2 UVC camera 046d: 0990**

While the built in as **v4l2 USB 2.0 Camera**...in the same aMSN preferences window??[/B]

yep, that's ok.  They use two completely different video controllers.

---

### Post by Yezinki on 2008-11-11
> **linux23dragon said:**
> ```

sda1    C:/      NTFS     60GB            |
sda2    D:/      NTFS     60GB            | <-- Primary partition
sda3    /boot    ext3     200MB           |
sda4    ->Extended Partition<-
sda5    /        XFS      1GB            ||
sda6    /usr     XFS      20GB           ||
sda7    /var     XFS      5GB            || <-- Logical drives
sda8    /tmp     XFS      13GB           ||
sda9    SWAP              512MB          ||
sda10   /home    XFS      72GB           ||

```

The Master Boot Record (MBR) must be installed on sda (or sda0)

KING you want  me to start from here????????

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> USB cam's channel shows vcO32x while Logitech shows as Camera 1??

Yea my logitech shows Camera 1 as well.  That is normal.

See how many different video devices you have connected, by running this command.

```
ls -la /dev/video*
```

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> KING you want  me to start from here????????

Yes, that would be better option for you currently.  You will have the best of both worlds at your finger tips.


Start installing windows first.
Create one partition to install windows (C: drive).
Then scandisk the C: drive afterwards.
Then install Ubuntu.  Installing Ubuntu will allow you to add the second D: drive (sda2) which windows will format as NTFS.  unless you have another partitioning tool handy.

---

### Post by Yezinki on 2008-11-11
> **linux23dragon said:**
> Yea my logitech shows Camera 1 as well.  That is normal.

See how many different video devices you have connected, by running this command.

```
ls -la /dev/video*
```



[B]ubuntu@ubuntu-laptop:~$ ls -la /dev/video*
crw-rw----+ 1 root video 81, 0 2008-11-11 13:18 /dev/video0
ubuntu@ubuntu-laptop:~$ 

[/B]

---

### Post by Yezinki on 2008-11-11
> **linux23dragon said:**
> Yes, that would be better option for you currently.  You will have the best of both worlds at your finger tips.


Start installing windows first.
Create one partition to install windows (C: drive).
Then scandisk the C: drive afterwards.
Then install Ubuntu.  Installing Ubuntu will allow you to add the second D: drive (sda2) which windows will format as NTFS.  unless you have another partitioning tool handy.



C & D both for windows yes?

Ubuntu in free space after D?

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> C & D both for windows yes?

Ubuntu in free space after D?

correct :)

---

### Post by Yezinki on 2008-11-11
**windows will format as NTFS. unless you have another partitioning tool handy.**

What exactly do you want me to partition with.....

---

### Post by Yezinki on 2008-11-11
Did you have a good look at the pics?

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> **windows will format as NTFS. unless you have another partitioning tool handy.**

What exactly do you want me to partition with.....

I was hopping you can partition with both windows and Ubuntu.  
But if you have issues that you OEM XP might create, then I might introduce a third party partitioning tool.

But for now, keep with Windows and Ubuntu for partitioning your drive.

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> Did you have a good look at the pics?

Yes thank you.  

You really did go to town dismantling your PC like that. :guitar:

---

### Post by Yezinki on 2008-11-11
**```
I might introduce a third party partitioning tool.
```**

KING please do.........

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-11
> **Yezinki said:**
> **```
I might introduce a third party partitioning tool.
```**

KING please do.........

Regards,

Yezinki.

Well there is two you can use.  But it has been a long time since I have ever used them.  

When I was using Mandarke (now called [[COLOR="Blue"]***_Mandriva_***[/COLOR]]("http://www.mandriva.com/en/download/free")) they had one of the most powerful partitioning tools I had ever seen.  You can allocate partition numbering, choose what partition was primary or logical.  And you could also format Fat32 and even resize partitions (even resize windows partitions).

You had to be in expert mode to have all of those features.   


The other is called [[COLOR="Blue"]_***partition magic***_[/COLOR]]("http://www.soft32.com/download_151.html").

It does not matter what you format you use (with the partitioning tools) since you can always reformat the drive when you install Ubuntu.

Give them a go.

---

### Post by Yezinki on 2008-11-12
Hi **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUX KING![/COLOR][/SIZE][/FONT]**

I am starting a new thread in General help sub forum......Partitioning........kindly have a look & post your views!

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-13
LINUX KING!

My Cam works with Ekiga even with a fresh Ubuntu install???????

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-13
> **Yezinki said:**
> LINUX KING!

My Cam works with Ekiga even with a fresh Ubuntu install???????

Regards,

Yezinki.

It appears that there might be a kernel update with the updated drivers.  The other issues are possibly due to gstreamer and possibly v4L2.

But that might not fix the aMSN issues.

Did you try Ekiga before you installed the driver update I posted?

---

### Post by Yezinki on 2008-11-13
Yes before haven't updated the driver plan you made.

Regards,

Yezinki.

---

