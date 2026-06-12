---
title: "Mouse Stops Working - Details"
date: 2009-12-15
forum: Hardware
---

### Post by Daddyo-613 on 2009-12-15
Ms Wireless Laser Mouse 5000 attached to USB

**The Problem:** Mouse works on boot up but freezes after a while and will not respond without rebooting.

**My System:**
CPU: Intel Core 2 Duo E6300 1.86GHz(1066MHz) s775
RAM: Kingston 1GB 240-pin DDR II 533MHz/PC4200
O/S: Ubuntu 8.10 Intrepid
Kernel: 2.6.27.16-Generic
Video Card: Asus GF7300LE w/TurboCache128MB TVOut DVI
Video Driver: nVidia ver. 180
USB Controllers: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 10 and 20)

Settings Manager: CCSM ver. 0.7.8
Window Manager: Compiz
Window Decoratior: GTK Window Decorator

The output for the USB using dmesg | grep usb is:
[PHP]stephen@stephen-desktop:~$ dmesg | grep usb
[    2.829625] usbcore: registered new interface driver usbfs
[    2.829661] usbcore: registered new interface driver hub
[    2.829698] usbcore: registered new device driver usb
[    2.848153] usb usb1: configuration #1 chosen from 1 choice
[    3.114758] usb usb2: configuration #1 chosen from 1 choice
[    3.220084] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    3.353501] usb 1-6: configuration #1 chosen from 1 choice
[    3.528053] usb 2-3: new low speed USB device using ohci_hcd and address 2
[    3.745738] usb 2-3: configuration #1 chosen from 1 choice
[    3.748879] usbcore: registered new interface driver libusual
[    3.756130] usbcore: registered new interface driver usb-storage
[    3.756229] usb-storage: device found at 3
[    3.756231] usb-storage: waiting for device to settle before scanning
[    3.766035] usbcore: registered new interface driver hiddev
[    3.779307] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /devices/pci0000:00/0000:00:0b.0/usb2/2-3/2-3:1.0/input/input2
[    3.784138] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:0b.0-3
[    3.784163] usbcore: registered new interface driver usbhid
[    3.784167] usbhid: v2.6:USB HID core driver
[    8.756475] usb-storage: device scan complete
[/PHP]

and the output for mouse using dmesg |grep mouse:
[PHP]stephen@stephen-desktop:~$ dmesg | grep mouse
[    1.937422] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.940670] mice: PS/2 mouse device common for all mice
[/PHP]

The mouse freezing occurs during normal use in Intrepid and Firefox 3.0.15 but occurs more quickly if I try to use any WINE app or if I try to access VMware 3.0 running a Win2K Guest on the Intrepid host.

I suspect that there is some conflict in the config files that may be reporting that one device is operating the mouse when in fact another has ownership of the mouse functions.

Any help or insights would be appreciated. If more information is required let me know and I'll do my best to post it.

**Note:**  
. The Ms Wireless Laser Mouse 5000 has a transmitter attached to a standard USB outlet. The mouse itself is powered by batteries.
. The Mouse is new and new batteries that work have been installed.
. I believe from what I have read that the MS BlueTrack system used in the mouse is essentially BlueTooth so I have installed all the "Bluez" related programs I could find in the repos.

---

### Post by Daddyo-613 on 2009-12-15
It happened again here is the relevant sections of my /var/log/syslog:

[html]Dec 15 11:27:52 stephen-desktop kernel: [ 6112.213193] ppdev0: registered pardevice
Dec 15 11:34:34 stephen-desktop kernel: [ 6513.856433] ppdev0: unregistered pardevice
Dec 15 11:34:34 stephen-desktop kernel: [ 6513.870462] device eth0 left promiscuous mode
Dec 15 11:34:34 stephen-desktop kernel: [ 6513.870475] bridge-eth0: disabled promiscuous mode
Dec 15 11:35:20 stephen-desktop init: tty5 main process (4517) killed by TERM signal
Dec 15 11:35:20 stephen-desktop init: tty4 main process (4516) killed by TERM signal
Dec 15 11:35:20 stephen-desktop init: tty2 main process (4520) killed by TERM signal
Dec 15 11:35:20 stephen-desktop init: tty3 main process (4521) killed by TERM signal
Dec 15 11:35:20 stephen-desktop init: tty6 main process (4522) killed by TERM signal
Dec 15 11:35:20 stephen-desktop init: tty1 main process (5699) killed by TERM signal
Dec 15 11:35:20 stephen-desktop compiz.real: *** glibc detected *** compiz.real: double free or corruption (!prev): 0x09529400 *** 
Dec 15 11:35:21 stephen-desktop bonobo-activation-server (stephen-6816): could not associate with desktop session: Failed to connect to socket /tmp/dbus-P1wSBB1zta: Connection refused
Dec 15 11:35:25 stephen-desktop bonobo-activation-server (stephen-6825): could not associate with desktop session: Failed to connect to socket /tmp/dbus-P1wSBB1zta: Connection refused
Dec 15 11:35:31 stephen-desktop kernel: [ 6571.405813] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Dec 15 11:35:31 stephen-desktop kernel: [ 6571.405821] apm: disabled on user request.
Dec 15 11:35:34 stephen-desktop vmnetBridge: RTM_DELLINK: name:pan0 index:5 flags:0x00001002 
Dec 15 11:35:34 stephen-desktop bluetoothd[5433]: bridge pan0 removed
Dec 15 11:35:34 stephen-desktop bluetoothd[5433]: Stopping SDP server
Dec 15 11:35:35 stephen-desktop bluetoothd[5433]: Exit
Dec 15 11:35:35 stephen-desktop avahi-daemon[4940]: Got SIGTERM, quitting.
Dec 15 11:35:35 stephen-desktop avahi-daemon[4940]: Leaving mDNS multicast group on interface vmnet8.IPv4 with address 192.168.226.1.
Dec 15 11:35:35 stephen-desktop avahi-daemon[4940]: Leaving mDNS multicast group on interface vmnet1.IPv4 with address 172.16.204.1.
Dec 15 11:35:35 stephen-desktop avahi-daemon[4940]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.152.
Dec 15 11:35:40 stephen-desktop exiting on signal 15
Dec 15 11:36:38 stephen-desktop syslogd 1.5.0#2ubuntu6: restart.[/html]As you can see there are some references to processes being stopped and bluetooth pan0 exiting. I hope this helps give someone an idea that might help me.

TTFN

---

