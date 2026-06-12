---
title: "Engenius 802.11b adapter"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by swa5000 on 2005-04-27
I have an Engenius NL-2511UB4 Mercury wireless 802.11b USB adapter, and I have no idea how to install it. Can anyone here help me? :|

---

### Post by az on 2005-04-29
Not knowing what chipset it is, perhaps you can use ndiswrapper.
First off, open a terminal, plug in your device and type 
dmesg
and post the last few lines.  It should show what hotplug says about your device.

---

### Post by swa5000 on 2005-04-29
I wasn't sure about how many lines you needed me to post, so I saved all of them in a .txt file. I also heard about something called wlan-ng and downloaded a DEB file called "linux-wlan-ng_0.2.0+0.2.1pre21-1_i386". Not sure how to install it or even if it is what I need. The kernel version of Ubuntu on my computer is 2.6.10-5-386, if that helps at all. I REALLY appreciate your help, by the way.

[Click here to access the TXT](http://abe.homestead.com/dmesg.txt)

---

### Post by az on 2005-04-30
"usb 2-1: new full speed USB device using ohci_hcd and address 6
usb 2-1: USB disconnect, address 6
usb 2-1: new full speed USB device using ohci_hcd and address 7
usb 2-1: USB disconnect, address 7
usb 2-1: new full speed USB device using ohci_hcd and address 8
abe@Abe:~$"

If it was the prism2 chipset, the module would have been loaded by hotplug.  You need ndiswrapper.

Install ndiswrapper-utils with synaptic.  The package is on your cd in Hoary,

Find the windows XP driver for your device (you need to find the inf file)

Open a terminal and go into the driver directory

cd Desktop
cd Driver
sudo ndiswrapper -i filename.inf
sudo modprobe ndiswrapper
then go into the networking tool and configure your device.  If all is well, add the word "ndiswrapper" to the end of /etc/modules so that it is loaded every time you boot.

sudo gedit /etc/modules

---

