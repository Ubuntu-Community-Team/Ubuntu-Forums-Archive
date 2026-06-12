---
title: "Lenovo laptop 3000 N200 built in webcam not working"
date: 2011-02-13
forum: Hardware
---

### Post by whitey_1 on 2011-02-13
Hi Everyone,

I installed Linux version 9 about a year or so ago on my laptop, everything was fine , but the webcam didnt work and still doesnt work. I upgraded to version 10 Lucid Lynx, but the webcam still does not work.

My laptop model :  Lenovo 3000 N200 , type 0769 , model BLG. Built-in web cam
OS: Ubuntu 10.04 LTS - the Lucid Lynx.

I have found a website providing some information about drivers for the webcam on my laptop, but i cant make any sense of it. I think its for advanced users or programmers etc. The link is as follows:
[http://www.linlap.com/wiki/lenovo+3000+n200](http://www.linlap.com/wiki/lenovo+3000+n200)

There is a link on this page to webcam drivers;
[http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)

i dont know if those links are any use, or if they actually apply to my specific hardware

Im lost with this problem though, can anyone help? 

Thank you.

---

### Post by whitey_1 on 2011-02-13
I forgot to mention something. I previously had windows xp on this laptop and the webcam worked fine with that OS.

---

### Post by whitey_1 on 2011-02-16
is this a very tough question ? or have i posted it in the wrong section?

Can someone make a reply please, saying anything just so i know its posted in the forum

---

### Post by lidex on 2011-02-16
Have you seen this page:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by whitey_1 on 2011-02-17
Thanks for the link,

I am using Lucid Lynx Ubuntu but that document is for version 10.10. I looked at the page for users of older versions of Ubuntu and Lucid Lynx is not listed there.

The document itself talks mainly about usb webcams, not bult in ones. There is a lot of information on that page assuming that the webcam can already be seen by the system, but my webcam cant seem to be seen by at least 3 of the programs listed on that page.

Can you recommend another link or give me any more advice please?

---

### Post by coffee412 on 2011-02-17
I dont know the actual specs on your laptop. But here is a page that might interest you. 

[http://www.linlap.com/wiki/lenovo+3000+n200](http://www.linlap.com/wiki/lenovo+3000+n200)

Pay particular attention to the "Linux Compatibility" section and the link in a the camera section. 

You can also do a lspci -v > pcidevices.txt and post that file to see what you have inside.

Hope this helps,

coffee

---

### Post by whitey_1 on 2011-02-17
Thanks Coffee , 
I have already seen that page. Where it says about the web cam there is a link to download a driver, but this leads to a really complicated page. I want to know how to do this, because its gibberish to me. I think that page was designed for people in the know.

I will try it though, but if anyone could give me another link or more advice , that would be much appreciated!

Ive had linux on my laptop for a while now, but ive never been able to get the web cam working, frustrating , but its a great OS

---

### Post by coffee412 on 2011-02-17
What would be really helpful is if you ran the following command:

> sudo lspci > pci.txt


Then posted the contents of the file pci.txt so we can know a bit about your webcam. Then we can investigate further.

---

### Post by whitey_1 on 2011-02-17
thanks for the reply, but i copied that over to the terminal but nothing happens. This is what happens ...

simon@simon-ubuntu:~$ sudo lspci > pci.txt 
simon@simon-ubuntu:~$ 

Am i getting something wrong there ? :frown:

---

### Post by coffee412 on 2011-02-17
> **whitey_1 said:**
> thanks for the reply, but i copied that over to the terminal but nothing happens. This is what happens ...

simon@simon-ubuntu:~$ sudo lspci > pci.txt 
simon@simon-ubuntu:~$ 

Am i getting something wrong there ? :frown:

Ok, Now you will have a file called pci.txt there. Go to your desktop, open up your filebrowser and open the file. Then look for where it mentions your cam and copy paste it into the next message. 

Typically, the file will be in /home/<username>

Where <username> is your login name.

---

### Post by whitey_1 on 2011-02-17
Ok i open the pci.txt file and it looks like this ;

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
08:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
08:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
08:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


I cant see where it mentions about the web cam though. Would it just be on one single line about the web cam ?

---

### Post by whitey_1 on 2011-02-17
I have tried to look up some of those lines on google, and its very tricky, ive had no luck there. It would be great if someone could make sense of that pci.txt document.

I just tried typing in 'lsusb' into the terminal and i got this ;

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Still nothing about my webcam though.

Any ideas anyone ?

---

### Post by coffee412 on 2011-02-17
The plot thickens!

I also see nothing about your webcam. Those lines represent the devices in your laptop --btw.

I would have to say that the cam is not recognized as even being there. I have no idea why though. Usually you will get a line stating "UVC device blah, blah" but you dont even have any info whatsoever about a vid cam.

Could you try : sudo dmesg > bootlog.txt 

Post the whole darn thing or see if you can attach as file.

---

### Post by coffee412 on 2011-02-17
Says its supported. Hummm.....

[http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)





Chicony USB 2.0 Camera (Lenovo 3000 N200 notebooks)       Chicony Electronics       [IMG]http://www.ideasonboard.org/uvc/ok.png[/IMG]

---

### Post by whitey_1 on 2011-02-17
thanks coffee ,

I tried putting **sudo dmesg > bootlog.txt**  into the terminal and i got this :

simon@simon-ubuntu:~$ Could you try : sudo dmesg > bootlog.txt 
Could: command not found
simon@simon-ubuntu:~$ 

Is that an obvious error im making there?

The cam always used to work on windows xp, but no way im going back to windows :D

---

### Post by whitey_1 on 2011-02-17
If i just type in the first bit i get a lot of code, here it is ;

[    3.724078] hub 4-0:1.0: unable to enumerate USB device on port 2
[    3.964063] usb 6-2: new full speed USB device using uhci_hcd and address 2
[    4.129543] usb 6-2: configuration #1 chosen from 1 choice
[   23.034113] udev: starting version 151
[   23.040792] Adding 4803392k swap on /dev/sda5.  Priority:-1 extents:1 across:4803392k 
[   23.263723] Linux agpgart interface v0.103
[   23.406672] sdhci: Secure Digital Host Controller Interface driver
[   23.406676] sdhci: Copyright(c) Pierre Ossman
[   23.408906] ricoh-mmc: Ricoh MMC Controller disabling driver
[   23.408909] ricoh-mmc: Copyright(c) Philip Langdale
[   23.408944] ricoh-mmc: Ricoh MMC controller found at 0000:08:06.2 [1180:0843] (rev 1)
[   23.408968] ricoh-mmc: Controller is now disabled.
[   23.409241] sdhci-pci 0000:08:06.1: SDHCI controller found [1180:0822] (rev 19)
[   23.409265] sdhci-pci 0000:08:06.1: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[   23.411333] Registered led device: mmc0::
[   23.412698] cfg80211: Calling CRDA to update world regulatory domain
[   23.424401] mmc0: SDHCI controller on PCI [0000:08:06.1] using PIO
[   23.484745] lp: driver loaded but no devices found
[   23.493836] [drm] Initialized drm 1.1.0 20060810
[   23.508418] cfg80211: World regulatory domain updated:
[   23.508423]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   23.508428]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.508432]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.508435]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.508438]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.508441]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.509587] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   23.510787] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   23.518577] Bluetooth: Core ver 2.15
[   23.518816] NET: Registered protocol family 31
[   23.518818] Bluetooth: HCI device and connection manager initialized
[   23.518823] Bluetooth: HCI socket layer initialized
[   23.519789] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   23.520899] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   23.521095] usbcore: registered new interface driver btusb
[   23.522847] type=1505 audit(1297978616.529:2):  operation="profile_load" pid=634 name="/sbin/dhclient3"
[   23.523791] type=1505 audit(1297978616.529:3):  operation="profile_load" pid=634 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   23.524296] type=1505 audit(1297978616.533:4):  operation="profile_load" pid=634 name="/usr/lib/connman/scripts/dhclient-script"
[   23.532496] type=1505 audit(1297978616.541:5):  operation="profile_replace" pid=642 name="/sbin/dhclient3"
[   23.562480] type=1505 audit(1297978616.569:6):  operation="profile_replace" pid=642 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   23.563007] type=1505 audit(1297978616.569:7):  operation="profile_replace" pid=642 name="/usr/lib/connman/scripts/dhclient-script"
[   23.622660] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.622668] i915 0000:00:02.0: setting latency timer to 64
[   23.630936]   alloc irq_desc for 29 on node -1
[   23.630941]   alloc kstat_irqs on node -1
[   23.630954] i915 0000:00:02.0: irq 29 for MSI/MSI-X
[   23.630964] [drm] set up 7M of stolen space
[   23.644754] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   23.644759] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   23.644854] iwl3945 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   23.644871] iwl3945 0000:04:00.0: setting latency timer to 64
[   23.828620] iwl3945 0000:04:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   23.828625] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   23.828750]   alloc irq_desc for 30 on node -1
[   23.828753]   alloc kstat_irqs on node -1
[   23.828791] iwl3945 0000:04:00.0: irq 30 for MSI/MSI-X
[   23.838192] [drm] initialized overlay support
[   23.850895] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.863838] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   23.900303] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   23.900562] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   23.900564] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   23.900567] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   24.222298] iwl3945 0000:04:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   24.263718] iwl3945 0000:04:00.0: loaded firmware version 15.32.2.9
[   24.288245] type=1505 audit(1297978617.297:8):  operation="profile_load" pid=857 name="/usr/share/gdm/guest-session/Xsession"
[   24.288434] type=1505 audit(1297978617.297:9):  operation="profile_replace" pid=858 name="/sbin/dhclient3"
[   24.289420] type=1505 audit(1297978617.297:10):  operation="profile_replace" pid=858 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   24.289937] type=1505 audit(1297978617.297:11):  operation="profile_replace" pid=858 name="/usr/lib/connman/scripts/dhclient-script"
[   24.334809] Registered led device: iwl-phy0::radio
[   24.335163] Registered led device: iwl-phy0::assoc
[   24.336011] Registered led device: iwl-phy0::RX
[   24.336414] Registered led device: iwl-phy0::TX
[   24.349145] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.351174]   alloc irq_desc for 31 on node -1
[   24.351179]   alloc kstat_irqs on node -1
[   24.351215] tg3 0000:06:00.0: irq 31 for MSI/MSI-X
[   24.381250] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.406498] fb0: inteldrmfb frame buffer device
[   24.406502] registered panic notifier
[   24.426105] acpi device:07: registered as cooling_device2
[   24.426447] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input5
[   24.426521] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   24.426573] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   24.426723] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   24.426774] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   24.432311] vga16fb: initializing
[   24.432316] vga16fb: mapped to 0xc00a0000
[   24.432322] vga16fb: not registering due to another framebuffer present
[   24.537977] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   24.557782] Console: switching to colour frame buffer device 210x65
[   24.559177] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x25c0b1, caps: 0xa04713/0x200000
[   24.744435] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   24.937389] Bluetooth: L2CAP ver 2.14
[   24.937394] Bluetooth: L2CAP socket layer initialized
[   24.944430] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.944434] Bluetooth: BNEP filters: protocol multicast
[   24.953948] Bridge firewalling registered
[   24.963914] Bluetooth: SCO (Voice Link) ver 0.6
[   24.963918] Bluetooth: SCO socket layer initialized
[   24.993749] ppdev: user-space parallel port driver
[   25.078718] Bluetooth: RFCOMM TTY layer initialized
[   25.078724] Bluetooth: RFCOMM socket layer initialized
[   25.078727] Bluetooth: RFCOMM ver 1.11
[   32.054563] Linux video capture interface: v2.00
[   32.056027] WebcamStudio module installed
[   56.909736] wlan0: deauthenticating from 00:16:e3:dd:41:0c by local choice (reason=3)
[   56.911200] wlan0: direct probe to AP 00:16:e3:dd:41:0c (try 1)
[   56.913405] wlan0: direct probe responded
[   56.913411] wlan0: authenticate with AP 00:16:e3:dd:41:0c (try 1)
[   56.915213] wlan0: authenticated
[   56.915248] wlan0: associate with AP 00:16:e3:dd:41:0c (try 1)
[   56.917696] wlan0: RX AssocResp from 00:16:e3:dd:41:0c (capab=0x411 status=0 aid=1)
[   56.917702] wlan0: associated
[   56.919598] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   67.885028] wlan0: no IPv6 routers present
[  996.128120] usb 4-2: new full speed USB device using uhci_hcd and address 7
[  996.252052] usb 4-2: device descriptor read/64, error -71
[  996.476057] usb 4-2: device descriptor read/64, error -71
[  996.693828] usb 4-2: new full speed USB device using uhci_hcd and address 8
[  996.820054] usb 4-2: device descriptor read/64, error -71
[  997.044063] usb 4-2: device descriptor read/64, error -71
[  997.260099] usb 4-2: new full speed USB device using uhci_hcd and address 9
[  997.669062] usb 4-2: device not accepting address 9, error -71
[  997.780107] usb 4-2: new full speed USB device using uhci_hcd and address 10
[  998.193119] usb 4-2: device not accepting address 10, error -71
[  998.193153] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 1272.065133] usb 4-2: new full speed USB device using uhci_hcd and address 11
[ 1272.185082] usb 4-2: device descriptor read/64, error -71
[ 1272.408178] usb 4-2: device descriptor read/64, error -71
[ 1272.624107] usb 4-2: new full speed USB device using uhci_hcd and address 12
[ 1272.744133] usb 4-2: device descriptor read/64, error -71
[ 1272.969127] usb 4-2: device descriptor read/64, error -71
[ 1273.185095] usb 4-2: new full speed USB device using uhci_hcd and address 13
[ 1273.597121] usb 4-2: device not accepting address 13, error -71
[ 1273.708155] usb 4-2: new full speed USB device using uhci_hcd and address 14
[ 1274.116130] usb 4-2: device not accepting address 14, error -71
[ 1274.116168] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 1282.568105] usb 4-2: new full speed USB device using uhci_hcd and address 15
[ 1282.688125] usb 4-2: device descriptor read/64, error -71
[ 1282.912090] usb 4-2: device descriptor read/64, error -71
[ 1283.129144] usb 4-2: new full speed USB device using uhci_hcd and address 16
[ 1283.249095] usb 4-2: device descriptor read/64, error -71
[ 1283.476091] usb 4-2: device descriptor read/64, error -71
[ 1283.692095] usb 4-2: new full speed USB device using uhci_hcd and address 17
[ 1284.101082] usb 4-2: device not accepting address 17, error -71
[ 1284.213129] usb 4-2: new full speed USB device using uhci_hcd and address 18
[ 1284.625093] usb 4-2: device not accepting address 18, error -71
[ 1284.625128] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 2964.365117] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 2964.753100] usb 4-2: new full speed USB device using uhci_hcd and address 19
[ 2964.872699] usb 4-2: device descriptor read/64, error -71
[ 2965.096100] usb 4-2: device descriptor read/64, error -71
[ 2965.257194] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 2965.992514] usb 4-2: new full speed USB device using uhci_hcd and address 21
[ 2966.113091] usb 4-2: device descriptor read/64, error -71
[ 2966.337093] usb 4-2: device descriptor read/64, error -71
[ 2966.552095] usb 4-2: new full speed USB device using uhci_hcd and address 22
[ 2966.672121] usb 4-2: device descriptor read/64, error -71
[ 2966.897090] usb 4-2: device descriptor read/64, error -71
[ 2967.113088] usb 4-2: new full speed USB device using uhci_hcd and address 23
[ 2967.520149] usb 4-2: device not accepting address 23, error -71
[ 2967.632146] usb 4-2: new full speed USB device using uhci_hcd and address 24
[ 2968.041115] usb 4-2: device not accepting address 24, error -71
[ 2968.041150] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 3869.488099] usb 4-2: new full speed USB device using uhci_hcd and address 25
[ 3869.608150] usb 4-2: device descriptor read/64, error -71
[ 3869.833068] usb 4-2: device descriptor read/64, error -71
[ 3870.048154] usb 4-2: new full speed USB device using uhci_hcd and address 26
[ 3870.168148] usb 4-2: device descriptor read/64, error -71
[ 3870.392096] usb 4-2: device descriptor read/64, error -71
[ 3870.608113] usb 4-2: new full speed USB device using uhci_hcd and address 27
[ 3871.021081] usb 4-2: device not accepting address 27, error -71
[ 3871.133132] usb 4-2: new full speed USB device using uhci_hcd and address 28
[ 3871.541080] usb 4-2: device not accepting address 28, error -71
[ 3871.541115] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 6184.289130] usb 4-2: new full speed USB device using uhci_hcd and address 29
[ 6184.408102] usb 4-2: device descriptor read/64, error -71
[ 6184.632150] usb 4-2: device descriptor read/64, error -71
[ 6184.848156] usb 4-2: new full speed USB device using uhci_hcd and address 30
[ 6184.968108] usb 4-2: device descriptor read/64, error -71
[ 6185.193084] usb 4-2: device descriptor read/64, error -71
[ 6185.409095] usb 4-2: new full speed USB device using uhci_hcd and address 31
[ 6185.817118] usb 4-2: device not accepting address 31, error -71
[ 6185.928151] usb 4-2: new full speed USB device using uhci_hcd and address 32
[ 6186.336141] usb 4-2: device not accepting address 32, error -71
[ 6186.336177] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 6188.536105] usb 4-2: new full speed USB device using uhci_hcd and address 33
[ 6188.657062] usb 4-2: device descriptor read/64, error -71
[ 6188.881084] usb 4-2: device descriptor read/64, error -71
[ 6189.096856] usb 4-2: new full speed USB device using uhci_hcd and address 34
[ 6189.217131] usb 4-2: device descriptor read/64, error -71
[ 6189.441091] usb 4-2: device descriptor read/64, error -71
[ 6189.656151] usb 4-2: new full speed USB device using uhci_hcd and address 35
[ 6190.064041] usb 4-2: device not accepting address 35, error -71
[ 6190.177135] usb 4-2: new full speed USB device using uhci_hcd and address 36
[ 6190.585121] usb 4-2: device not accepting address 36, error -71
[ 6190.585157] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 6196.192111] usb 4-2: new full speed USB device using uhci_hcd and address 37
[ 6196.312911] usb 4-2: device descriptor read/64, error -71
[ 6196.537090] usb 4-2: device descriptor read/64, error -71
[ 6196.752096] usb 4-2: new full speed USB device using uhci_hcd and address 38
[ 6196.873128] usb 4-2: device descriptor read/64, error -71
[ 6197.097080] usb 4-2: device descriptor read/64, error -71
[ 6197.313145] usb 4-2: new full speed USB device using uhci_hcd and address 39
[ 6197.724124] usb 4-2: device not accepting address 39, error -71
[ 6197.836093] usb 4-2: new full speed USB device using uhci_hcd and address 40
[ 6198.249120] usb 4-2: device not accepting address 40, error -71
[ 6198.249156] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 7049.169335] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 7049.356342] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 7049.548339] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 7049.789071] usb 1-4: new high speed USB device using ehci_hcd and address 11
[ 7049.856334] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 7050.304090] usb 4-2: new full speed USB device using uhci_hcd and address 41
[ 7050.451411] usb 4-2: not running at top speed; connect to a high speed hub
[ 7050.503630] usb 4-2: configuration #1 chosen from 1 choice
[ 7050.522537] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[ 7050.527556] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input8
[ 7050.527641] usbcore: registered new interface driver uvcvideo
[ 7050.527645] USB Video Class driver (v0.1.0)
[ 7051.993081] wlan0: deauthenticating from 00:16:e3:dd:41:0c by local choice (reason=3)
[ 7052.635575] PM: Syncing filesystems ... done.
[ 7052.640376] PM: Preparing system for mem sleep
[ 7052.640382] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 7052.641440] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 7052.641515] PM: Entering mem sleep
[ 7052.641532] Suspending console(s) (use no_console_suspend to debug)
[ 7052.702001] btusb_intr_complete: hci0 urb f2e2ab80 failed to resubmit (1)
[ 7052.703002] btusb_bulk_complete: hci0 urb f1eb5800 failed to resubmit (1)
[ 7052.703998] btusb_bulk_complete: hci0 urb f1eb5c00 failed to resubmit (1)
[ 7052.736118] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[ 7052.758032] sd 2:0:0:0: [sda] Stopping disk
[ 7055.155355] PM: suspend of drv:sd dev:2:0:0:0 complete after 2419.240 msecs
[ 7055.571974] PM: suspend of drv:psmouse dev:serio1 complete after 416.496 msecs
[ 7055.676063] PM: suspend of drv:atkbd dev:serio0 complete after 104.083 msecs
[ 7055.680678] ACPI handle has no context!
[ 7055.681804] ACPI handle has no context!
[ 7055.681813] sdhci-pci 0000:08:06.1: PCI INT B disabled
[ 7055.681820] ACPI handle has no context!
[ 7055.701138] ACPI handle has no context!
[ 7055.796368] ata_piix 0000:00:1f.1: PCI INT A disabled
[ 7055.796400] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[ 7055.796423] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 7055.796443] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 7055.796465] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 7056.004166] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 7056.020081] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 223.579 msecs
[ 7056.020100] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[ 7056.020122] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[ 7056.020144] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[ 7056.097488] PM: suspend of devices complete after 3455.510 msecs
[ 7056.097492] PM: suspend devices took 3.456 seconds
[ 7056.098126] ricoh-mmc: Suspending.
[ 7056.098148] ricoh-mmc: Controller is now re-enabled.
[ 7056.128350] PM: late suspend of devices complete after 30.850 msecs
[ 7056.128547] ACPI: Preparing to enter system sleep state S3
[ 7056.149226] Disabling non-boot CPUs ...
[ 7056.149244] CPU0 attaching NULL sched-domain.
[ 7056.149248] CPU1 attaching NULL sched-domain.
[ 7056.197024] CPU0 attaching NULL sched-domain.
[ 7056.198154] Breaking affinity for irq 1
[ 7056.198187] Breaking affinity for irq 12
[ 7056.198211] Breaking affinity for irq 19
[ 7056.198218] Breaking affinity for irq 21
[ 7056.198233] Breaking affinity for irq 28
[ 7056.300063] CPU 1 is now offline
[ 7056.300067] SMP alternatives: switching to UP code
[ 7056.308485] Extended CMOS year: 2000
[ 7056.308485] Back to C!
[ 7056.308485] CPU0: Thermal monitoring handled by SMI
[ 7056.308485] Extended CMOS year: 2000
[ 7056.308485] Enabling non-boot CPUs ...
[ 7056.308485] SMP alternatives: switching to SMP code
[ 7056.316404] Booting processor 1 APIC 0x1 ip 0x6000
[ 7056.308485] Initializing CPU#1
[ 7056.308485] CPU: L1 I cache: 32K, L1 D cache: 32K
[ 7056.308485] CPU: L2 cache: 1024K
[ 7056.308485] CPU: Physical Processor ID: 0
[ 7056.308485] CPU: Processor Core ID: 1
[ 7056.308485] CPU1: Thermal monitoring handled by SMI
[ 7056.404127] CPU1: Intel(R) Pentium(R) Dual  CPU  T2330  @ 1.60GHz stepping 0d
[ 7056.404199] CPU0 attaching NULL sched-domain.
[ 7056.432020] CPU0 attaching sched-domain:
[ 7056.432024]  domain 0: span 0-1 level MC
[ 7056.432027]   groups: 0 1
[ 7056.432032] CPU1 attaching sched-domain:
[ 7056.432035]  domain 0: span 0-1 level MC
[ 7056.432037]   groups: 1 0
[ 7056.432652] CPU1 is up
[ 7056.433047] ACPI: Waking up from system sleep state S3
[ 7056.434157] i915 0000:00:02.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[ 7056.434175] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[ 7056.434216] pci 0000:00:02.1: restoring config space at offset 0x1 (was 0x900000, writing 0x900007)
[ 7056.434258] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 7056.434300] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 7056.434353] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[ 7056.434420] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100102)
[ 7056.434477] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20002020, writing 0x2020)
[ 7056.434492] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 7056.434569] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0x20003030, writing 0x3030)
[ 7056.434585] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[ 7056.434672] pcieport 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[ 7056.434748] pcieport 0000:00:1c.3: restoring config space at offset 0x7 (was 0x20005050, writing 0x5050)
[ 7056.434764] pcieport 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[ 7056.434838] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 7056.434880] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 7056.434921] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 7056.434973] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[ 7056.435128] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2880005)
[ 7056.435182] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[ 7056.435246] pci 0000:00:1f.3: restoring config space at offset 0x4 (was 0x0, writing 0x80000000)
[ 7056.435333] iwl3945 0000:04:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 7056.435404] iwl3945 0000:04:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xf8000000)
[ 7056.435419] iwl3945 0000:04:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 7056.435439] iwl3945 0000:04:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
[ 7056.435644] tg3 0000:06:00.0: restoring config space at offset 0xf (was 0x141, writing 0x10a)
[ 7056.435668] tg3 0000:06:00.0: restoring config space at offset 0xc (was 0x0, writing 0x10000000)
[ 7056.435712] tg3 0000:06:00.0: restoring config space at offset 0x5 (was 0xb0420148, writing 0x0)
[ 7056.435726] tg3 0000:06:00.0: restoring config space at offset 0x4 (was 0xbf000004, writing 0xc8000004)
[ 7056.435739] tg3 0000:06:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 7056.435758] tg3 0000:06:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x40100106)
[ 7056.435992] ricoh-mmc: Resuming.
[ 7056.436031] ricoh-mmc: Controller is now disabled.
[ 7056.452026] __ratelimit: 21 callbacks suppressed
[ 7056.452028] pci 0000:08:06.4: Refused to change power state, currently in D3
[ 7056.452502] PM: early resume of devices complete after 18.495 msecs
[ 7056.580220] PM: resume of drv:battery dev:PNP0C0A:00 complete after 127.160 msecs
[ 7056.586584] i915 0000:00:02.0: setting latency timer to 64
[ 7056.728214] PM: resume of drv:i915 dev:0000:00:02.0 complete after 141.640 msecs
[ 7056.728234] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 7056.728242] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[ 7056.728271] usb usb3: root hub lost power or was reset
[ 7056.728297] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[ 7056.728305] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[ 7056.728334] usb usb4: root hub lost power or was reset
[ 7056.728371] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 7056.728380] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[ 7056.728408] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 7056.728417] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 7056.818041] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 7056.818054] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 7056.818083] usb usb5: root hub lost power or was reset
[ 7056.818116] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 7056.818124] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 7056.818152] usb usb6: root hub lost power or was reset
[ 7056.818196] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 7056.818204] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 7056.818233] usb usb7: root hub lost power or was reset
[ 7056.818262] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 7056.818270] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 7056.818328] pci 0000:00:1e.0: setting latency timer to 64
[ 7056.818351] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 7056.818357] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 7056.818398] ahci 0000:00:1f.2: setting latency timer to 64
[ 7056.874071] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fc200000-fc2007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[ 7056.880156] sdhci-pci 0000:08:06.1: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[ 7056.988501] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[ 7056.988506] ata1.00: ACPI cmd ef/03:42:00:00:00:a0 (SET FEATURES) filtered out
[ 7057.020399] ata1.00: configured for UDMA/33
[ 7057.132059] PM: resume of drv:usb dev:usb1 complete after 251.327 msecs
[ 7057.136077] ata5: SATA link down (SStatus 0 SControl 300)
[ 7057.136102] ata4: SATA link down (SStatus 0 SControl 300)
[ 7057.384063] PM: resume of drv:usb dev:usb2 complete after 251.983 msecs
[ 7057.528061] PM: resume of drv:usb dev:usb3 complete after 143.981 msecs
[ 7057.776044] PM: resume of drv:usb dev:usb4 complete after 247.965 msecs
[ 7057.920060] PM: resume of drv:usb dev:usb5 complete after 143.999 msecs
[ 7058.168043] PM: resume of drv:usb dev:usb6 complete after 247.966 msecs
[ 7058.312061] PM: resume of drv:usb dev:usb7 complete after 144.001 msecs
[ 7058.320280] sd 2:0:0:0: [sda] Starting disk
[ 7058.592052] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 7058.593119] ata3.00: _GTF unexpected object type 0x1
[ 7058.594414] ata3.00: _GTF unexpected object type 0x1
[ 7058.594535] ata3.00: configured for UDMA/100
[ 7058.626764] PM: resume of drv:sd dev:2:0:0:0 complete after 306.484 msecs
[ 7058.736045] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[ 7058.888087] PM: resume of drv:usb dev:4-1 complete after 261.291 msecs
[ 7059.000048] usb 6-2: reset full speed USB device using uhci_hcd and address 2
[ 7059.150084] btusb 6-2:1.0: no reset_resume for driver btusb?
[ 7059.150087] btusb 6-2:1.1: no reset_resume for driver btusb?
[ 7059.400172] PM: resume of drv:usb dev:6-2 complete after 512.062 msecs
[ 7059.512044] usb 4-2: reset full speed USB device using uhci_hcd and address 41
[ 7059.632043] usb 4-2: device descriptor read/64, error -71
[ 7059.860043] usb 4-2: device descriptor read/64, error -71
[ 7060.076045] usb 4-2: reset full speed USB device using uhci_hcd and address 41
[ 7060.200043] usb 4-2: device descriptor read/64, error -71
[ 7060.424039] usb 4-2: device descriptor read/64, error -71
[ 7060.640043] usb 4-2: reset full speed USB device using uhci_hcd and address 41
[ 7061.048041] usb 4-2: device not accepting address 41, error -71
[ 7061.160043] usb 4-2: reset full speed USB device using uhci_hcd and address 41
[ 7061.568042] usb 4-2: device not accepting address 41, error -71
[ 7061.568066] PM: resume of drv:usb dev:4-2 complete after 2167.645 msecs
[ 7061.568092] PM: resume of devices complete after 5115.400 msecs
[ 7061.568497] PM: resume devices took 5.116 seconds
[ 7061.568532] PM: Finishing wakeup.
[ 7061.568535] Restarting tasks ... 
[ 7061.568612] usb 4-2: USB disconnect, address 41
[ 7061.622291] done.
[ 7061.709055] usb 4-2: new full speed USB device using uhci_hcd and address 42
[ 7061.833050] usb 4-2: device descriptor read/64, error -71
[ 7062.061048] usb 4-2: device descriptor read/64, error -71
[ 7062.277081] usb 4-2: new full speed USB device using uhci_hcd and address 43
[ 7062.401059] usb 4-2: device descriptor read/64, error -71
[ 7062.628052] usb 4-2: device descriptor read/64, error -71
[ 7062.844098] usb 4-2: new full speed USB device using uhci_hcd and address 44
[ 7062.980488] Registered led device: iwl-phy0::radio
[ 7062.980581] Registered led device: iwl-phy0::assoc
[ 7062.980627] Registered led device: iwl-phy0::RX
[ 7062.980678] Registered led device: iwl-phy0::TX
[ 7062.993279] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7062.996061] tg3 0000:06:00.0: irq 31 for MSI/MSI-X
[ 7063.026967] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7063.260067] usb 4-2: device not accepting address 44, error -71
[ 7063.372095] usb 4-2: new full speed USB device using uhci_hcd and address 45
[ 7063.792060] usb 4-2: device not accepting address 45, error -71
[ 7063.792088] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 7065.655056] wlan0: deauthenticating from 00:16:e3:dd:41:0c by local choice (reason=3)
[ 7065.690941] wlan0: direct probe to AP 00:16:e3:dd:41:0c (try 1)
[ 7065.693099] wlan0: direct probe responded
[ 7065.693109] wlan0: authenticate with AP 00:16:e3:dd:41:0c (try 1)
[ 7065.694835] wlan0: authenticated
[ 7065.694883] wlan0: associate with AP 00:16:e3:dd:41:0c (try 1)
[ 7065.696958] wlan0: RX AssocResp from 00:16:e3:dd:41:0c (capab=0x411 status=0 aid=2)
[ 7065.696966] wlan0: associated
[ 7065.698885] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7076.652077] wlan0: no IPv6 routers present
[ 7214.500089] No probe response from AP 00:16:e3:dd:41:0c after 500ms, disconnecting.
[ 7217.281123] wlan0: direct probe to AP 00:16:e3:dd:41:0c (try 1)
[ 7217.283256] wlan0: direct probe responded
[ 7217.283267] wlan0: authenticate with AP 00:16:e3:dd:41:0c (try 1)
[ 7217.285256] wlan0: authenticated
[ 7217.285359] wlan0: associate with AP 00:16:e3:dd:41:0c (try 1)
[ 7217.287580] wlan0: RX AssocResp from 00:16:e3:dd:41:0c (capab=0x411 status=0 aid=1)
[ 7217.287589] wlan0: associated
simon@simon-ubuntu:~$

