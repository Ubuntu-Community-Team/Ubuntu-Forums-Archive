---
title: "Suggest a Cheap PCI-e  choice for old system"
date: 2016-02-16
forum: Hardware
---

### Post by NS on 2016-02-16
I have an old Dell Dimension E310 that i have revived into  Ubuntu 14.04 LTS machine.  Last year, netflix was streaming fine on this machine (soon after  Ubuntu installation) using chrome.  It was on break, and i resurrected it again, to stream video in my home.  Meanwhile Chrome is version 45.0  now,  but  netflix is not streaming  smoothly anymore.  It stutters, and i found that other sites (cbs.com, abc.com etc)  show video in low def. I also notice that my CPU spikes to 100%  when using netflix (but not others).   So, i have decided to try installing a pci-e  card to help the CPU.

Currently, the video is being driven by Intel chipset that has 256MB video memory.  I am not playing any games on this, and it was enough before !!!  All the latest  changes to Adobe flash & chrome sandboxing it and packing it along, has changed the video streaming quality.   The machine has  only  a pci-e 1x  slot, but i found that i can purchase any cheap pci-e  card on ebay and cut it to fit into the 1x slot.  So, i am wondering if my OS will be happy with any card,  or if there is a compatibility list somewhere.  I do not want to run into driver issues, even though i am trying to find the budget ones on ebay.   Please  suggest brand names,  or share your experience in using a 1x  slot  alongside  Ubuntu LTS.

---

### Post by weatherman2 on 2016-02-17
I have worked on a lot of Dell towers of that vintage, though I can't remember its exact specs.  If it has a Pentium 4 or Pentium D CPU, then I'd say it is pretty much obsolete, and you would be much better off putting any money you'd spend on a graphics card into a new tower instead.  Even the newer Core 2 Duo CPUs are starting to feel old.  I've spent too much time in the past trying to refurbish and nurse along too many of these old towers to try to keep them going, but at some point it's a waste of time.  In your case, I'd think you'd be much better off with a faster, newer CPU.

---

### Post by mastablasta on 2016-02-17
NVidia GT 210 or GT 610 should be good enough for your needs. otherwise GT 730 is a bit more expensive if you plan to invest a bit more. it of course depends on the CPU.

if CPU is descent then card will help. if CPU is the bottle neck then it won't.

@weatherman2 - exchanging CPU usually means - replacing almost the whole thing which is a lot more expensive and creates unnecessary waste if you do not actually need it. you would need to change the motherboard, ram and GPU which in total can be at least 3x or 4x the amount it would take to just upgrade the GPU.

---

### Post by mörgæs on 2016-02-17
Before buying more gear I recommend that we take a look at what you have got now. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by weatherman2 on 2016-02-17
> **mastablasta said:**
> @weatherman2 - exchanging CPU usually means - replacing almost the whole thing which is a lot more expensive and creates unnecessary waste if you do not actually need it. you would need to change the motherboard, ram and GPU which in total can be at least 3x or 4x the amount it would take to just upgrade the GPU.

I would recommend just getting a new tower. I think this one is over ten years old.  Even a Core 2 Duo - if this old Dell is a Pentium 4 - will be much better.  They are not expensive used.  As I said, I have worked on and tried to refurbish and reuse many of these old towers.  It's questionable whether it is worth the time, but it's probably not worth much money if any to keep them going.

If you look for sales and deals, building a much newer budget box could be very cheap.  This is usually how I do my builds.  Look for motherboards and cheap CPU combos on Newegg, etc.  I've built a couple of towers for under $100 USD out of sale parts over the last few years.

---

