---
title: "Easy-Peasy Wireless w/ Ubuntu (Debian) Linux"
date: 2005-11-17
forum: General Help
---

### Post by Czar on 2005-11-17
In this brief (forum) entry I will reference the steps it takes to provide a wireless network connection, that is function on both Linux 2.6 and Windows, using a [Belkin Wireless G USB Network Adapter](http://catalog.belkin.com/IWCatProductPage.process?Merchant_Id=&Section_Id=201522&pcount=&Product_Id=179211).  This is basically my first attempt to even use wireless networking yet everything is very clean cut (for the most part).

[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)
Or Digg it at [http://digg.com/linux_unix/Easy_Peasy_Wireless_w_Ubuntu_Debian_Linux](http://digg.com/linux_unix/Easy_Peasy_Wireless_w_Ubuntu_Debian_Linux)

---

### Post by GameGod on 2005-11-17
Nice HOWTO!
How about simplifying a bunch of that driver installation by installing "ndisgtk" through synaptic? (It's a graphical config tool for ndiswrapper...)

---

### Post by Czar on 2005-11-18
[QUOTE=GameGod]Nice HOWTO!
How about simplifying a bunch of that driver installation by installing "ndisgtk" through synaptic? (It's a graphical config tool for ndiswrapper...)[/QUOTE]

Dear GameGod,

Thank you.  ndisgtk is also a nice suggestion, yet at the time of this tutorial I was without any network connection and everything above (other then the recommenced wifi tools) are available on the local CD-Rom. ;-)

---

### Post by Zotova on 2005-11-27
In this scenario it would be better to use the native Linux driver for the belkin wireless device.

[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)

As a native Linux driver will work better than a Microsoft driver on steroids.

---

### Post by Czar on 2005-11-27
[QUOTE=Zotova]In this scenario it would be better to use the native Linux driver for the belkin wireless device.

[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)

As a native Linux driver will work better than a Microsoft driver on steroids.[/QUOTE]

Ah!  Thanks for the link...

---

### Post by hhh on 2005-12-23
Awesome, thank you so much. This should be stickied in the Networking forum as well.

---

### Post by bootsie on 2005-12-27
Thank You! I'm a newbie to linux and was quickly becoming frusterated with my lack of success after hours of reading ideas and trying to download and install drivers and tweak my network settings to get my belkin wireless adapter going on my desktop. Following your steps got me up and running in minutes! 

-bootsie

---

### Post by NeoFax on 2006-01-13
I am having problems setting this up with WPA.  I am using wpa_supplicant and I can see the AP, but it is not accepting the key.  Also, I do not know if it makes a difference, but I have a version 2.011 usb Belkin nic.

---

### Post by Czar on 2006-01-17
[QUOTE=NeoFax]I am having problems setting this up with WPA.  I am using wpa_supplicant and I can see the AP, but it is not accepting the key.  Also, I do not know if it makes a difference, but I have a version 2.011 usb Belkin nic.[/QUOTE]

Dear NeoFax,

You are going to want to enable AP Broadcast on your Wifi router.  Also, verify your **/etc/default/wpasupplicant**;

```
# ATTEMPT BELKIN 54G WPA ENABLED
ENABLED=1
OPTIONS="-i wlan0 -D ndiswrapper -c /etc/wpa_supplicant.conf -w"
```

* Also see; [Ubuntu/Debian WPA Wi-Fi w/ Belkin Adapter](http://czarism.com/ubuntu-debian-wpa-wi-fi-w-belkin-adapter)

---

### Post by marco51 on 2006-01-26
Czar
very nice how-to.  However (anyone?) I have the following issues:
I run on Ubuntu Live CD and when I try to remove the cd to insert the drivers cd the drive won't open.  I presume because that is the filesystem.
So I copied the drivers to a floppy, but for some reason I cannot mount the floppy drive.  It shows in "computer" but cannot browse it and if i try to mount the volume it returns error "unable to mount selected volume"
ANy suggestions for a complete newbe?
thanks

---