---

### Post by whitey_1 on 2011-02-17
I think it must be missing a bit at the start because i scrolled back up to the top far as i could and i couldnt get to the original start bit.

Is that useful? i see some errors on there, right at the start for example.

---

### Post by lidex on 2011-02-18
Try this as it seems to work for some others. Enter this in a terminal:
```
echo Y | sudo tee /sys/module/usbcore/parameters/old_scheme_first
```
Now reboot.

Run this command to see if that usb -71 error is persistent:
```
dmesg | grep -i error
```

Reference:
[http://art.ubuntuforums.org/showthread.php?t=797789](http://art.ubuntuforums.org/showthread.php?t=797789)

---

### Post by coffee412 on 2011-02-18
Apparently, YOu have a **Sonix/Microdia Webcam **in the laptop.

The following link shows how to install the drivers for it. However, Its from 2007. So, The webcam should work. 

[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

According to the dmesg output your camera id is --> uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)

Have you tried to install the program cheese and see if it detects it?

---

### Post by whitey_1 on 2011-02-18
> **coffee412 said:**
> Apparently, YOu have a **Sonix/Microdia Webcam **in the laptop.

The following link shows how to install the drivers for it. However, Its from 2007. So, The webcam should work. 

[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

According to the dmesg output your camera id is --> uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)

Have you tried to install the program cheese and see if it detects it?

Thanks for the link and the info coffee !

I followed the link, but i get stuck on step 2 

[B][I]2) In Terminal enter this
svn checkout [http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/](http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/)
            cd trunk/
            gedit Makefile[/I][/B]