### Post by NS on 2016-02-17
Thanks all.  I have looked into this system throughly, when i resurrected it, purely for fun and for use at home as netflix streaming machine. Nothing serious is being done on this machine.   Here is the system essentials :  Dell Dimension 3100 (E310 model) with Pentium 4 (Prescott)  2.8GHz, Hyper threading 64-bit CPU,  3GB RAM, Integrated  Intel video 915GV using 256MB shared memory, slow old HDD connected to a 36 Mb/sec cable modem internet.  All other streaming sites (abc, cbs, youtube) are streaming without bottleneck but netflix hiccups (only during the first 5  minutes or so, when i startup a fresh video).  Once it is streaming for 10 minutes, no more pauses for half second that happens during beginning of netflix session.  Running task manager clearly shows 100% CPU during these hiccups and getting a seperate video card would  take the load off the CPU, and might give me a higher resolution which my TV is capable of handling.
                     I have linked  to** [the output from lshw]("http://paste.ubuntu.com/15102579/")**.   [http://paste.ubuntu.com/15102579/](http://paste.ubuntu.com/15102579/)

 weatherman2  has a point about not spending time on old systems, while i get a newer laptop on sale for about $150 in my area. But, i have already spent the major time on this system, while nuking the Windows and installing Ubuntu (my very first Ubuntu system).

 Mastablasta - thanks for suggestion on Nvidia GT210 and 610 models. They are going for about $30 on average in ebay with 1GB memory.  These are for gamers, and overkill for streaming video.  I found a bunch of  ATI radeon on ebay with 512 MB memory going for about $15.  See below for an example.   I remember reading somewhere not to mix intel chipset mobo (like mine) with a AMD chipset graphics card.  I take it that Nvidia brand is ok to use. Not sure Ubuntu compatibility of ATI Radeon;  comments welcome......   [http://www.ebay.com/itm/Dell-ATi-Radeon-HD-4350-512MB-VGA-DVI-HDMI-PCI-e-Video-Card-dell-P002P-/161890470959?hash=item25b16c8c2f:g:jPUAAOSw4UtWS8hs](http://www.ebay.com/itm/Dell-ATi-Radeon-HD-4350-512MB-VGA-DVI-HDMI-PCI-e-Video-Card-dell-P002P-/161890470959?hash=item25b16c8c2f:g:jPUAAOSw4UtWS8hs)

BTW, once i get the card, how do i install the corresponding video driver in Ubuntu ? Most likely i can find windows drivers for the card on internet.  Is there a * driver manager *(similar to Ubuntu Software download center)  that i can use find drivers ?

---

### Post by NS on 2016-02-17
Next, i need to figure out why netflix is not showing the little  "_**HD**_"  icon,  even though my TV is at 1360 x 768,  which satisfies  HD requirement, and my internet speed is high enough.  I do get HD on my macbook pro for the same movies !!  So, i am hoping this will be also resolved  by spending $20.

---

### Post by weatherman2 on 2016-02-17
FYI, a separate video card doesn't completely take the load off of the CPU.  It will give you back some of the integrated RAM, though.

Be careful with PCI-E video cards.  There are different standards for that slot.  If your PC's PCI-E slot is only say 1.0, a graphics card that is 2.0 may not work in the PC.  I can confirm that indeed I had a couple of old PCs where this turned out to be the case.  Find out what standard of PCI-E your Dell supports - I suspect only 1.0, like my old Dell that had a Core 2 Duo in it.  That means you need to find a graphics card that also is backward compatible to 1.0.

Also, you may need to increase the power supply with a new graphics card, which can really suck down the power.

Your new video card is likely to have a chipset from either Radeon (AMD) or Nvidia.  There's a good chance that it will boot in Ubuntu without installing anything but you would still want to install an optimal driver.  There are really two ways to do that in Ubuntu: either let Ubuntu search for a compatible "Additional Driver" (proprietary) or go to the manufacturer's website (AMD or Nvidia) and download/install their latest Linux driver for the card, following their specific instructions.

Your idea of cutting the PCI-E card to fit into a 1X slot would make me even more wary of spending any money on this.

Which flavor of Ubuntu are you running?  Have you tried Gnome Flashback (Metacity) which gives you the old Gnome (Mate) feel?  The Metacity option is also less resource-intensive.

You could actually get a faster Prescott P4 for that thing, though they all run really hot.  If it's socket 775, you can get 3.2GHZ and 3.4GHZ Prescotts - I used to have a few laying around, but I have gotten rid of all of my old P4 stuff.  The faster the CPU, of course, the more power it will draw, so you really the heat sink clean, the fan working properly, etc.

---

### Post by weatherman2 on 2016-02-17
> **NS said:**
> Next, i need to figure out why netflix is not showing the little  "_**HD**_"  icon,  even though my TV is at 1360 x 768,  which satisfies  HD requirement, and my internet speed is high enough.  I do get HD on my macbook pro for the same movies !!  So, i am hoping this will be also resolved  by spending $20.

It could be that Netflix things your PC is too slow to handle streaming of HD content, and from what you describe, that is probably true.  If the CPU is already at 100% trying to stream SD content, there's no way it would keep up with HD streams.  It would do the same thing if your network was too slow - but you say you get HD on other devices so obviously that's not the problem for you.

---

### Post by Yellow Pasque on 2016-02-18
There are a lot of cheap, low-end used PCI-e x16 cards out there that would help with video decode, but you only have a PCI-e x1 slot and that really limits your options. The card you linked to on ebay is PCI-e x16. Be real careful about ebay because a lot of the cards listed under PCI-e x1 are actually x16.

Quite frankly, I don't think you're going to find a cheap x1 GPU (used or new). They're kind of a novelty compared to x16 cards, so they tend to be overpriced. Cards like the following would be much better than your current integrated GPU, but they're pricey:
[http://www.newegg.com/Product/Product.aspx?Item=9SIA4GS3RK2636](http://www.newegg.com/Product/Product.aspx?Item=9SIA4GS3RK2636)
[http://www.newegg.com/Product/Product.aspx?Item=9SIA6ZP3S61232](http://www.newegg.com/Product/Product.aspx?Item=9SIA6ZP3S61232)

As for the chipset/driver, I've used cards like the above (specifically, an 8400GS and RadeonHD 4550) with open source drivers with good results for video playback. You just need to install mesa-vdpau-drivers and vpdau-va-driver packages for video decode accel.

>  I remember reading somewhere not to mix intel chipset mobo (like mine) with a AMD chipset graphics card.
That's nonsense IMO, unless you're talking about a hybrid graphics laptop.

---

### Post by NS on 2016-02-18
Temujin -          
as before, your answers are informative and useful. Thank you, you helped me again.  Yes, i also noticed that PCI-e x1 cards are now high priced due to being novelties.  That is why i came up with the idea of using a x8 or x16 which are selling cheaper.  Do you know if there is a list of recommended / tested video cards for Ubuntu ? I would really like to run a driver that is non-generic and hence has been tested with Ubuntu, but not averse to a generic driver since my system is non-gaming and would not use much 3D graphics.

weatherman - 
thanks for your answers.  PCIe version 2.0 is backwards compatible, and problems might arise only in non-brand cards.  That is one reason i am planning to stick to  brand names (Nvidia or  Radeon).   If you don't like the idea of cutting out the Pci-e  x16 card  to fit into x1 slot,  then you can also cut away the plastic in the PCI-e slot, to make  room for the  x16 card.  There are videos and discussions on the net and many have done it.  Anyone who is daring enough to put together a barebones system, is likely  to be handy enough to accomplish this.  Regarding the power supply, you bring up a good point.   The  GPU  draws power through the  PCI-e  slot and would need more power for gaming applications.  In my case, the power needs are very little.  The power requirements of a GPU are not as high as stated by manufacturers.  For a sample discussion, see this thread : 
[http://www.tomshardware.com/forum/294297-33-geforce-8400-watt-system](http://www.tomshardware.com/forum/294297-33-geforce-8400-watt-system).  This card has peak power draw of 71 watts.  I would guess normal usage draw less than 50% of a gaming situation. My system is old and only has a 230W power supply.  I will update this thread after few weeks, once i complete this little project.  The idea is to shift atleast 20% of workload to GPU during video streaming.  HD plays fine in youtube, but only netflix has problems. I suspect this may have something to do with the fact that Adobe flash has gone crazy on CPU in recent years. Chrome uses HTML5, but i suspect that is not being taken advantage of under Ubuntu.  I am using  XUbuntu and hence resource usage is lower than Ubuntu.

Any suggestions regarding a low power GPU / card  is welcome.

---

### Post by kurt18947 on 2016-02-18
I'm not knowledgeable about most of the subjects being discussed here. I was running an Nvidia G210 on an AMD board/processor. It worked quite well using Nvidia's drivers but had suspend/resume issues when using the xorg/Nouveau drivers so if using an Nvidia card I'd recommend Nvidia drivers if possible. Nvidia cards older than 8400GS might not have current Nvidia drivers. If your current MoBo doesn't have a PCIe X16 slot I wonder if a PCI video card would be an improvement. When I was hunting a video card for a much older system I was surprised to find PCI cards using current video chip sets.

---

### Post by mörgæs on 2016-02-19
The link to the lshw output is dead. Better to post here using CODE tags than linking to an external page.

Anyway, you mention that your Prescott is 64 bit. Is your Buntu also 64 bit?

---

### Post by NS on 2016-02-19
Morgaes, 
    I did not think pastebin links expire (has been only 2 days i think).   Does pastebin links have any sort of expiration ?  I have few other messages in this forum where i have used such links, and wonder if those threads will become useless in item due to lack of information from pastebin.   Now, i tried to create another pastebin link, and i got an error messages that says    "*An error has occured.  Please notify  Adimins".    (*I will update those dead links, once pastebin is working again).  Meanwhile, the following post contains the same info....

Kurt - thanks for that info, i am taking my time in choosing a card that has drivers available.  I wonder which manufacturer is Linux/Ubuntu friendly and makes an effort to create drivers for this OS ?   I  have not bought graphics cards in over a decade, and i wonder about  Nvidia  &  AMD radeon  which seem to be the 2 top brands in video cards these days.  I also see Gigabyte, MSI and other names on ebay, that i do not recognize.   BTW,  PCI-e is better for video/graphics  than PCI, for a few   reasons.  They are cheap on ebay anyways, since i am not looking for  gaming quality.

Meanwhile, i want to add some info into this thread, that i found while browsing the net ......

[LIST]
[*]PCIe can draw a maximum of 75W power through the interface (and hence the need for seperate power connector on some graphics cards).  Power consumption of  GPUs  that i am considering (like Radeon HD 5450)  is 19w max, when  you are gaming.
[*] My Dell dimension 3100 uses 95 to 110W power during normal operation.  Thus, much of the 230W power supply is available still for my needs.
[*]Found a suggestion for  non-gaming  video card upgrades for general use and movies at  *upgradevideocards.com*
[*]Found a  hierarchy of video card performance,  at  *tomshardware.com *  which is very useful for  purchase decisions, when you are considering  older  video cards from Nvidia/AMD radeon/Intel.
[/LIST]

---

### Post by NS on 2016-02-19
Ouput  from  lshw   (same as the pastebin link posted previously about system)

```

ns@ns-Dell-Desktop:~/ubuntu-related$ sudo lshw -sanitize > lshw.txt
[sudo] password for ns: 
ns@ns-Dell-Desktop:~/ubuntu-related$ cat lshw.txt 
computer
    description: Mini Tower Computer
    product: Dell DV051
    vendor: Dell Inc.
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall32
    configuration: administrator_password=enabled boot=normal chassis=mini-tower power-on_password=enabled uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0JC474
       vendor: Dell Inc.
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A03
          date: 10/08/2005
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          slot: Microprocessor
          size: 2800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 800MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc pebs bts nopl pni dtes64 monitor ds_cpl cid cx16 xtpr lahf_lm
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 16KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 1MiB
             capacity: 1MiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: FFFFFFFFFFFFFFFF
             physical id: 0
             serial: [REMOVED]
             slot: DIMM_1
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: Kingston
             physical id: 1
             serial: [REMOVED]
             slot: DIMM_2
             size: 2GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: 82915G/P/GV/GL/PL/910GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:dff80000-dfffffff ioport:ecd8(size=8) memory:c0000000-cfffffff memory:dff40000-dff7ffff
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:26 memory:dff3c000-dff3ffff
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:1000(size=4096) memory:dfe00000-dfefffff ioport:d0000000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 memory:dfd00000-dfdfffff
        *-usb:0
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:ff80(size=32)
        *-usb:1
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:ff60(size=32)
        *-usb:2
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:3
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:ff20(size=32)
        *-usb:4
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:21 memory:d0200000-d02003ff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:d000(size=4096) memory:dfc00000-dfcfffff
           *-network
                description: Ethernet interface
                product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:03:08.0
                logical name: eth0
                version: 04
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=[REMOVED] latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
                resources: irq:20 memory:dfcff000-dfcfffff ioport:dcc0(size=64)
        *-isa
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-ide:1
             description: IDE interface
             product: 82801FR/FRW (ICH6R/ICH6RW) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:20 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fea0(size=16) memory:dff3bc00-dff3bfff
        *-serial
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0
             resources: irq:17 ioport:ece0(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: CDRW/DVD GCC4482
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: E107
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: HDS728080PLA380
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: A63A
             serial: [REMOVED]
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000e353b
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: [REMOVED]
                size: 243MiB
                capacity: 243MiB
                capabilities: primary bootable extended_attributes ext2 initialized
                configuration: filesystem=ext2 lastmountpoint=/boot modified=2016-02-08 18:59:49 mount.fstype=ext2 mount.options=rw,relatime mounted=2016-02-08 18:59:49 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 74GiB
                capacity: 74GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux LVM Physical Volume partition
                   physical id: 5
                   logical name: /dev/sda5
                   serial: [REMOVED]
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: multi lvm2
ns@ns-Dell-Desktop:~/ubuntu-related$



```

---

### Post by NS on 2016-02-19
After finding a list of  *Supported Hardware for Ubuntu*,  it  navigated from there to find that AMD supplies  Ubuntu drivers (starting 2014).  But Nvidia.com  provides drivers only  for  Linux.  There is a bunch of links in ubuntu site that provide  "opensource driver for nvidia".  But there is no mention  if  the  Linux drivers  provided by  Nvidia.com  have been tested  with  Ubuntu 14.04   and/or  15.04.  Any input regarding this will add to the comprehensiveness of this thread.   I have added info here, with all that i found in my research,  to help those who are trying to find  a cheap  video driver.

---

### Post by Yellow Pasque on 2016-02-20
So you're going to try cutting the end off the PCI-e x1 slot? It seems risky to me, though I guess it works in theory.

To maximize your chances of success, you need a card that has:
1. PCI-e 2.0 or older
2. Max TDP of 25W or less

On the AMD side, that limits you to RadeonHD 4350/4550 (or older). Actually, the 4350/4550 is a good card for Linux compatibility (using open-source radeon driver) and video acceleration. I happen to have a 4550 that I used for that purpose.
On the Nvidia side, the GT710 seems ideal and you can get new ones for about $35-45: [http://www.phoronix.com/scan.php?page=article&item=nvidia-geforce-gt710&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia-geforce-gt710&num=1)
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&IsNodeId=1&N=100007709%20601186533%20600007779](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&IsNodeId=1&N=100007709%20601186533%20600007779)


> **NS said:**
> After finding a list of  *Supported Hardware for Ubuntu*,  it navigated from there to find that AMD supplies  Ubuntu drivers (starting 2014).  But Nvidia.com  provides drivers only  for  Linux. 

It's a matter of semantics. Ubuntu uses Linux, and they package those drivers specifically for their distro for easy install/uninstall.

> There is a bunch of links in ubuntu site that provide  "opensource driver for nvidia".  But there is no mention  if  the  Linux drivers  provided by  Nvidia.com  have been tested  with  Ubuntu 14.04   and/or  15.04. 

It really depends on which card you get and specifically how old it is.

---

### Post by kurt18947 on 2016-02-20
I am currently using ATI/AMD HD4200 integrated graphics w/ Ubuntu's built-in drivers. It seems to work pretty well at least for non-gaming use. I did bring RAM up to 6 GB. because 512 MB. is dedicated to video use. A complaint with ATI/AMD is that they haven't maintained legacy drivers for older cards as well as Nvidia. I didn't find Nouveau/Xorg to work very well with a G210 Nivida card on an AMD/Gigabyte MoBo. The display worked but suspend/resume didn't. Nvidia proprietary drives found on the 'additional drivers' tab worked fine. You'll find that most video cards regardless of manufacturer use either AMD or Nividia chipsets.

---

### Post by Yellow Pasque on 2016-02-20
> A complaint with ATI/AMD is that they haven't maintained legacy drivers for older cards as well as Nvidia. 

They haven't maintained **proprietary** drivers as well as Nvidia. Given that the open source radeon drivers work well for olders cards and the proprietary AMD driver aren't always the best, it's not a big loss...

---

### Post by kurt18947 on 2016-02-22
> **Temüjin said:**
> They haven't maintained **proprietary** drivers as well as Nvidia. Given that the open source radeon drivers work well for olders cards and the proprietary AMD driver aren't always the best, it's not a big loss...

That is true. IME the open source Radeon drivers work much better than the open source Nvidia drivers.

---

### Post by NS on 2016-02-23
When i was searching around the internet regarding  driver support for  Radeon as well as Nvidia,  i got the same feeling as you guys have commented here.... AMD driver support was better than Nvidia (at least for older cards).  Heck,  Nvidia does not even test their drivers on Ubuntu.

Temujin - thanks again for your comments.  Yes, i understand that the core of Ubuntu is Debian which is derived from Linux.  But still, the fact is that AMD tests their drivers on Ubuntu whereas Nvidia does not.  I wound up finding a cheap  512MB Radeon HD 6350,  which is on par with HD 5450 performance, but lower than HD 6450. I do not know why you mentioned that the power consumption of  PCIe card has to be lower than 25W,  but  the card i ordered is low at 19W  TDP. Even a 25 to 30W card  (like  HD 6450) would have worked using my 230W  power supply (Reference:  An article from PC Magazine or PC-something that reviewed HD 6450 quoted power consumptions under gaming conditions).  BTW, if the hard drive crashes, i would move one of my spare HDD (pulled from a 2009 Macbook pro) and reinstall Ubuntu. All i want to do is stream Netflix in 720p HD - currently 1080 HD is supported only through  IE and safari, but not through firefox or chrome (which get 720p HD).

After much reading, my opinion was to find any card that shows up on ebay for sale at a decent price (from the 4000, 5000, or 6000 HD series of Radeon).  They would be more than enough for non-gaming system, perhaps even for playing old games which are not demanding.  Heck - passmark  rating for  HD 6450 was 281 (as of this posting), whereas the  Integrated Intel 915G/GV  video chip is rated   about  3 to 5 !!!  And if i was streaming netflix with the Intel integrated, then i would guess i would use my new HD 6350 for many years to come, as i keep upgrading Ubuntu.

Thanks to all of you guys, i will mark this thread Solved.

---

### Post by NS on 2016-02-24
I have marked the thread solved, but want to take this process to completion and report results of this project.  So, the HD 6350 has arrived.  When i installed  Ubuntu I do not remember if i separately installed the proprietary driver for the* integrated Intel 915G/GV  video.* How would i find out if my Ubuntu is currently running  generic  driver OR the Intel  specific one ?  If it is using a proprietary driver, then my understanding is that i can proceed as follows:
[LIST=1]
[*]uninistall  the  Intel  proprietary driver first.
[*]Then shut down the system
[*]Install the new HD 6350 radeon in PCI-e slot (after i cut down the slot to accomodate, in my case)
[*]Reboot the system
[*]Install the AMD proprietary driver (fglrx)  once the system boots up.  In my case, i wonder if this is really necessary and what i stand to gain from running the AMD driver  as opposed to using the generic  Ubuntu provided driver for this new video card.  I guess i can always compare the performance between the two drivers by watching the CPU load, but that seems like a overkill for  simple netflix  streaming.  Perhaps a gamer would try these things.
[/LIST]

---

