---
title: "at76c503a, the WUSB11, and no interface name"
date: 2005-06-25
forum: Hardware &amp; Laptops
---

### Post by OwlManAtt on 2005-06-25
Howdy folks, 

I recently aquired an old iBook Clamshell without an airport card. Since those airport cards were rather pricey, I opted for a Linksys WUSB11 USBv1.1 wireless adapter. I did a bit of preliminary research before I ordered it, and it seemed to function under Linux, so I ordered away.

Today, my package containing the WUSB11 arrived. I opened it up, plugged it in, and hoped that it would Just Work. Having used Linux for some time, however, I knew it wouldn't Just Work (and it didn't!), so I got to work compiling the kernel module for it.

I used the module found here: [http://at76c503a.berlios.de](http://at76c503a.berlios.de). I have kernel headers and kernel source installed, so it compiled happily. I issued make install, then plugged my WUSB11 in.

No beans. It didn't load the modules that googled claimed it required. So I helped it along and issued a modprobe or two. The modules loaded and dmesg has some stuff about three amtel things loading (firmware looking stuff). 

So I went in to the GNOME networking thing, and the wireless device does not show up. I issued iwconfig, and nothing has a wireless extension. 

I looked here: [https://wiki.ubuntu.com/MyIBookClamshellAndMe](https://wiki.ubuntu.com/MyIBookClamshellAndMe) and didn't find much help. (By the way, I tried it with and without the modification that he suggested to the kernel source file, both produced the same results). 

It would appear as if I'm having the same problem as the last two chaps to post on this thread: [http://ubuntuforums.org/showthread.php?t=14030&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=14030&page=1&pp=10) had. I've done everything to the letter, yet I see no interface. The WUSB11 has the power light activate when I plug it in, so I'm guessing my unit is not the problem here. (Or at least, it isn't defective.)

Any help would be appreciated by myself and probably those two chaps from the other thread. 

Regards!


EDIT: I just noticed something else in dmesg that may be relevant.

'divert: not allocating divert_blk for non-ethernet device sit0'

However, according to iwconfig, there is no wireless extension for 'sit0'.

---

### Post by az on 2005-06-25
I just bought one of those on ebay for a buck and it works better than my dwl-122!


I compiled the berlios drivers (they are included in the Breezy kernel... Stay tuned)

I used the debian package option and make them into a deb package and installed that.

I cannot cold plug the device (boot with it plugged in - the firmware does not load) but when I hotplu, I get an iwconfig device.

Once the module is loaded, I can configure the interfacein the networking tool, or just do

sudo dhclient wlan0

by hand.  I actually cannot do this because I have a wep key...

---

### Post by az on 2005-06-25
Here is that package I made...



apqi.com/ubuntu/at76c503a-modules-unknown_0.10.99.beta5+unknown_i386.deb

---

### Post by az on 2005-06-25
I just tried it on another machine:

Jun 25 14:59:33 localhost kernel: usb 2-1.2: new full speed USB device using ohci_hcd and address 5
Jun 25 14:59:33 localhost kernel: usb 2-1.2: new full speed USB device using ohci_hcd and address 6
Jun 25 14:59:35 localhost usb.agent[14328]:      at76c503-rfmd: can't be loadedJun 25 14:59:35 localhost usb.agent[14328]: missing kernel or user mode driver a t76c503-rfmd
Jun 25 14:59:35 localhost kernel: /usr/src/modules/at76c503a/at76_usbdfu.c: USBDevice Firmware Upgrade (DFU) handler v0.12beta22-fw_dwl loading
Jun 25 14:59:35 localhost kernel: /usr/src/modules/at76c503a/at76c503.c: Generic Atmel at76c503/at76c505 routines v0.12beta22-fw_dwl
Jun 25 14:59:35 localhost kernel: at76c503_rfmd: Unknown symbol release_firmwareJun 25 14:59:35 localhost kernel: at76c503_rfmd: Unknown symbol request_firmware


I will install the firmware package...

---

### Post by OwlManAtt on 2005-06-25
Your package will not work for me, it's an iBook. PowerPC, not x86. =/

I've tried various methods of plugging it in (plug it in once the system it up, plug in and reboot, etc).

In my googling I think I may have found the problem - I am using a WUSB11 v4. Currently, there appears to be no support for the WUSB11 v4 beyond ndiswrapper.

And since it's powerpc, ndiswrapper is apperantly not an option (or so claims IRC). 

I don't know what to do now.

---

### Post by az on 2005-06-25
[QUOTE=OwlManAtt]Your package will not work for me, it's an iBook. PowerPC, not x86. =/

I've tried various methods of plugging it in (plug it in once the system it up, plug in and reboot, etc).

In my googling I think I may have found the problem - I am using a WUSB11 v4. Currently, there appears to be no support for the WUSB11 v4 beyond ndiswrapper.

And since it's powerpc, ndiswrapper is apperantly not an option (or so claims IRC). 

I don't know what to do now.[/QUOTE]

Bummer.  I am sorry I did not notice that you were on PPC.  I notice that the driver is only included in 486, 686 and k7 kernel in breezy, too.  Sorry.


Insofar as my problem with the other machine, it would seem than the dirver likes using wlan0 and I already had another device on wlan0.




Wanna crappy dwl-122?  They work on PPC...

---

### Post by OwlManAtt on 2005-06-25
Ugh. The driver itself works on PPC, however, it does not support the v4.

I've e-mailed the maintainer of the driver and asked about support for it. We shall see what happens...

---

### Post by kaaredyret on 2005-06-26
I have a Linksys '**Instant Wireless USB Network adapter ver 2.6**' attched to my Windows 2000 desktop pc; this machine acts as an ICS host for my laptop (Acer TravelMate 290E) using a network cable, switch etc.

I installed Ubuntu on the laptop about one month ago and I am *VERY* new to Linux, but not helpless. I understand that on Ubuntu I am looking forward to anything else than instant wireless :)

