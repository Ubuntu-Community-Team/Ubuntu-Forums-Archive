---
title: "Intel &quot;My Wifi&quot; Wpan"
date: 2010-01-20
forum: Hardware
---

### Post by aquabanianskakid on 2010-01-20
I have an Intel Wifi Link 1000. It works great in Ubuntu. However it supposedly can connect to your router and then allow other devices to connect to it using a wifi wpan network at the same time, so that other wireless devices can share internet connectivity. Does anyone know if or how this can be used in ubuntu?

---

### Post by Awadi on 2010-04-27
I have exactly the wifi device but not sure what you talking about.
Please provide more information regarding the feature "wifi wpan" does it work with windows ??? if it works with windows i'm sure there's a way to get it to work in Ubuntu.

---

### Post by aquabanianskakid on 2010-04-27
They call it "Intel My wifi technology". That is about all I can tell you. I removed windows from my machine as soon as I bought it so I've never tried this feature on windows. They have a short explanation at this link.

[http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=3141&DwnldID=17045&lang=eng&iid=dc_rss]("http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=3141&DwnldID=17045&lang=eng&iid=dc_rss")

[http://www.intel.com/network/connectivity/products/wireless/adapters/1000/index.htm]("http://www.intel.com/network/connectivity/products/wireless/adapters/1000/index.htm")

Apparently the feature is on more than one chipset and allows you to use your machine somewhat like a wireless router. Couldn't find a better explanation and I was wondering if anyoe else had a clue as to what it was.

---

### Post by akshay2000 on 2011-04-02
It seems a bit old thread but in case anyone drifts here, here's the info about Intel My WiFi. It let's you share your PC's internet connection with other WiFi enabled devices. It makes your laptop work like a WiFi hotspot. However, I am wondering how to do it in Ubuntu.

---

### Post by nghalion on 2011-08-12
Same issue here. Did you manage to get it work in Ubuntu 11.04?

---

### Post by akshay2000 on 2011-08-13
> **nghalion said:**
> Same issue here. Did you manage to get it work in Ubuntu 11.04?

In case you were referring to me, no! I didn't try, but it should work by simple ad-hoc network. Anyway, I've left Ubuntu already. Sure, post it here if you get it working!

---

### Post by adamp_825 on 2011-08-28
**+1** -- I would also like to know if there is any support (planned?) for Intel's "My WiFi Technologies".

BTW, "My WiFi Technologies" is more than an ad-hoc network, apparently (see the links a couple of pages up).

---

### Post by satyaog on 2012-01-19
+1 would be great

---

### Post by grahammechanical on 2012-01-19
I have not checked the links but it could be that this is referring to something called AP or Access Point mode.

A router is an Access Point. When a computer is in Infrastructure mode it can connect to the router and use the router as an Access Point to connect to other computers that are connected to the router. As well as connecting to the Internet itself through the router.

Computers in Ad-hoc mode can connect by wireless to each other without the need for a router.

A computer with the right kind of wireless adapter can be put into AP or Access Point mode in which case other computers can by wireless connect to this computer and through it to the router/modem that connects to the internet.

The wireless adapter on my motherboard is capable of AP-Access Point mode and if I was using Windows I could use the drivers that came with the motherboard to set the computer as an Access Point.

Ubuntu at the moment does not have an easy way of doing the same thing. But I am testing 12.04 and in System Settings there is a utility called Network and when I select my wireless connection I get a button that says "Use as Hotspot." I think that this will set up the machine in AP mode.

I have not tried this because I have no need to. Likewise, I have not tried the Aeroplane Mode on/off slider.

This is how to do it the hard way if you cannot wait until the end of April:

[http://www.su-root.eu/computing/turn-your-linux-computer-in-a-wireless-access-point-using-hostapd]("http://www.su-root.eu/computing/turn-your-linux-computer-in-a-wireless-access-point-using-hostapd")

Regards.

---

