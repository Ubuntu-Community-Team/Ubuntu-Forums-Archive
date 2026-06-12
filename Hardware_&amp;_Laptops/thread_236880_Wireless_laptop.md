---
title: "Wireless laptop"
date: 2006-08-15
forum: Hardware &amp; Laptops
---

### Post by thekeeper on 2006-08-15
Hello, i have a laptop Asus z92j with ipw3945, network admin detected my wireless card, and wireless assitang to, but, i cant connect, i dont know why.

And i have wireless usb (usb key) , i installed this one with Ndiswrapper and its ok, but, i cant connect, the two card detecte wireless conexion but i cant connect.

My connection its open without wep and wpa.

lspci : 

0000:03:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)

iwconfig 

eth1      unassociated  ESSID:off/any
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


thanks for all

---

### Post by meng on 2006-08-15
Things to try (in order)
iwconfig eth1 essid [ESSID name]
ifconfig eth1 up
dhclient eth1

---

### Post by thekeeper on 2006-08-15
Listening on LPF/eth1/00:13:02:38:07:ae
Sending on   LPF/eth1/00:13:02:38:07:ae
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

](*,) thank but dont work :confused:

---

### Post by meng on 2006-08-15
Bummer.

I had assumed that your router was assigning DHCP leases, but if it's a static IP thing then dhclient isn't applicable.

Sorry, that's the limit of my knowledge.

---

### Post by chocbar31 on 2006-08-15
First, looks like a driver issue. Unknowd device is an unknown driver. Just because you detect the device does not mean the driver is detected. There is a difference in the two.

I also have a USB device, and what works for me in connecting is this: (Unplug your USB device and then reboot. Wait until you reach your desktop and then plugin your device.

Otherwise you will need to do a search on ndiswrapper's website for your brand and also a search on how to get it up and running. Here [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

You also may want to visit this site for quick assistance. [http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/)

Another good thing to do is to go to firefox's extension/addon site and add the Ubuntu Forums.xpi. Also a good place for support. It will install as a menu list in your firefox browser and give you direct access to solving most issues and other info about Ubuntu and Linux.

](*,)

---

