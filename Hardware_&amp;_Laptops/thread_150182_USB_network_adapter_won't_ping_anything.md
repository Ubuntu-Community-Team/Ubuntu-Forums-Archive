---
title: "USB network adapter won't ping anything"
date: 2006-03-25
forum: Hardware &amp; Laptops
---

### Post by rj686 on 2006-03-25
Hey guys i followed [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperH](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperH) owto
to set up my WUSB54G, i installed ndisgtk and ndiswrapper-utils no problem. I got my driver off the disk and everything looked like it was set up correctly. My wlan0 device is listed in System > Administration > networking so i thought all was good. I entered my ssid and such, but i still cant ping anything? Could someone help me?

---

### Post by jml on 2006-03-25
If you can see the USB device in your network manager, then we know you have the hardware issues sorted out.  That in itself is a major accomplishment for a USB device.  I'm assuming you have already activated the network device after configuring it.  Is the network you are trying to connect to encrypted?  If it is, temporarily turn off encryption and then try to connect.  If that works, then set up WEP encryption on both units and see what happens.  If you are trying to connect to a network encrypted with WPA then your life got more complicated.  You need to install and configure an application called WPA_supplicant, since Ubuntu does not support it out of the box.  Before you go too far, however, go to the WPA supplicant web site (just Google wpa_supplicant and one of the top hits will be the site) and make sure that the chipset your wireless device uses is supported by wpa_supplicant.  Hope that this helps.

Joe

---

### Post by rj686 on 2006-03-25
it does list a wireless device in my network manager, ill try turning off encryption to see if that works.....

is there a re-fresh network list button somewhere?

one more thing.... i dont have anything listed under dns servers....do i need to mess with that?

---

