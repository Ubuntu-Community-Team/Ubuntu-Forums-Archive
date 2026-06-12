---
title: "PLEASE HELP!!! The Graphic is not working in my Toshiba"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by stalinheredia on 2007-09-05
Hey guys

I just installed Ubuntu feisty 7.04 on my laptop Toshiba satellite A215-S4757 and basically the installation went through successfully, but when I'm booting the system the X server crashes. I'm getting this error messages "Failed to start the X server your graphical interface. It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"......and then takes me to the shell.....Based on the lspci output I have a VGA: ATI Technologies Inc Unknown device 791f....PLEASE somebody help me to fix this...I don't want to go back to the virus (windows)...Thanks in advance........

---

### Post by w4ett on 2007-09-05
From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "vesa" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This SHOULD get you to a GUI desktop

Good Luck

---

### Post by stalinheredia on 2007-09-07
Thanx so much W4ETT for your response. I tried what you suggested but it didn't work. I actually tried every single driver and none of them worked.....PLEASE somebody help me with this...

---

### Post by w4ett on 2007-09-07
> **stalinheredia said:**
> Thanx so much W4ETT for your response. I tried what you suggested but it didn't work. I actually tried every single driver and none of them worked.....PLEASE somebody help me with this...

From the terminal (or CLI) type:

```
lspci
```

and let's see what chipset you are using.( we need the copy and paste) if you can do it.

---

### Post by rustybronco on 2007-09-07
remember the SPACEBAR selects the option (i.e. 1024x768 )
kb8hsd...

---

### Post by stalinheredia on 2007-09-14
00:00.0 Host bridge: ATI Technologies Inc Unknown device 7910
00:01.0 PCI bridge: ATI Technologies Inc Unknown device 7912
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc Unknown device 7916
00:07.0 PCI bridge: ATI Technologies Inc Unknown device 7917
00:12.0 IDE interface: ATI Technologies Inc Unknown device 4380
00:13.0 USB Controller: ATI Technologies Inc Unknown device 4387
00:13.1 USB Controller: ATI Technologies Inc Unknown device 4388
00:13.2 USB Controller: ATI Technologies Inc Unknown device 4389
00:13.3 USB Controller: ATI Technologies Inc Unknown device 438a
00:13.4 USB Controller: ATI Technologies Inc Unknown device 438b
00:13.5 USB Controller: ATI Technologies Inc Unknown device 4386
00:14.0 SMBus: ATI Technologies Inc Unknown device 4385 (rev 14)
00:14.1 IDE interface: ATI Technologies Inc Unknown device 438c
00:14.2 Audio device: ATI Technologies Inc Unknown device 4383
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 438d
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4384
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Unknown device 791f
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8136 (rev 01)
14:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
1a:04.0 CardBus bridge: Texas Instruments Unknown device 8039
1a:04.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
1a:04.2 Mass storage controller: Texas Instruments Unknown device 803b
1a:04.3 Class 0805: Texas Instruments Unknown device 803c

---

