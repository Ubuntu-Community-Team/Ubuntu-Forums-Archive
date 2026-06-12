---
title: "Karmic's Crazy CPU Usage!?"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by higashi on 2009-11-08
I've only been using karmic for a while, and i've noticed that it has been lagging a lot. i looked at the system monitor and noticed that my CPU usage is usually around 90%, with just firefox running.

I'm assuming this issue has to do with firefox itself. How can i lower the CPU usage?

---

### Post by hansdown on 2009-11-08
Hi higashi.

I noticed firefox causes high cpu usage with Karmic as well.

I've gone back to Jaunty for now.

---

### Post by ratcheer on 2009-11-08
I am using FF 3.5.5 and I just looked. My CPU usage is maxing to about 9%, usually much less.

Tim

PS - when I posted the above, it spiked to around 80%, momentarily.

---

### Post by paxmark1 on 2009-11-08
many people swear Opera is faster and less resource hungry.  
I use it more than Firefox due to personal preference.

What does top (or if you have it installed htop) or the system manager appp say are the cpu intensive processes?

---

### Post by chris7777 on 2009-11-08
Firefox bogs down my laptop too. 

I have had problems with it on and off, in xp, but trying to switch to ubuntu, It is becoming unusable. 

Should I roll back to Jaunty? and how.

---

### Post by henryfranz2005 on 2009-11-08
firefox uses more ram than other internet browsers I think..

---

### Post by Arup on 2009-11-08
> **paxmark1 said:**
> many people swear Opera is faster and less resource hungry.  
I use it more than Firefox due to personal preference.

What does top (or if you have it installed htop) or the system manager appp say are the cpu intensive processes?

I agree, Opera 10 runs far more smoothly and even after whole day of heavy surfing, it never slows down or hog immense resources.

---

### Post by End Us3r on 2009-11-08
I'm running Chromium via Ubuntu Tweak. No CPU usage issues.

---

### Post by higashi on 2009-11-09
i have these problems even when firefox is closed. For example, Miro. (keep in mind, i used to run firefox and miro with absolutely no problems or lag while using jaunty)

---

### Post by scottuss on 2009-11-10
> **End Us3r said:**
> I'm running Chromium via Ubuntu Tweak. No CPU usage issues.

I'm also using Chromium and it's a great browser. Much faster to load than Firefox and handles memory much more efficiently. Not to mention JavaScript execution seems much snappier.

---

### Post by higashi on 2009-11-24
Bump.  It's not only firefox that's acting up. im not looking for alternatives, i just want to know how to get my cpu usage back to the way it was with jaunty ):

---

### Post by Arup on 2009-11-24
Can you tell me what video drivers you are using?

---

### Post by Razmear on 2009-11-24
> **higashi said:**
> Bump.  It's not only firefox that's acting up. im not looking for alternatives, i just want to know how to get my cpu usage back to the way it was with jaunty ):

Before rolling back to 9.04 try using the Xubuntu desktop instead of Gnome. I'm now running Opera on Xubuntu and things are much faster than FF on stock 9.10 

Installation is simple and non-destructive: 
```

Install Xubuntu from Ubuntu

If you have an existing Ubuntu, Kubuntu, or Edubuntu 
installation, it is possible to install Xubuntu and retain 
your current installation. To do so, just go into Synaptic 
(or Adept if you use Kubuntu) and install the xubuntu-desktop package. 
Next time you login, you can choose Xfce4 from the Session menu 
on the login screen.


```

eb

---

### Post by higashi on 2009-11-26
i typed lspci -v  to get my drivers, here's the output:

```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
	Subsystem: Dell Device 0151
	Flags: bus master, fast devsel, latency 0
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
	Subsystem: Dell Device 0151
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at ed98 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
	Flags: fast devsel
	Memory at fecf0000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
	Subsystem: Dell Device 0151
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff80 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
	Subsystem: Dell Device 0151
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at ff60 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
	Subsystem: Dell Device 0151
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ff40 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
	Subsystem: Dell Device 0151
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff20 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Dell Device 0151
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fea00000-feafffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Device 0151
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Memory at feb7fc00 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Dell Device 0151
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at fe00 [size=8]
	I/O ports at fe10 [size=4]
	I/O ports at fe20 [size=8]
	I/O ports at fe30 [size=4]
	I/O ports at fea0 [size=16]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
	Subsystem: Dell Device 0151
	Flags: medium devsel, IRQ 3
	I/O ports at eda0 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Dell Device 0151
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ee00 [size=256]
	I/O ports at edc0 [size=64]
	Memory at feb7fa00 (32-bit, non-prefetchable) [size=512]
	Memory at feb7f900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
	Subsystem: Dell Device 0151
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at feae0000 (32-bit, non-prefetchable) [size=128K]
	I/O ports at df40 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: e1000
	Kernel modules: e1000

```

---

### Post by higashi on 2009-11-26
Okay, i re-installed and everything's fine now. The only time the CPU usage goes crazy now is when i open the System Monitor... which i find ironic that the thing checking the CPU usage uses up the most.. which renders it pretty inaccurate.

---

### Post by SuperDrive on 2009-11-27
> **higashi said:**
> Okay, i re-installed and everything's fine now. The only time the CPU usage goes crazy now is when i open the System Monitor... which i find ironic that the thing checking the CPU usage uses up the most.. which renders it pretty inaccurate.

I have the same problem, system monitor takes the most of cpu usage (sometimes up to 50%) while firefox takes about 16-22%.

---

### Post by higashi on 2009-11-27
if you want to know your cpu usage without having to open System Monitor, just open up a terminal and type > top and press enter. when you're done, just close the terminal or press q

---

