---
title: "Dell E6400, docking station, and external displays (12.04)"
date: 2012-05-09
forum: Hardware
---

### Post by richardgaywood on 2012-05-09
Hi there!

Things went smoothly with my Ubuntu install on this slightly ageing Dell until I dropped it into the docking station, which has two monitors connected via DVI. I want it to do what Windows does by default -- turn off the built-in panel and drive the two external screens (I don't think the GPU can drive triplehead). But instead, the two screens stay off. They aren't listed in the "Displays" settings panel at all. 

Stuff I've tried:

1) Both versions of the nVidia binary driver offered to me by the "Additional drivers" control panel.

2) Only plugging one monitor into the docking station at once (no change).

3) Plugging a monitor directly into the VGA port on the laptop -- it wouldn't fire up or appear in Displays.

4) Testing the docking station -- it works fine in Windows, and the Ethernet and USB ports work fine with Ubuntu.

5) Various combinations of the above whilst hitting Fn-F8 (Dell's "toggle external screen" button).

6) Nosing through the laptop's BIOS for anything that looks relevant (nothing did).

Back when I last used Linux seriously on the desktop (2005 or so), I'd be hacking X11 config files but my understanding was that this should be much more dynamic now. Not sure what I should try next though. Any advice would be welcomed!


Hardware info:

It's a Dell Latitude E6400 with a Quadro NVS 160M GPU (G98M core). I have a Dell E-port Plus docking station. 

lspci output:

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation G98M [Quadro NVS 160M] (rev a1)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

```

xrandr output with docking station and both monitors connected:

```
richg@kalee:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1440x900       50.0     51.0     52.0* 
   1360x768       53.0     54.0  
   1152x864       55.0     56.0     57.0     58.0  
   1024x768       59.0     60.0     61.0     62.0     63.0  
   960x600        64.0  
   960x540        65.0  
   896x672        66.0  
   840x525        67.0     68.0     69.0     70.0     71.0  
   832x624        72.0  
   800x600        73.0     74.0     75.0     76.0     77.0     78.0     79.0     80.0     81.0  
   800x512        82.0  
   720x450        83.0  
   720x400        84.0  
   700x525        85.0     86.0     87.0     88.0  
   680x384        89.0     90.0  
   640x512        91.0     92.0     93.0  
   640x480        94.0     95.0     96.0     97.0     98.0     99.0  
   640x400       100.0  
   640x350       101.0  
   576x432       102.0    103.0    104.0    105.0    106.0    107.0    108.0  
   512x384       109.0    110.0    111.0    112.0    113.0  
   416x312       114.0  
   400x300       115.0    116.0    117.0    118.0    119.0  
   360x200       120.0  
   320x240       121.0    122.0    123.0    124.0  
   320x200       125.0  
   320x175       126.0  

```

---

### Post by richardgaywood on 2012-05-09
One thing I hadn't tried was nouveau. Trying that out now.

The good: both my screens work!

The bad: I've had one hard crash in the first minute (when re-arranging displays, I ended up with random chunks of video memory all over the display -- flashing squares etc) and it's visibly slower for 2D work. Even dragging windows around can cause screen tearing etc. Overall, it's not encouraging.

Advice on working with nVidia's driver would be gratefully received ;)

Edit -- on the performance note, I'm seeing a load average of 1.2 with nothing loaded except a single tab in Chrome and a terminal running top. 25-30% of CPU time is going to compiz. Is this because nouveau isn't as accelerated?

---

### Post by richardgaywood on 2012-05-10
Going to keep talking to myself to help future Googlenauts...

Switched back to the nVidia binary driver and added
```
Option "Twinview" "1"
```
to my /etc/X11/xorg.conf. Rebooted and the system brought up one of the external monitors.

Ran the nvidia-settings app, which allowed me to configure the screens how I wanted (laptop screen off, both external monitors enabled). Told that to save its changes to xorg.conf (it wrote a ton of stuff).

Had a period where Unity wanted to put the launcher strip on the left hand side of my right hand screen (i.e. in the middle of the screen overall), but telling nvidia-settings to make the leftmost monitor the "primary X display" and then rebooting again fixed that.

Next problem: no dynamic switching. When I lift the laptop out of the docking station, the internal panel doesn't switch on. There's talk of dynamic switching with hotkeys in the nVidia docs, but no mention of how to configure it. Hammering Fn-F8 (the Dell's nominated button for this) doesn't do anything.

My investigations continue...

---

### Post by blurredveg on 2012-05-16
Keep trying, we're googlenauts are listening! :)  Got a single monitor attached to a docking station for a Latitude E6410 and would also like the dynamic display change ala Windows...  Thanks for your struggles...

---

### Post by rootusr on 2012-05-21
Yep, I'm having the same issues on the same type of display.  Previously I had to add the following to my grub config file to get the hotkey to work:

GRUB_CMDLINE_LINUX="nouveau.modeset=0 acpi_sleep=nonvs acpi_osi=\\\"!Windows 2009\\\""

but that doesn't seem to work anymore.

---

### Post by MSPdwalt on 2012-07-23
Any luck?  I'm having the same issue. Dock with 1 external monitor, When docked I want it to prefer the external.

With 10.04 this worked until I had to use a 3rd party repo to get a more recent NVIDIA driver to solve a different issue.  I'm running the the NVIDIA package from the standard repos on this build.

---

### Post by markbeverley on 2012-09-10
Hi all,

I'm having the same issue with dynamic switching. When I boot my Dell E6410 laptop whilst docked it will default to the laptop screen. I can configure two external monitors using the Nvidia software but when I undock the laptop screen stays blank.

Any progress on this appreciated.

Mark

---

### Post by static_k on 2012-11-14
> **richardgaywood said:**
> One thing I hadn't tried was nouveau. Trying that out now.

The good: both my screens work!

The bad: I've had one hard crash in the first minute (when re-arranging displays, I ended up with random chunks of video memory all over the display -- flashing squares etc) and it's visibly slower for 2D work. Even dragging windows around can cause screen tearing etc. Overall, it's not encouraging.

Advice on working with nVidia's driver would be gratefully received ;)

Edit -- on the performance note, I'm seeing a load average of 1.2 with nothing loaded except a single tab in Chrome and a terminal running top. 25-30% of CPU time is going to compiz. Is this because nouveau isn't as accelerated?

Do you see the same performance issue when using the nvidia driver? I have the 2 monitors hooked to the dvi ports of my docking station and am using twinview. I notice that system performance gradually gets worse when I'm in the docking station. I never get the issue when I work out of the docking station.

---

