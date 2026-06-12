---
title: "WIFI on acer aspire one"
date: 2009-10-26
forum: Hardware
---

### Post by CicPot on 2009-10-26
Hello dear friends,

I bought a used acer aspire one zg5 with Ubuntu 9.04 jaunty, kernel linux 2.6.2.8 - generic, Gnome 2.26.1 - and everything is ok but the WIFI...I am a novice in Linux but I know at least something...the wired lan network works fine but the WIFI is not working at all...the front wifi light is off and not showing at all...and I do not have even the possibility to run the wifi network search or even anything on the wifi manager...

I installed the wicd - and on icon it says there is no wireless connestion...also what is intresting when i looked at the preferences the wire interface is eth0 and the wireless has a blank space - also the WPA driver is WEXT...



I am freaking out so I would greatly appreciate any kind off help

sudo lspci
[sudo] password for nesib: 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

regards

---

### Post by ScarySquirrel on 2010-04-24
Do you have the windows driver pack cd for this beast? 
If you do, look into a program called 'ndiswrapper'. 
To use: 
 Put the driver cd in the cd drive.
 Find "Windows Wireless Drivers" in your installation menu. 
 Run it like a bunnit. 
 click "install new driver" (button has a shiny + on it. Seriously, if you miss it you are a retard or have a corrupted install image)
 Click button for browsing. 
 Browse to the .inf file on the driverpack cd for the XP wireless driver. 
 TA ****ing DA!

You're welcome.

Ndiswrapper Screenshot (this is to help you find the "install new driver" button): 
[IMG]http://icanhascheezburger.files.wordpress.com/2007/09/128338556871093750ctrlaltdelda.jpg[/IMG]

---

