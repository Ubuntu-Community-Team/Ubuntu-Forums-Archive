---
title: "Maverick won't recognize Wacom Bamboo"
date: 2011-03-07
forum: Hardware
---

### Post by Afishionado on 2011-03-07
I have an Inspiron running Maverick Meercat. I got my hands on a Wacom Bamboo Pen, and plugged it in. The light on the tablet comes on, and it flashes every time I touch the pen to the tablet, so the tablet itself seems to be working.

Ubuntu, however, doesn't react to the device. Even after a reboot, the OS doesn't seem to respond to input from it. When I launch Gimp and look under "Configure Extended Input Devices", no tablet entry shows up. (I do see an "XTEST pointer", the PS/2 trackpad, and my USB mouse.) The device does show up in the output from lsusb, but that's it.

The Wacom thread on the wiki [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom) hasn't helped me. I already have the Wacom Xorg drivers installed, and the only configuration tweaks they discuss for Maverick involve the buttons on the tablet, which is currently moot.

Ideas?

**Edit: Console output that might be helpful.**

[FONT="Courier New"]wtracy@wtracy-Inspiron-1420:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 046d:c30f Logitech, Inc. Logicool HID-Compliant Keyboard (106 key)
Bus 006 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 056a:00d4 Wacom Co., Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
wtracy@wtracy-Inspiron-1420:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Basic Optical Mouse           	id=9	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Logitech Logitech USB Keyboard          	id=10	[slave  keyboard (3)]
    &#8627; Logitech Logitech USB Keyboard          	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=15	[slave  keyboard (3)]
wtracy@wtracy-Inspiron-1420:~$[/FONT]

---

### Post by Favux on 2011-03-07
Hi Afishionado,

The default wacom.ko (usb kernel driver/module) in Maverick is from linuxwacom 0.8.4-4 and does not have your model in it.  You need to update your wacom.ko.  See part I. of the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Either compile an update or use one of the PPAs.

---

### Post by Afishionado on 2011-03-07
Thanks, that did the trick!

For future reference, is there any resource that tracks which kernels support which tablets?

---

### Post by Favux on 2011-03-08
No I'm afraid not.  The linuxwacom project does have a list of supported models in the FAQ for example or the Device ID table.  But it doesn't get down to the level of which kernel supports which models.

---