When i copy those lines over to the terminal i get this response;

[I][B]simon@simon-ubuntu:~$ svn checkout [http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/](http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/)
Authentication realm: <http://svn.berlios.de:80> Members Only
Password for 'simon': [/B][/I]

Im not a member of what ever it is so i cannot go any further. I followed the ***svn.berlios.d****e*** link but i do not see anything about joining to become a member.

I think ive missed something obvious there, any ideas ? :confused:

---

### Post by whitey_1 on 2011-02-18
> **lidex said:**
> Try this as it seems to work for some others. Enter this in a terminal:
```
echo Y | sudo tee /sys/module/usbcore/parameters/old_scheme_first
```Now reboot.

Run this command to see if that usb -71 error is persistent:
```
dmesg | grep -i error
```Reference:
[http://art.ubuntuforums.org/showthread.php?t=797789](http://art.ubuntuforums.org/showthread.php?t=797789)

Thanks for the link, but i dont think it worked. This is what happens;

[B][I]simon@simon-ubuntu:~$ echo Y | sudo tee /sys/module/usbcore/parameters/old_scheme_first
Y
simon@simon-ubuntu:~$ [/I][/B]

I restarted after that, as you said. Then opened the terminal back up and typed the second part and got this;

[B][I]simon@simon-ubuntu:~$ dmesg | grep -i error
[    1.804081] usb 4-2: device descriptor read/64, error -71
[    2.028057] usb 4-2: device descriptor read/64, error -71
[    2.365049] usb 4-2: device descriptor read/64, error -71
[    2.593050] usb 4-2: device descriptor read/64, error -71
[    3.221072] usb 4-2: device not accepting address 5, error -71
[    3.744046] usb 4-2: device not accepting address 6, error -71
[  142.868084] usb 4-2: device descriptor read/64, error -71
[  143.092096] usb 4-2: device descriptor read/64, error -71
[  143.428125] usb 4-2: device descriptor read/64, error -71
[  143.652114] usb 4-2: device descriptor read/64, error -71
[  144.276100] usb 4-2: device not accepting address 9, error -71
[  144.796075] usb 4-2: device not accepting address 10, error -71
[  850.208098] usb 4-2: device descriptor read/64, error -71
[  850.436104] usb 4-2: device descriptor read/64, error -71
[  850.772088] usb 4-2: device descriptor read/64, error -71
[  850.996142] usb 4-2: device descriptor read/64, error -71
[  851.620089] usb 4-2: device not accepting address 13, error -71
[  852.140089] usb 4-2: device not accepting address 14, error -71
[ 2644.952103] usb 4-2: device descriptor read/64, error -71
[ 2645.177093] usb 4-2: device descriptor read/64, error -71
[ 2645.512113] usb 4-2: device descriptor read/64, error -71
[ 2645.736114] usb 4-2: device descriptor read/64, error -71
[ 2646.360098] usb 4-2: device not accepting address 17, error -71
[ 2646.880092] usb 4-2: device not accepting address 18, error -71
simon@simon-ubuntu:~$ 

[/I][/B]Is that any use to solving the problem?
****

---

### Post by whitey_1 on 2011-02-18
Regarding the cheese program. I have tried it and it doesnt detect any web cam at all. 'No device detected'

---

### Post by lidex on 2011-02-18
Can you post some bios and kernel info please:
```
uname -a
sudo dmidecode -t bios
sudo dmidecode -t baseboard
```

---

### Post by whitey_1 on 2011-02-18
> **lidex said:**
> Can you post some bios and kernel info please:
```
uname -a
sudo dmidecode -t bios
sudo dmidecode -t baseboard
```

Ok here it is :

**simon@simon-ubuntu:~$ uname -a**
Linux simon-ubuntu 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686 GNU/Linux
[B]
simon@simon-ubuntu:~$ sudo dmidecode -t bios[/B]
[sudo] password for simon: 
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: LENOVO
    Version: 68ET24WW
    Release Date: 08/15/2007
    Address: 0xE5820
    Runtime Size: 108512 bytes
    ROM Size: 1024 kB
    Characteristics:
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        5.25"/360 KB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        LS-120 boot is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
    BIOS Revision: 0.36
    Firmware Revision: 0.36

**simon@simon-ubuntu:~$ sudo dmidecode -t baseboard**
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: LENOVO
    Product Name: IEL10
    Version: REFERENCE
    Serial Number: 41R7640Z1ZDCX78Y2UB             

Handle 0x000A, DMI type 10, 6 bytes
On Board Device Information
    Type: Sound
    Status: Disabled
    Description: HD-Audio


Thanks alot again for your help, much appreciated!

---

### Post by lidex on 2011-02-19
OK, here's my take. Your kernel actually has the uvc driver needed for your webcam and dmesg shows it is recognized. You have usb errors. I would suggest a bios update at this point.

---

### Post by Rahul Jain on 2011-02-19
well the way i did it in 10.10 is to go to your synaptic package manager, and search for CHEESE. install it . and it should work...

---

### Post by whitey_1 on 2011-02-19
> **lidex said:**
> OK, here's my take. Your kernel actually has the uvc driver needed for your webcam and dmesg shows it is recognized. You have usb errors. I would suggest a bios update at this point.

I have been doing my updates using the update manager, but do you mean updating it in some other way?

Could you tell me how i update my bios, sounds like its what needs to be done to solve this problem.

If it is a bios problem, how come everything else works, like the speakers, dvd drive, internet etc ?

---

### Post by whitey_1 on 2011-02-19
> **Rahul Jain said:**
> well the way i did it in 10.10 is to go to your synaptic package manager, and search for CHEESE. install it . and it should work...

Thanks Rahul, i already have it installed and it says that it cant see a camera at all.

---

### Post by lidex on 2011-02-20
> **whitey_1 said:**
> I have been doing my updates using the update manager, but do you mean updating it in some other way?

Could you tell me how i update my bios, sounds like its what needs to be done to solve this problem.

If it is a bios problem, how come everything else works, like the speakers, dvd drive, internet etc ?

The bios is the lowest level software that interacts directly with your hardware. You would need to get the update from the website of your system manufacturer.

---

### Post by whitey_1 on 2011-02-21
> **lidex said:**
> The bios is the lowest level software that interacts directly with your hardware. You would need to get the update from the website of your system manufacturer.

Thanks Lidex. I have been to the lenovo website and found the relevant bios update page ;

[http://www-307.ibm.com/pc/support/site.wss/MIGR-67975.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-67975.html)

It says this update is only for windows xp and vista though. Is it still safe to run? I dont want to risk messing up my system.

I also tried their support section, i specified my laptop and selected the os as Linux, but it said there was 'no documents found. So i dont think Lenovo actually support Linux.

Any ideas anyone ?

---

### Post by lidex on 2011-02-22
> **whitey_1 said:**
> Thanks Lidex. I have been to the lenovo website and found the relevant bios update page ;

[http://www-307.ibm.com/pc/support/site.wss/MIGR-67975.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-67975.html)

It says this update is only for windows xp and vista though. Is it still safe to run? I dont want to risk messing up my system.

I also tried their support section, i specified my laptop and selected the os as Linux, but it said there was 'no documents found. So i dont think Lenovo actually support Linux.

Any ideas anyone ?
You get that alot from manufacturers. That bios update utility is designed to run in windows. Do you have windows on there as well?

---

### Post by whitey_1 on 2011-02-23
> **lidex said:**
> You get that alot from manufacturers. That bios update utility is designed to run in windows. Do you have windows on there as well?


No, its just linux on here. Maybe i should try posting on the Lenovo forums? 

I would prefer help from here though, because i think this is where the knowledge is best.

---

