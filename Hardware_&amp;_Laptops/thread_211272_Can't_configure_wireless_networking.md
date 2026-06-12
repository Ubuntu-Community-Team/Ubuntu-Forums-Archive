---
title: "Can't configure wireless networking"
date: 2006-07-08
forum: Hardware &amp; Laptops
---

### Post by PryGuy on 2006-07-08
Hello everybody!
There's a little problem with my wireless PCIMCIA card DLink DWL-G650, but I don't think it matters what type of hadware I have because it seems that I just don't know how to configure a wireless card under Ubuntu. Here's what I do: I open the "Networking" applet choose Wireless connection. Connection is active, It sees the Network name of my network (that proves that adapter works, right?), I type in the WEP key and configure the static IP address. The only question about that is: I'm not sure what Key type should I choose, Plain(ASCII) or Hexadecimal, though they both do not seem to work.;)
So I set it up, close the applet and try to find some PCs in my Windows network and I fail. It sees my notebook only and it is in the "mshome" network though my network is called "workgroup". It Doesn't see PCs if I try to connect to them in the following way: "smb://192.168.0.1". I have a feeling that I do something wrong, but what? please help!

---

### Post by PryGuy on 2006-07-08
I've fixed it!!! I have set WEP security type on my D-Link wireless router and it worked. One question, does Ubuntu support other wireless security types out of the box, 'cause I have Windows machines in my network and they seem to work with WPA and WPA-PSK only?

---

### Post by PryGuy on 2006-07-08
Hello! Somebody? Anybody???:)

---

### Post by pitkali on 2006-07-08
> **PryGuy said:**
> I've fixed it!!! I have set WEP security type on my D-Link wireless router and it worked. One question, does Ubuntu support other wireless security types out of the box, 'cause I have Windows machines in my network and they seem to work with WPA and WPA-PSK only?

I heard that Dapper should support WPA security after installing network-manager from packages.

And I don't believe your windows machines do not support WEP. They actually support WPA out of the box only since XP SP2. WEP is there since the very beginning.. It's rather configuration problem. In that case try removing your wireless network from the list of known networks (somewhere under properties of the wireless connection..). Then refresh list of wireless networks and connect.

Regards,

---

### Post by PryGuy on 2006-07-08
No, my windows boxes do support WPA and WPA-PSK. It's Ubuntu that doesn't support WPA.:confused: I will try to play with Windows settings, thank you!

---

### Post by tturrisi on 2006-07-08
Your dlink is probably an atheros chipset (madwifi drivers) & I believe there are some bugs w/ madwifi & WPA.  However, to use WPA you need to configure wpa-supplicant.

---

### Post by pitkali on 2006-07-08
> **PryGuy said:**
> No, my windows boxes do support WPA and WPA-PSK. 
Sorry - I made a typo. I don't believe in Windows not supporting WEP.

---

### Post by sylverwing on 2006-07-08
Read this. Maybe this can help you.

[http://www.ubuntuforums.org/showthread.php?t=125150&highlight=networkmanager](http://www.ubuntuforums.org/showthread.php?t=125150&highlight=networkmanager)

---

### Post by CoolGui on 2006-07-08
> **sylverwing said:**
> Read this. Maybe this can help you.

[http://www.ubuntuforums.org/showthread.php?t=125150&highlight=networkmanager](http://www.ubuntuforums.org/showthread.php?t=125150&highlight=networkmanager)


If you can't get network manager to work reliably, I found that someone had posted detailed instruction how to do it for the madwifi drivers, and it worked for me.  :D

[http://comphobby.org/archives/14-More-Ubuntu-WPA-PSK-From-A-Joe-Sixpack-Perspective.html](http://comphobby.org/archives/14-More-Ubuntu-WPA-PSK-From-A-Joe-Sixpack-Perspective.html)

-John

---

### Post by PryGuy on 2006-07-09
Thank you, mates!
I actually reconfigured my wireless Windows box! Strange that it does not see the router side changes! Micro$oft is so proud of the Windows plugandplayness and shout out loud on every corner about it!:D Anyway, I did what pitkali recomended, just removed my network from the list and it found it again, and set it up correctly.

And I do not have any problem with my D-Link stuff under Ubuntu. I have heared about D-Link problems but thanks God it's not my case.:)

---

