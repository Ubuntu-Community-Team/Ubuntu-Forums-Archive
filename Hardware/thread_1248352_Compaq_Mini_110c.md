---
title: "Compaq Mini 110c"
date: 2009-08-24
forum: Hardware
---

### Post by Filippo on 2009-08-24
Hi,
I have installed Ubuntu 9.04 Netbook Remix on Compaq Mini 110 , here there
is the lspci :

```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
02:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)

```

Wired nic (atl1e) doesn't work out of the box (as expained here : [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#HP%20Mini%20110%20/%20Compaq%20Mini%20100c](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#HP%20Mini%20110%20/%20Compaq%20Mini%20100c)) so i have compiled the driver, 
but I have still problems with audio.
I have still tried with alsa-driver-linuxant_1.0.20.3_all.deb.zip or this with fix [https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/175](https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/175) 
but it's still not working ...

Any suggestion ?

thanks

Filippo

---

### Post by Filippo on 2009-08-24
Now everything works :)

steps:
1. install latest ubuntu netbook remix (9.04)
2. video, wifi and Fn keys are working out of the box
3. download NIC driver [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) (AR81Family)
   ```
tar -xzvf AR81Family-linux-vXXXXX.tar.gz
cd src
make
sudo make install
sudo insmod atl1e.ko
```
4. for audio Driver, use the default kernel and install [http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.20.3/alsa-driver-linuxant_1.0.20.3_all.deb.zip](http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.20.3/alsa-driver-linuxant_1.0.20.3_all.deb.zip) 
5. reboot and unmute.

the system is up and running.

Thanks to [https://wiki.ubuntu.com](https://wiki.ubuntu.com) contributors

---

### Post by gnu.enri on 2010-02-18
> **Filippo said:**
> Now everything works :)

steps:
1. install latest ubuntu netbook remix (9.04)
2. video, wifi and Fn keys are working out of the box
3. download NIC driver [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) (AR81Family)
   ```
tar -xzvf AR81Family-linux-vXXXXX.tar.gz
cd src
make
sudo make install
sudo insmod atl1e.ko
```
4. for audio Driver, use the default kernel and install [http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.20.3/alsa-driver-linuxant_1.0.20.3_all.deb.zip](http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.20.3/alsa-driver-linuxant_1.0.20.3_all.deb.zip) 
5. reboot and unmute.

the system is up and running.

Thanks to [https://wiki.ubuntu.com](https://wiki.ubuntu.com) contributors
HI !

I have a mini 110c and i had the same problem with the audio, but i installed ubuntu 9.10 and everything is running now !! !!

Only one advertisement, the wireless did not work, I had to install the "These package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware." a driver not free, you can install it or the free one in "System" >"administration"> "hardware drivers" (you need internet, so with a wire).

buona fortuna per tutti
ciao

---

### Post by binary_dreamer on 2012-08-24
Does all the above apply to ubuntu 12.04? the wifi manager says that there is a firmware missing.

---