I have read a 1000 posts about this NIC, but it is still not clear; **is it supported in Hoary at all... or more important, will it be in Breezy?**

I am not afraid of a little configuration file editing and command line interface, but compiling kernels is just too advanced for me... and I am too busy these days to be able to spend hours on frustrating configuration tasks; aaand the laptop IS connected to the internet via the ICS, so I CAN wait for breezy.

But... it would be nice to be able to skip the ICS and power off the damn noisy old desktop pc.  ;-) 

TIA!

This is my NIC: [LinkSys WUSB11 ](http://www.linksys.com/international/product.asp?coid=143&ipid=91)

---

### Post by ncrr on 2005-07-07
The ATMEL firmware did not work for me with my Linksys WUSB11V26. It took me two days to figure it out and I finally managed to get a Linksys WUSB11V26 working with Hoary Hedghog 5.04. I installed the ndiswrapper-utils, downloaded the Windows 98 drivers for this Wireless USB from Linksys Support website, and was able to get it working. Here are the steps:

1. sudo apt-get install ndiswrapper-utils (to install the ndiswrapper-utils)

Download the driver from Linksys.Be sure to download the drivers. Do this on a Windows machne if possible since this is an exe file and creates its own directories. Go to the folder where the drivers were extracted and copy this folder to a folder in your Desktop on Ubuntu.

Open a terminal and do:

cd /home/USERNAME/Desktop/Drivers (or any other folder you have created)
sudo ndiswrapper -i NETUSB.INF
sudo ndiswrapper -l
(This should list the driver)

sudo -m netusb

edit the file /etc/network/interfaces as follows:
# iface eth0 inet dhcp (My PCI wired card is disabled here)
auto wlan0
iface wlan0 inet dhcp (I use DHCP on my network)
wireless_keymode restricted
wireless_key XXXXXXXXXXX (Replace with your Wireless Key)
wireless_essid XXXXXXXX (Replace with your SSID from Router)

 Shutdown; conect your WUSB11v26 and you should be set.

I am thrilled that I finally got this working. I was almost beginning to give up.

 :grin:

---

### Post by kaaredyret on 2005-07-12
**Thank you!** I will give it a try later today. Almost can't wait!  :razz:

Two questions:
(1)
# iface eth0 inet dhcp (My PCI wired card is disabled here)

Do I have to disable eth0? I will not use it at home, but possibly somewhere else (and in that case the linksys NIC will be unplugged).

(2)
sudo -m netusb

Something is missing? ndiswrapper -m?

TIA!

---

### Post by kaaredyret on 2005-07-12
> Download the driver from Linksys.Be sure to download the drivers. Do this on a Windows machne if possible since this is an exe file and creates its own directories. Go to the folder where the drivers were extracted and copy this folder to a folder in your Desktop on Ubuntu. 

I did this as above, answered question 2 myself:

sudo ndiswrapper -m

But when booting something goes wrong. In the network settings I see no wlan0 interface, only my eth0. That is not a  good sign, eh?  :neutral:

---

