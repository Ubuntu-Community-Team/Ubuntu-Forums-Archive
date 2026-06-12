---
title: "Dell XPS 15 nvidia graphics problem"
date: 2010-11-09
forum: Hardware
---

### Post by Knorr on 2010-11-09
I've bought one of the new Dell XPS 15 laptops, and installed Ubuntu 10.10 64bit on it.

I'm having problems with the graphics. As long as I don't install the nvidia drivers all is good (except that I don't get accelerated graphics).

When I try to install nvidia-current X is not able to start. It says (EE) No device detected.

I can't figure out if the problem is the graphics card (Nvidia 420M) or the screen (Full HD screen 1080p that you can upgrade to on European Dell XPS 15)

I've attached the Xorg logs and dmesg from a boots with and without the nvidia driver loaded, and the xorg.conf file in use when nvidia is enabled.

I hope somebody might have some pointers to what could be the problem.

Regards

Jesper

---

### Post by Slicestrider on 2010-11-09
Hi,

I'm thinking of buying one of these laptops and was wanting to see if anyone had experienced any problems with the graphics.

I assume it's an core i5 machine version you bought. As far as I know the laptops use the nvidia Optimus system (in windows) that switches between graphics card when certain applications have been run. As far as I know the Linux support of this system is not straight forward (according to nvidia). I also asked the dell support people if there was an option in the BIOS to disable the switching graphics and choose either the intel or the nvidia one, but they said there was not. It still might be worth having a look though.

I know this has probably not been much help but I would like to know more about any possible solutions. I was thinking of buying the core i7 version which doesn't come with an integrated GPU so would have the nvidia chip visible to the system all the time!

---

### Post by Knorr on 2010-11-09
Yes it is an i5 one with integrated graphics. Might be the problem.

However, I just discovered that my nvidia card and the usb host controller share IRQ channel 16. But I don't know how to resolve this.

---

### Post by Slicestrider on 2010-11-09
Have you looked at the vga switcheroo stuff?

[http://en.gentoo-wiki.com/wiki/Vga_switcheroo](http://en.gentoo-wiki.com/wiki/Vga_switcheroo)

I know its a gentoo link but there ight be some stuff of use there.

Does the rest of the system work ok, sound, wifi etc?

---

### Post by Knorr on 2010-11-09
> **Slicestrider said:**
> Have you looked at the vga switcheroo stuff?

[http://en.gentoo-wiki.com/wiki/Vga_switcheroo](http://en.gentoo-wiki.com/wiki/Vga_switcheroo)

I know its a gentoo link but there ight be some stuff of use there.

Does the rest of the system work ok, sound, wifi etc?

As I see it, the link explains how to efficiently change between X settings. But I don't have a working configuration for my nvidia card, so I can't do that.

The rest of the system seems okay. Wifi, sound, touchpad etc works.

---

### Post by Knorr on 2010-11-10
If I specify the PCI bus the nvidia card is on:

```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"False"
        BusID   "PCI:2:0:0"
EndSection

```

I get the following from dmesg

```

[   18.099945] NVRM: failed to copy vbios to system memory.
[   18.102872] NVRM: RmInitAdapter failed! (0x30:0xffffffff:820)
[   18.102882] NVRM: rm_init_adapter(0) failed
[   18.223066] NVRM: failed to copy vbios to system memory.
[   18.226000] NVRM: RmInitAdapter failed! (0x30:0xffffffff:820)
[   18.226011] NVRM: rm_init_adapter(0) failed
[   18.275124] NVRM: failed to copy vbios to system memory.
[   18.278108] NVRM: RmInitAdapter failed! (0x30:0xffffffff:820)
[   18.278119] NVRM: rm_init_adapter(0) failed
[   18.326037] NVRM: failed to copy vbios to system memory.
[   18.329016] NVRM: RmInitAdapter failed! (0x30:0xffffffff:820)
[   18.329027] NVRM: rm_init_adapter(0) failed
[   18.377035] NVRM: failed to copy vbios to system memory.
[   18.379975] NVRM: RmInitAdapter failed! (0x30:0xffffffff:820)
[   18.379985] NVRM: rm_init_adapter(0) failed
[   18.428769] NVRM: failed to copy vbios to system memory.
[   18.431696] NVRM: RmInitAdapter failed! (0x30:0xffffffff:820)
[   18.431706] NVRM: rm_init_adapter(0) failed

```

---

### Post by psypher on 2010-11-10
Hi,

I have also been very interested in getting one of these but also weary of the optimus problem. From what i understand, have read up a little, there is now way to switch between discreet and accelerated graphics under the x server is it is today. The problem is not with the driver but with the fact that in windows there is an api which allows for this hardware switch. So nothing nividia can really do. x has to support it. 

I found this though:
[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)

This team is a group of hybrid graphics laptop owners and/or developers interested in getting it to work 100% under Linux.

Please subscribe to this team if you are new by clicking on the "Join Team" link at the right.

Use the mailing list [email]hybrid-graphics-linux@lists.launchpad.net[/email] to report on your testing.



So check it out and report back. How is the rest of the hardware supported? Wireless 100%?
And you probably cannot turn on compiz at all?

I want to order mine like tomorrow, they are such sweet looking laptops!
If the rest of the hardware is supported i think I'll get one and just hang in there and actively help these guys in getting it to work.

And I'm sure Wayland will support it, another reason for the switch. I think unity and wayland is gonna be awesome.


Edit:
I see that the integrated chip is Intel HD gfx, which as mention in this thread: [http://ubuntuforums.org/showthread.php?t=1465764](http://ubuntuforums.org/showthread.php?t=1465764) in 10.04/10 supports compiz. Can you please confirm? If compiz works and I can play HD movies, I'm really not fussed if I use the Nvidia card or not, leave that for gaming in windows. But will still try help get it to work.

Thanks

---

### Post by Knorr on 2010-11-11
> **psypher said:**
> Hi,

I found this though:
[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)

This team is a group of hybrid graphics laptop owners and/or developers interested in getting it to work 100% under Linux.



I will look into it.


> **psypher said:**
> 


So check it out and report back. How is the rest of the hardware supported? Wireless 100%?
And you probably cannot turn on compiz at all?



I'm not able to enable compiz, but I haven't looked that much into it. Wireless works out of the box (intel 6200 card). Haven't had a chance to test n though. Sound works, and is of a very good quality compared to other laptops I've used.

---

### Post by psypher on 2010-11-11
Can you do an lspci and post it here? Help you get that intel chip doing compiz.

---

### Post by Knorr on 2010-11-11
> **psypher said:**
> Can you do an lspci and post it here? Help you get that intel chip doing compiz.

```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
	Subsystem: Dell Device 046e
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: ac000000-adefffff
	Prefetchable memory behind bridge: 00000000ae000000-00000000bfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 046e
	Flags: bus master, fast devsel, latency 0, IRQ 50
	Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Dell Device 046e
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at f0906800 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
	Subsystem: Dell Device 046e
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f0907000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
	Subsystem: Dell Device 046e
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at f0900000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: a0000000-a01fffff
	Prefetchable memory behind bridge: 00000000a0200000-00000000a03fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: f0400000-f04fffff
	Prefetchable memory behind bridge: 00000000a0400000-00000000a05fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=06, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f0500000-f05fffff
	Prefetchable memory behind bridge: 00000000f0c00000-00000000f0dfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=08, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f0600000-f06fffff
	Prefetchable memory behind bridge: 00000000f0e00000-00000000f0ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: a0600000-a09fffff
	Prefetchable memory behind bridge: 00000000f0a00000-00000000f0afffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
	Subsystem: Dell Device 046e
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f0907400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
	Subsystem: Dell Device 046e
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06) (prog-if 01 [AHCI 1.0])
	Subsystem: Dell Device 046e
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 47
	I/O ports at 1840 [size=8]
	I/O ports at 1814 [size=4]
	I/O ports at 1818 [size=8]
	I/O ports at 1810 [size=4]
	I/O ports at 1820 [size=32]
	Memory at f0906000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
	Subsystem: Dell Device 046e
	Flags: medium devsel, IRQ 10
	Memory at f0907800 (64-bit, non-prefetchable) [size=256]
	I/O ports at 1860 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
	Subsystem: Dell Device 046e
	Flags: fast devsel, IRQ 18
	Memory at f0905000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: intel ips
	Kernel modules: intel_ips

02:00.0 VGA compatible controller: nVidia Corporation Device 0df1 (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 046e
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ac000000 (32-bit, non-prefetchable) [size=16M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Memory at ae000000 (64-bit, prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	[virtual] Expansion ROM at ad000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nouveau, nvidiafb

02:00.1 Audio device: nVidia Corporation Device 0bea (rev a1)
	Subsystem: Dell Device 046e
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at adefc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

04:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
	Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN
	Flags: bus master, fast devsel, latency 0, IRQ 49
	Memory at f0400000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

05:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03) (prog-if 30)
	Subsystem: Dell Device 046e
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f0500000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci-hcd

09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
	Subsystem: Dell Device 046e
	Flags: bus master, fast devsel, latency 0, IRQ 46
	I/O ports at 5000 [size=256]
	Memory at f0a04000 (64-bit, prefetchable) [size=4K]
	Memory at f0a00000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0


```

---

### Post by Knorr on 2010-11-11
Got compix running on the intel board now. It was a conflict with the nvidia drivers. Running nvidia-uninstall and reinstalling xserver-xorg-video-intel did the trick.

---

### Post by Slicestrider on 2010-11-11
> **Knorr said:**
> Got compix running on the intel board now. It was a conflict with the nvidia drivers. Running nvidia-uninstall and reinstalling xserver-xorg-video-intel did the trick.

Good work, so now you have graphics being accelerated by the intel chip? Whats is the performance like?

---

### Post by Knorr on 2010-11-11
> **Slicestrider said:**
> Good work, so now you have graphics being accelerated by the intel chip? Whats is the performance like?

Yes I have acceleration. Don't really know how to give a measure of performance, as I currently haven't got anything with heavy graphics installed. glxgears is able to keep up with the monitor refresh rate (60Hz).

---

### Post by Slicestrider on 2010-11-11
Have you got any HD video files you can throw at it?

---

### Post by Knorr on 2010-11-11
> **Slicestrider said:**
> Have you got any HD video files you can throw at it?

It plays back 1080p theora+vorbis without any hickups.

---

### Post by Knorr on 2010-11-12
It seems like there are some problem with ACPI. I can't get any meaningful temperatures, the battery is reported as not rechargeable with only 5Wh, and I'm not able to adjust screen brightness.

I will investigate further when I have the time.

---

### Post by psypher on 2010-11-16
> **Knorr said:**
> It plays back 1080p theora+vorbis without any hickups.

Could you try any H264 videos. ogg not nearly as intense as H264. Really shouold be fine, in this case all the decompression will happen on the CPU and not the GPU. If you had the NVidia working then we could try VDPAU. But a nice dualcore or higher CPU should play H264 without any issues.

---

### Post by Knorr on 2010-11-16
> **psypher said:**
> Could you try any H264 videos. ogg not nearly as intense as H264. Really shouold be fine, in this case all the decompression will happen on the CPU and not the GPU. If you had the NVidia working then we could try VDPAU. But a nice dualcore or higher CPU should play H264 without any issues.

No problems with H264. Test video [http://www.bigbuckbunny.org/index.php/download/](http://www.bigbuckbunny.org/index.php/download/)

---

### Post by psypher on 2010-11-16
Sold, I am literally ordering mine right now. Just can't decide between the 17 or 15" due to the 17" not having full HD. Yet I am leaning towards the 17" cos it has 4 USB and space for 2 HDD's and a better GFX card. What you think? I don't mind the size, I have a M6300 now and it's HUGE.

---

### Post by Knorr on 2010-11-16
> **psypher said:**
> Sold, I am literally ordering mine right now. Just can't decide between the 17 or 15" due to the 17" not having full HD. Yet I am leaning towards the 17" cos it has 4 USB and space for 2 HDD's and a better GFX card. What you think? I don't mind the size, I have a M6300 now and it's HUGE.

Personally, I wouldn't buy a laptop bigger than 15". And I don't play a lot of games, so no need for extreme graphics, so I guess I'm too biased.

But I must say this screen is awesome. Not just for the resolution, but it has truly amazing colors.

---

### Post by panchicore on 2011-01-02
> **Knorr said:**
> Got compix running on the intel board now. It was a conflict with the nvidia drivers. Running nvidia-uninstall and reinstalling xserver-xorg-video-intel did the trick.

friend, can you make a guide to uninstall nvidia and reinstall xorg intel? 

I dont have nvidia-uninstall:

~$ sudo nvidia- [tab]
nvidia-bug-report.sh  nvidia-detector       nvidia-settings       nvidia-smi            nvidia-xconfig 

thankyou very much!

---

### Post by whitethunder922 on 2011-03-16
> **panchicore said:**
> friend, can you make a guide to uninstall nvidia and reinstall xorg intel? 

I dont have nvidia-uninstall:

~$ sudo nvidia- [tab]
nvidia-bug-report.sh  nvidia-detector       nvidia-settings       nvidia-smi            nvidia-xconfig 

thankyou very much!

Just uninstall anything nvidia-* related and rename your /etc/X11/xorg.conf file. Then make sure you've installed xorg-xserver-video-intel and reboot.

---

### Post by jsonder on 2011-04-16
I'm using a Dell XPS laptop with:

Intel(R) HD Graphics [Display adapter]
NVIDIA GeForce GT 420M [Display adapter]
Generic PnP Monitor (15.3"vis)

(belarc info above)  

When I installed the beta2 version of Natty, I had Unity.

When I booted into Natty today, I was told that my hardware was inadequate for Unity, and I got the Gnome desktop.

I know that the higher quality video upon demand setup is awkward, but this really is a glitch that needs to be resolved if Unity & Natty are accepted.  I can always boot into mint debian, so it is no biggie for me, but I do feel an obligation to report a problem which will keep some folks from using Ubutu.  Our LUG has recommended Ubuntu for several years so I have a strong support role with Ubuntu installations.

---

### Post by dinostabOMG on 2011-05-14
> **Knorr said:**
> Got compix running on the intel board now. It was a conflict with the nvidia drivers. Running nvidia-uninstall and reinstalling xserver-xorg-video-intel did the trick.

Kind of a noob here, can you expound upon what I have to do to do this? What commands to use or where to go? I would like to get compiz working with the intel card if possible. Fresh install of 11.04 here.

---

