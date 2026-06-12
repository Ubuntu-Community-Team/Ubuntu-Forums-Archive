---
title: "need websites for driver downloads for ndiswrapper"
date: 2010-01-02
forum: Hardware
---

### Post by ddrury on 2010-01-02
I was using Kubuntu on my laptop and wireless worked fine. I installed Xubuntu on my laptop so it will run faster and now wireless doesn't work. I have been reading up on Ubuntu wireless. I have installed ndiswrapper and need the drivers to install for my wireless card. I followed a link posted on sourgenet, but the FTP site would not open. I have searched but not found the .exe file that I need in order to extract the .sys and .inf files that I need.

I have an Intel Pro/Wireless 2200 BG wireless card. I cannot find a website to get the needed .exe file to get the drivers that I need. I am fairly new to Linux so I am in need of some help. Does anyone know of a website to get the downloads?

Thanks

---

### Post by prshah on 2010-01-02
> **ddrury said:**
> I have an Intel Pro/Wireless 2200 BG wireless card. 

This card is natively supported in Ubuntu by the ipw2200 module. You do not need to install ndiswrapper.

What exactly is the difficulty you are facing? 

You can check if the driver (module) is active by opening the Terminal (Applications-Accessories-Terminal) and giving the command```
lsmod|grep ipw2200
``` You should also check if wireless extensions are working for the interface in question with the command```
iwconfig
```

Please post back with the output and a description of your problem for more specific troubleshooting.

---

