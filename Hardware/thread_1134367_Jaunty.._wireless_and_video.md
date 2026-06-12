---
title: "Jaunty.. wireless and video"
date: 2009-04-23
forum: Hardware
---

### Post by marco1989 on 2009-04-23
Hello... I've a januty question:

wireless -> Atheros Communications Inc. AR928X
video -> Ati Radeon HD 3400

Them work with Jaunty Jackalope? With wich driver?
On Intrepid them worked but with some problem..

---

### Post by The2DQuartet on 2009-04-29
> **marco1989 said:**
> Hello... I've a januty question:

wireless -> Atheros Communications Inc. AR928X
video -> Ati Radeon HD 3400

Them work with Jaunty Jackalope? With wich driver?
On Intrepid them worked but with some problem..
I have a Fujitsu Siemens Amilo Pa 3553 with Atheros 9281 wireless-N card (Ralink RT2860 chipset) and an ATI Radeon HD 3400 graphics card. I've just upgraded to Jaunty from Hardy (skipped Intrepid because of compatibility issues with this computer).

Graphics card works OK with the proprietary driver suggested by Ubuntu, although from experience I would recommend getting the [Linux driver installer]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English") from the ATI website. I had some flickering issues at first which were resolved by switching this driver.
For some reason I wasn't able to install a driver using EnvyNG, which kept hanging when trying to find a driver.

WLAN works and picks up lots of networks, however I can't connect to my own wifi. The password is rejected over and over again. I can connect to it using Vista on the same laptop, so I don't yet know whether it's Ubuntu or the router which has the problem. Out of interest, it's an old Belkin G cable router using WPA2. When I have time I'll try a few different settings on the router and also try the laptop on other routers and see if anything works.
My old desktop (just got rid of it last weekend) had a Belkin G+ wireless card which worked fine on Ubuntu Gutsy and Hardy on the same router with the same settings.

A final word of warning to anyone using an Amilo Pa 3553, or other similar laptops (I don't know how many models this affects):
When I bought the laptop, the wireless was always off by default and the Fn+F1 hotkey launches an app in Vista to switch it on. Rebooting always switched it off, and the BIOS settings didn't allow setting it to be on at startup.
There's a BIOS update available online from [Fujitsu support]("http://support.ts.fujitsu.com/com/support/downloads.html") which sets the wireless to be on at startup by default, but IIRC it needs to be found and installed using a Windows app downloaded from the site.

---

