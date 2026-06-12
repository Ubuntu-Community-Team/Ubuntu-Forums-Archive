---
title: "Configuring Wireless card on Acer/ card: INPROCOMM IPN 2220 LinkSys"
date: 2006-01-16
forum: Hardware &amp; Laptops
---

### Post by psylvester on 2006-01-16
Hi,
Im using INPROCOMM wireless card with Acer 2300.Im trying to setup wireless on ubuntu, but everytime I fails. Im using Xp/ubuntu (dual boot). On Xp I can access wireless but ubuntu fails.
Kernel is 2.6
In Device Manager I can see the Wireless card, but its not avialable in networking - where we configure LAN.

Please, Help is req at the earliest.
I would appreciate help, 
Thanks in advance.
P Sylvester
Bangalore, IND.
Ph: +91-9886600666

---

### Post by wolf359 on 2006-01-26
Hi
My notebook/laptop uses the same wireless device. Have you tried using your windows drivers with Ndiswrapper? I have been using it with Suse 10 on my Toshiba L10 for a while now and it works without problem. I found that setup was easier in Linux than with Windows.
I hope this helps

---

### Post by apt on 2006-05-01
How did you manager to get WiFI working|. I've tried everything to get this working on my L10 , I've managed to get the windows wifi driver installed using ndiswrapper and it is recognised by the hardware but everytime I try and load the driver is gives me an error in the log something about not being able to load the driver.

Ay suggestions?

Regards

Adrian

---

### Post by patrickfromspain on 2006-05-01
you must use ndiswrapper, to load the windows drivers. Install ndiswrapper-utils and copy your drivers to the desktop.

Open a terminal:

cd Desktop
sudo ndiswrapper -i driver_name.inf
sudo ndiswrapper -l (L not 1 or I) to see if it's correctly installed, you should see hardware present, driver present.
sudo ndiswrapper -m
sudo modprobe ndiswrapper and now it should appear in the networking section.

---

### Post by apt on 2006-05-01
I have done exactly that process and get as for as hardware presnet, driver present but when I continue the process and then check my log I get an error saying driver not able to load (not the exact error message).

I have never have the Wifi adpater available as a network device, only Ethernet and Modem. :(

Its actially a work laptop so I will try your EXACT instructions tomorrow.

Many Thanks

Adrian

---

### Post by apt on 2006-05-02
No its a no go.... Tried exactly as you said and it doesnt appear in available networks but is hardware and driver are present when using ndiswrapper -l.

Did I mention I was trying this with Dapper?

Adrian

---

### Post by Titus A Duxass on 2006-05-02
You have a couple more tasks to do before you will be successful.

1. Add ndiswrapper to /etc/modules (do at CLI)
2. Edit /etc/network/interfaces to add wlan0 (do a search on these forums for an example)
3. Do a cold reboot.

---

### Post by apt on 2006-05-02
I'm pretty new the Ubuntu could you take me through these steps?

Many Thanks

Adrian

---

### Post by wolf359 on 2006-05-08
**I use Suse Linux 10.0 on my Toshiba L10 and know that ndiswrapper software works with  LinkSys INPROCOMM IPN 2220 device. I have copied the suse install docs here. I believe that the setup would be the similar for Ubuntu, but no guarantees.**

Ensure the following:
_The ethernet device is only enabled when cable is plugged in._
_The wireless device is enabled using the button on front of machine._:rolleyes: 

Setting up ndiswrapper with SUSE Linux 10.0 requires the following steps:

(1) Get an NDIS driver for your wireless network adapter. *(I used the Toshiba WINXP driver files supplied with the machine)*. See [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/) for lists of supported chipsets and driver links.

(2) Each driver consists of a <driver>.inf file and one or more DLLS. *(Change to the directory _where the driver files have been saved_)*. As superuser, install the driver with "ndiswrapper -i <driver>.inf". This copies the driver to a directory below /etc/ndiswrapper/.

(3) Load the ndiswrapper module with "modprobe ndiswrapper". The system log /var/log/messages will indicate success or failure.

(4) To ensure that ndiswrapper will always use the same network interface name, call "ndiswrapper -m". This step is optional; usually ndiswrapper will not change to a different interface.

(5) Configure the wireless network adapter in YaST, Network Devices, Network Card. Choose "Other", Device Type = Wireless, Configuration Name = 0, Module Name = ndiswrapper. Leave the other fields to their defaults. Configure the wireless settings.

I hope that this info is of help, but as I have said I cannot guarantee it, if in any doubt further reading of the docs supplied with ndiswrapper is advised.

---

