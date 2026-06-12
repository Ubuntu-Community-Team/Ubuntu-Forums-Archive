---
title: "Acer aspire e5-521 touchpad not working"
date: 2014-12-11
forum: Hardware
---

### Post by lance bermudez on 2014-12-11
Help someone please my touchpad not working

lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1566
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon APU A4-6000 with R2 Graphics]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 9840
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 156b
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:08.0 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 1537
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 11)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.7 SD Host controller: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1580
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1581
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1582
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1583
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1584
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1585
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5287 (rev 01)
01:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)

drivers on acers web cite for windows 8.1 says 
Category 	Vendor 	Description 	         Version 	Size   	Date
TouchPad 	Synaptics 	Touchpad Driver 	18.1.2.1 	1.6 MB 	2014/10/21

---

### Post by bomm2 on 2014-12-11
I own the same laptop, and my touchpad is not working as well. It's a matter of kernel version. On Debian and Mint it works with 3.16.xx kernel... Upgrading the kernel, it stops working. On Ubuntu, it doesn't work even with 3.16.xx. I've asked for help on many forums, but I still have no idea how to solve this issue. :(

$ synclient
```
Couldn't find synaptics properties. No synaptics driver loaded?
```

$ xinput list
```
&#9121; Virtual core pointer                       id=2   [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                 id=4   [slave  pointer  (2)]
&#9116;   &#8627; SIGMACHIP USB Keyboard                     id=11   [slave  pointer  (2)]
&#9116;   &#8627; MLK Trust Mouse 15313                      id=12   [slave  pointer  (2)]
&#9123; Virtual core keyboard                      id=3   [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                id=5   [slave  keyboard (3)]
    &#8627; Power Button                               id=6   [slave  keyboard (3)]
    &#8627; Video Bus                                  id=7   [slave  keyboard (3)]
    &#8627; Power Button                               id=8   [slave  keyboard (3)]
    &#8627; Sleep Button                               id=9   [slave  keyboard (3)]
    &#8627; SIGMACHIP USB Keyboard                     id=10   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard               id=13   [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                           id=14   [slave  keyboard (3)]

```

dmesg --> no answers from the terminal (it immediately waits for a new command)

xserver-xorg-input-synaptics and multitouch are installed. I've also tried to install the liquorix kernel, but it didn't work.

---

### Post by lance bermudez on 2014-12-11
Thank you for letting me know what is going on. 
$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627;                                         	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HD WebCam                               	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
    &#8627; Acer WMI hotkeys   

I have the same installed. I will just keep using the wireless mouse I have tell lUbuntu or Ubuntu fixes the problem. When I get it working I will post here if you don't beat me to it. It has been years sense I had hardware that did not work with ubuntu.

---

### Post by lance bermudez on 2014-12-13
Installed new linux-image kernel with synaptic page manager in Lubuntu. Touchpad  will move the mouse pointer now and click but still does not work like it is suppose to do. I have a little arrow with white box under it. Have not been able to take a screen shot of the white box but can get the small arrow. 


$ sudo uname -r; xinput --list
3.16.0-28-generic
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627;     UNKNOWN                             	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HD WebCam                               	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                        	id=15	[slave  keyboard (3)]

---

