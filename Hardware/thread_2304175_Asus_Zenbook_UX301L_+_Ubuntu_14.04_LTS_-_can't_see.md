---
title: "Asus Zenbook UX301L + Ubuntu 14.04 LTS - can't see bluetooth adapter"
date: 2015-11-24
forum: Hardware
---

### Post by stefan_bahrens on 2015-11-24
Running Ubuntu 14.04 LTS on this zenbook seems to work apart from screen brightness and bluetooth. Strangely the system can't see the bluetooth adapter. If I run lspci and lsusb neither of them pick up any device called 'bluetooth'. So, I don't even know what sort of bluetooth adapter its got. If anyone can cast any light on this I'd be very grateful.

---

### Post by stefan_bahrens on 2015-11-25
This looks a bit more promising. If I do this -
dmesg | grep Blue
then I get this -

[    8.880099] Bluetooth: Core ver 2.19
[    8.880114] Bluetooth: HCI device and connection manager initialized
[    8.880120] Bluetooth: HCI socket layer initialized
[    8.880122] Bluetooth: L2CAP socket layer initialized
[    8.880306] Bluetooth: SCO socket layer initialized
[    8.903457] Bluetooth: hci0: read Intel version: 370810011003110e00
[    9.278340] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.3.11.e.bseq
[    9.341722] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   11.513372] Bluetooth: RFCOMM TTY layer initialized
[   11.513381] Bluetooth: RFCOMM socket layer initialized
[   11.513384] Bluetooth: RFCOMM ver 1.11
[   11.623971] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   11.623974] Bluetooth: BNEP filters: protocol multicast
[   11.623980] Bluetooth: BNEP socket layer initialized

Is this good? Does it mean that Ubuntu can see my bluetooth adapter? What sort
is it? Is there a way I can get it working? Thanks for any help.

---

### Post by stefan_bahrens on 2015-11-25
Opinion seems to be that the output above doesn't prove much.
Here is the output of lsusb

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 03eb:8a03 Atmel Corp. 
Bus 001 Device 003: ID 1bcf:2987 Sunplus Innovation Technology Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and here is the output of lspci

00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 09)
00:04.0 Signal processing controller: Intel Corporation Device 0a03 (rev 09)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Wireless 7260 (rev 6b)

Does any of this look like a bluetooth adapter?
Thanks for any help.

---

### Post by boyi on 2016-06-15
> **stefan_bahrens said:**
> Running Ubuntu 14.04 LTS on this zenbook seems to work apart from screen brightness and bluetooth. Strangely the system can't see the bluetooth adapter. If I run lspci and lsusb neither of them pick up any device called 'bluetooth'. So, I don't even know what sort of bluetooth adapter its got. If anyone can cast any light on this I'd be very grateful.

Do you manage to solve your problem? I am using exactly the same model of yours and encountered the same problem with bluetooth. I had this problem earlier, when I use kernel 3.13. Then, when I update to kernel 4.6.2 the problem still persists. 

I manage to solve my problem by following the the instruction in [http://askubuntu.com/questions/466158/ubuntu-14-04-bluetooth-adapter-not-found](http://askubuntu.com/questions/466158/ubuntu-14-04-bluetooth-adapter-not-found). > [COLOR=#111111][FONT=Ubuntu]Try disabling USB 3.0 at the BIOS, and then try again. In the BIOS, the option will probably say something about "xHCI", which is another way of calling USB 3.0[/FONT][/COLOR]

Hope you able to get to your bluetooth.

Regards.

---

### Post by jeremy31 on 2016-06-15
boyi

This is the first I have heard of xhci causing issues with Intel bluetooth.  This should be reported as a bug, there is a guide [http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)
I would file against package linux

---

### Post by him610 on 2016-06-15
FWIW, depending on your wireless card, you may have a bluetooth module built into the wireless card.

---

### Post by weatherman2 on 2016-06-15
Yes, bluetooth is built into the Intel 7260 card mentioned above.  I installed this card into my Acer laptop.  Bluetooth works (though I had to tape a pin on the card to prevent it from disabling the USB connection to the card).  But each time I boot up or resume from sleep, I must use the hardware disable key (Fn + F3 on my Acer) to cycle through different modes of the wireless card.  By default only WiFi is enabled.  Each time I hit Fn + F3 it toggles between disabled and enabled...disabled and Bluetooth enabled...disabled and WiFi+Bluetooth enabled.

---

### Post by jeremy31 on 2016-06-16
The original poster could have suffered from the xhci problem as the dmesg info definitely shows the results of firmware getting loaded for the bluetooth.  The strange part is that lsusb doesn't show the bluetooth device.  My 7260 card with bluetooth shows a 8087:07dc in lsusb.  I also have a 7260 without bluetooth, it doesn't have a bluetooth MAC on the sticker

---

### Post by stefan_bahrens on 2016-09-14
I upgraded to Ubuntu 16.04 and the problem persisted. I don't believe that the way the BT module in the Intel 7260 adaptor connects is supported by the Ubuntu driver. I solved this problem by removing the Intel 7260 adaptor and throwing it away. I replaced it with an Intel 7265 adaptor. The problem immediately vanished and BT works perfectly.

---

