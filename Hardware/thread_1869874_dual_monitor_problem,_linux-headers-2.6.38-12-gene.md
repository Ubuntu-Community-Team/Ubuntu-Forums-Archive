---
title: "dual monitor problem, linux-headers-2.6.38-12-generic 2.6.38-12.51"
date: 2011-10-26
forum: Hardware
---

### Post by magicsowon on 2011-10-26
I have Ubuntu 11.04 on my T520 Thinkpad laptop. After updating the kernel to
linux-headers-2.6.38-12-generic 2.6.38-12.51, I tried to connect my computer to a second monitor. The screen would simply not work, so I reverted to mirrored monitors, but lost the high resolution. The temporary fix was
xrandr --output VGA1 --auto --output LVDS1 --off

This worked fine on one external monitor, but not on the other. In the end I reverted to the previous version of the kernel. This works fine. 

I still don't know what is the problem with this new kernel. 

This is what I get if I type lspci:

[SIZE="2"]```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 6 Series Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 (rev 34)
0d:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 05)
0d:00.3 FireWire (IEEE 1394): Ricoh Co Ltd FireWire Host Controller (rev 04)

```[/SIZE]

---

### Post by magicsowon on 2011-10-28
On the monitor at work I have to use 
linux-headers-2.6.38-12-generic

at home, 
linux-headers-2.6.38-11-generic

I would be happy if someone could give me a hint how can I fix this. Or do I have to wait for the next kernel?

---

### Post by Atomic-Fanboy on 2011-10-28
Ugh... I know. My laptop screen does not work with 2.6.38 either.

---

### Post by magicsowon on 2011-10-28
The solution I found is to install the 2.6.39 kernel. That seems to work for now, or at least until ubuntu developers come up with a new "update".

```
sudo dpkg -i linux-headers-2.6.39-02063904_2.6.39-02063904.201108040905_all.deb

sudo dpkg -i linux-headers-2.6.39-02063904-generic_2.6.39-02063904.201108040905_amd64.deb

sudo dpkg -i linux-image-2.6.39-02063904-generic_2.6.39-02063904.201108040905_amd64.deb
```

Since they were deleted from the repository (I wish I knew why), I had to download them from

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/")

---

### Post by magicsowon on 2011-11-02
Current fix for my monitor at work:

1. Turn on the machine with the monitor hooked up.
2. Login
3. press FN + F7 once -- both monitors have maximum resolution
4. press again -- only the external monitor is active

If this didn't work

xrandr --output VGA1 --auto LSVD1 --auto
turns both monitors on at maximum resolution

xrandr --output VGA1 --auto LSVD1 --off
turns off the laptop monitor.
In my case, it was important in which order I do things, otherwise the system would freeze. If this goes on, I'll go back to debian.

---

