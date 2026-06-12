---
title: "Samsung Laptop - Sound and Power Issues"
date: 2013-12-12
forum: Hardware
---

### Post by mookster1 on 2013-12-12
Hello all

I recently installed Xubuntu 13.10 on my Samsung NP350V5C-S08AU laptop, and all went incredibly smoothly (this is one of the models of Samsung notebook that may or may not have UEFI issues).  Apart from a couple of things.  First, the power consumption has gone through the roof.  When running Windows 8, through normal use I'd be lucky to top out at 10 watts.  On Xubuntu, I was using over double that, with a maximum power consumption reported as 27 watts.  I've also noticed that, while the sound works, the hotkeys (Fn+F7 and Fn+F8) for changing the volume are dodgy.  The brightness hotkeys work brilliantly, however a single press of one of the volume hotkeys sets the volume to maximum (or minimum) and appears to stop the keyboard from working.  The touchpad is still usable then, so I tried navigating to the PulseAudio volume control applet and changing the volume with the mouse, but the volume selector kept returning to maximum (or minimum.)  This is usually fixed by suspending the laptop and logging in again.  Has anyone else experienced this issue before?

This is the output of inxi -Fzx:

```
System:    Host: DeepThought Kernel: 3.11.0-14-generic x86_64 (64 bit, gcc: 4.8.1) 
           Desktop: Xfce 4.10.2 (Gtk 2.24.20) Distro: Ubuntu 13.10
Machine:   System: SAMSUNG product: 350V5C/351V5C/3540VC/3440VC version: P09ABE.012.CP
           Mobo: SAMSUNG model: NP350V5C-S08AU version: BOARD 00 Bios: American Megatrends version: P09ABE date: 07/04/2013
CPU:       Dual core Intel Core i5-3210M CPU (-HT-MCP-) cache: 3072 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9977.48 
           Clock Speeds: 1: 1200.00 MHz 2: 1200.00 MHz 3: 1200.00 MHz 4: 1200.00 MHz
Graphics:  Card-1: Intel 3rd Gen Core processor Graphics Controller bus-ID: 00:02.0 
           Card-2: Advanced Micro Devices [AMD/ATI] Thames [Radeon HD 7500M/7600M Series] bus-ID: 01:00.0 
           X.Org: 1.14.3 drivers: intel (unloaded: fbdev,vesa) Resolution: 1366x768@60.1hz 
           GLX Renderer: N/A GLX Version: N/A Direct Rendering: N/A
Audio:     Card: Intel 7 Series/C210 Series Family High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0 
           Sound: Advanced Linux Sound Architecture ver: k3.11.0-14-generic
Network:   Card-1: Qualcomm Atheros AR9485 Wireless Network Adapter driver: ath9k bus-ID: 03:00.0
           IF: wlan0 state: up mac: <filter>
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
           driver: r8169 ver: 2.3LK-NAPI port: 2000 bus-ID: 02:00.0
           IF: eth0 state: down mac: <filter>
           Card-3: Atheros usb-ID: 001-006
           IF: N/A state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 750.2GB (0.7% used) 1: id: /dev/sda model: ST750LM022_HN size: 750.2GB 
Partition: ID: / size: 60G used: 5.0G (9%) fs: ext4 ID: swap-1 size: 4.10GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 63.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 173 Uptime: 57 min Memory: 685.9/3845.5MB Runlevel: 2 Gcc sys: 4.8.1 
           Client: Shell (bash 4.2.45) inxi: 1.9.12
```

I've also installed powertop, and the sound device appears to consistently be at 100% usage, so I suspect the two issues may be linked somehow (dodgy driver, perhaps?)

If anyone has any suggestions as to how I can go about sorting these issues out, I'd greatly appreciate it :)

---

### Post by thelionroars1337 on 2013-12-13
The high power usage will be the hybrid graphics - your dedicated AMD card will be using full power while the system is using the integrated Intel graphics for the display.

If you don't object to using the proprietary AMD driver, installing this is the easiest fix. You will be able to choose between the dedicated and integrated graphics using a GUI settings manager, and the change will take place after a reboot. This will also offer you the best performance when using the dedicated graphics. This will properly turn off the dedicated graphics card when not in use, and I suspect power will be better managed when using the dedicated graphics also. There may be an 'Additional Drivers' application in your menu (sorry I'm unfamiliar with Xubuntu), which will be the easiest way to install this. Further installation options are discussed here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

If you have an ideological objection to using the proprietary driver, you can still get your power usage back to normal by using vga_switcheroo. This is a little more complex to set up and you will not get as good performance out of your dedicated graphics. Further information is available here: [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

I also have a Samsung laptop and my sound keys also misbehave as you've described. I've learnt to live with it, and use the software sound control on my desktop panel instead.

---

