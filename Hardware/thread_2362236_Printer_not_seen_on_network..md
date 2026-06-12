---
title: "Printer not seen on network."
date: 2017-05-25
forum: Hardware
---

### Post by jukingeo on 2017-05-25
Hello All, 

I have two computers set up on a network connection using Ubuntu Studio 16.04 64 bit.   My printer is an HP Photosmart C5580 All in one.  So it is a printer and a scanner.  In my previous set up with two machines on Ubuntu Studio 14.04, I was able to hook the printer up to one computer via USB and access it across the network on my other machine.    Now I got a new computer that is running US 16.04 and I upgraded my wife's machine to US 16.04 as well and now I cannot see the printer on my machine.  The printer can be seen on her machine (as it is hooked up to hers) and can print from it.  But I cannot see it anymore when I search for it on the network.

I would like to solve this issue.  I do not know if this is an issue because I switched to a 64 bit operating system, but I never had problems connecting to a printer across a network using the same OS on both machines.

Please assist.

Thank You,

Geo

---

### Post by jukingeo on 2017-06-20
Hello All,

I am still having this issue on my home system.   My wife's computer CAN print to the printer, but I cannot see it on my computer, we are both running Ubuntu Studio 16.04, 16 bit.

Again as I said above, I NEVER had problems accessing a printer across a linux network before I changed to 64 bit.  Could that be an issue?

Thank You,

Geo

---

### Post by gsahli on 2017-06-21
64 bit is not an issue.
So, do I understand correctly that you have the printer connected by USB to the other computer, and have it shared from that other computer? Sharing has to be enabled on her computer.
Read this:
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#Ubuntu_print_server](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#Ubuntu_print_server)

---

### Post by vocx on 2017-06-21
> **jukingeo said:**
> Hello All, 

I have two computers set up on a network connection using Ubuntu Studio 16.04 64 bit.   My printer is an HP Photosmart C5580 All in one.  So it is a printer and a scanner.  In my **previous set up with two machines on Ubuntu Studio 14.04**, I was able to hook the printer up to one computer via USB and access it across the network on my other machine.    Now I got a new computer that is running US 16.04 and I upgraded my wife's machine to US 16.04 as well and now I cannot see the printer on my machine.  The printer can be seen on her machine (as it is hooked up to hers) and can print from it.  But I cannot see it anymore when I search for it on the network.

I would like to solve this issue.  I do not know if this is an issue because **I switched to a 64 bit operating system**, but I never had problems connecting to a printer across a network using the same OS on both machines.

Please assist.

Thank You,

Geo
The change from 32 to 64-bit system means nothing. Most probably the reason is you changed from 14.04 to 16.04. Sometimes things are a bit different from one version to the next one.

How did you install the printer in the first place? Maybe you can repeat those same steps and see if it works.

Since you are using an HP printer I suggest you make sure you have HPLIP installed. HPLIP is the official collection of utilities by HP to provide support for their printers in Linux.
```
sudo apt install hplip
```

Your device seems to be supported
[http://hplipopensource.com/hplip-web/models/photosmart/photosmart_c5500_series.html](http://hplipopensource.com/hplip-web/models/photosmart/photosmart_c5500_series.html)

In machine A, directly connected to the printer, run the setup
```
hp-setup
```

Maybe it will ask you if you want to share the printer in the local network.

In machine B, run the setup as well. Depending on if the printer was correctly shared on the network, maybe you will be able to detect it by IP address or name.

I don't have your setup. I have an HP printer that is connected to the network directly, so it is accessible by all computers on the network. Maybe your printer can be connected like this as well. Instead of it being connected to machine A by USB, connect it directly to the router by an Ethernet cable, or by Wi-Fi, and run the setup on both machines.

---

