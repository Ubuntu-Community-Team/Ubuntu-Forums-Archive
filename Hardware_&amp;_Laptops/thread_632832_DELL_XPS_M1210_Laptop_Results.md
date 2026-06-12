---
title: "DELL XPS M1210 Laptop Results"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by HDave on 2007-12-05
After 6 weeks of reading and experimenting I have everything I care about on my Dell XPS M1210 Laptop working in Ubuntu 7.10 Gutsy.  Many thanks to the Ubuntu community and the Ubuntu laptop testing team. If you haven't already check out  [https://wiki.ubuntu.com/LaptopTestingTeam]("https://wiki.ubuntu.com/LaptopTestingTeam")

Hope this helps somebody.  Here's the results:


Worked out of the box:
	Laptop Keyboard
	Laptop Touch Pad
	Laptop Media Player Keys
	USB Mouse(s)
	USB Keyboard(s)
	Hi-Definition Audio (Sound)
	BlueTooth (didn't test this much though)
	Built-in Broadcom 100mbps Ethernet
	PC Express Card: Belkin Gigabit Ethernet Adapter


Didn't work, don't care:
	Video Camera
	Microphone
	Modem
	Suspend
	Hibernate



Everything else ----------------------------------------

Wifi:
	Not recognized, found it as a PCI device in prefs->hardware info (lspci works too)
	Installed ndiswrapper-utils-1.9 package around proprietary driver
	Broadcom BCM4328 (Vendor = 0x14E4, Product = 0x4328)
	NOTE: network manager doesn't work for hidden (not broadcast) SSIDs...Bug #50214

NVIDIA Geforce Go 7400:
	Activated restricted repository
	Installed nvidia-glx-new

External Monitor (with Laptop Screen Off, not Dual-View):
	Did not work, had to use "nvidia-settings" program to enable
	NOTE: don't install nvidia-settings package...program is available with restricted drivers
	NOTE: Screens and Graphics applet will break xorg.conf and set you back big time!
	NOTE: Fn-F8 key could not get to work, have to reboot to switch modes

Verizon Wireless Internal 5700 Mini EVDO Card:
	Not recognized, found it as a USB serial device in prefs->hardware info (lsusb works too)
	Device is Novatel Wireless EXPD CDMA (Vendor = 0x413C, Product = 0x8114)
	This URL has exact instructions: [http://www.savvyadmin.com/2007/06/03/ubuntu-dell-5700-evdo/]("http://www.savvyadmin.com/2007/06/03/ubuntu-dell-5700-evdo/")
	NOTE: Gnome network manager keeps renaming interface to ppp0, use this name instead of "verizon" as instructions in link suggest.

---

### Post by Slingshot on 2007-12-20
Hi, I have a M1210 with nvidia 7400 card. Almost all worked out of the box for me even the webcam works under Skype by changing the resolution settings and I am now happily Windows free at last :)

**What didn't work**
Suspend/Hibernate

**Not tested yet**
Modem (should work as Dell has support for this under edgy)
Card reader

My only problem with this machine is the webcam gets hot even when not in use.

---

