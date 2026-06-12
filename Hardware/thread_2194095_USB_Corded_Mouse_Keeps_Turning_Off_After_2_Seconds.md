---
title: "USB Corded Mouse Keeps Turning Off After 2 Seconds"
date: 2013-12-16
forum: Hardware
---

### Post by wewantutopia on 2013-12-16
Hello

I have a Samsung Series 7 NP700Z5A-S0AUS laptop and my corded USB mouse keeps turning off every 2 seconds of non-use.

I've tried:
```
sudo powernap-action --disable usb_autosuspend
```

It has not solved the problem.

If I try it again it says:
```
INFO: [usb_autosuspend] is already disabled, skipping...
```

Does anyone have any other ideas?  This is driving me crazy!!

Thanks!

---

### Post by wewantutopia on 2013-12-19
Bump.

Anyone?

---

### Post by tgalati4 on 2013-12-19
Install *acpitool* and post the output of:

```
sudo apt-get install acpitool
acpitool -w
lsusb
lspci
```

Do you get the same behavior from all USB ports?

---

### Post by wewantutopia on 2013-12-19
Thanks!

Here is acpitool -w
```
   Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. P0P1      S4    *disabled
  2. GLAN      S4    *disabled
  3. HDEF      S4    *disabled  pci:0000:00:1b.0
  4. RP01      S4    *disabled  pci:0000:00:1c.0
  5. PXSX      S4    *disabled  pci:0000:02:00.0
  6. RP02      S4    *disabled
  7. PXSX      S4    *disabled
  8. RP03      S4    *disabled
  9. PXSX      S4    *disabled
  10. RP04      S4    *disabled  pci:0000:00:1c.3
  11. PXSX      S4    *disabled  pci:0000:03:00.0
  12. RP06      S4    *disabled
  13. PXSX      S4    *disabled
  14. RP07      S4    *disabled
  15. PXSX      S4    *disabled
  16. RP08      S4    *disabled
  17. PXSX      S4    *disabled
  18. PEG0      S4    *disabled  pci:0000:00:01.0
  19. PEGP      S4    *disabled  pci:0000:01:00.0
  20. PEGA      S4    *disabled
  21. PEG1      S4    *disabled
  22. PEG2      S4    *disabled
  23. PEG3      S4    *disabled
  24. PWRB      S4    *enabled 


```

Here is lsusb
```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 2232:1018  
Bus 002 Device 006: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 004: ID 8086:0189 Intel Corp.
```

Here is lspci
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6630M/6650M/6750M/7670M/7690M]
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6230 [Rainbow Peak] (rev 34)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
04:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller

```

This happens whether plugged in or using battery.  Also, I'm trying a different, now wireless mouse, with the same outcome.

Thanks!!!

---

### Post by tgalati4 on 2013-12-19
So your system has only one device that has power to it when it is asleep (state S4) and the disks are spun down.  That would be the power button (labeled PWRB).  Every other device is "disabled" during state S4.  Before we mess around with the sleep state of these devices, let us check the BIOS.

Reboot your computer and go into BIOS--F2, Delete, Tab, F12, whatever key you need to get into BIOS.

Look around for a tab or page labeled "Power Management".  Check the settings for "Support Legacy USB devices".  And "Allow USB device to Wake from Sleep".  Make sure both of them are checked (turned on).  Reboot and see if that changes the behavior.

---

### Post by wewantutopia on 2013-12-19
Thanks for the reply.

If I remember correctly, there is, by design, only one USB port with power when the computer is sleeping/off. In fact it is the only one of 3 that has a little power lightning bolt above it (the one that charges my phone when the computer is off)

Just to be sure, I restarted and checked the bios and I had already enabled enabled all things USB.

In the time between posts I added usbcore.autosuspend=-1 after quiet splash in grub using grub customizer.  Checking /sys/module/usbcore/parameters/autosuspend the value now says -1 when before it said 2.

The mouse behavior is the same....

---

### Post by tgalati4 on 2013-12-19
I would check the BIOS version on your machine and compare it to the latest from Samsung.  It's possible that it is a bug and there may be an update for it.

A quick google search gives:  [http://unix.stackexchange.com/questions/91027/how-to-disable-usb-autosuspend-on-kernel-3-7-10-or-above](http://unix.stackexchange.com/questions/91027/how-to-disable-usb-autosuspend-on-kernel-3-7-10-or-above)

Try different values:  0 and 1.  If you have a USB hub, use that and see if the mouse stays awake.

According to your *acpitool* output, all ports are asleep (no power) when in state S4 (asleep).  Verify that your phone is charging when you use the "live" USB port when your machine is put to sleep under linux.  If not, then try turning it on using the -W parameter with *acpitool*.

---

### Post by wewantutopia on 2013-12-20
Well, just for the heck of it I installed [Solaar]("http://www.webupd8.org/2013/07/pair-unpair-logitech-unifying-devices.html") last night.  Without altering any of the settings within the program, the mouse now works perfectly.  Very odd.

For the record, the mouse is a Logitech M325.

Thanks for all your help!!  I'll now mark this solved.

---

