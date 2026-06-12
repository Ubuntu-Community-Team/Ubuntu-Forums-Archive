---
title: "wireless help please"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by vash469 on 2007-02-11
Hi everyone this is my first post and my first install with any linux distribution i have been wanting to use linux for a while but the difficultly level was the only thing stopping me.
finally getting ubuntu to install on an old desktop i have. the os seems to recognize the card but i cant seem to get the setting correct to connect to my access pt and connect to the internet. i have gotten a little bit of help from another forum i visit [link to the other forum were i received some help]("http://forums.hostmatrix.org/showthread.php?t=13266") 
 
when i put "iwconfig" the connection its giving me for my wireless is ra0

please view the link that i provide for more info on what i have tried to do concerning this topic

this is my hardware info 
model number linksys wmp54g mini-pici card for desktop - wireless card
router-wrt54g v4 wireless-g 2.4 ghz

thanx for everyones help in advance

---

### Post by ltmon on 2007-02-11
Hi,

I (used to) have very similar hardware, and had it working.  The ralink drivers that are used aren't the best (occasional dropouts), but they shouldn't be too much trouble.

Generally it helps to do the following:
- Make sure your router is broadcasting it's SSID.  This should be a router setting.
- Turn off ALL wep, wpa, MAC and radius security you might have enabled
- Try scanning/connecting
- Slowly turn on all your security measures one at a time

You could also try NetworkManager, as it helps by auto configuring a whole lot of stuff.  NetworkManager will be the default in the next version of Ubuntu.

The following docs might help:
[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

Cheers,

L.

---

### Post by vash469 on 2007-02-11
can u please clarify what the scan and connecting command lines are???:confused:

---

### Post by agiamba on 2007-02-11
hey i looked up NetworkManager, [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/) and I have it installed, but how to you get the GUI for the wireless networks shown in the pictures?

---

### Post by vash469 on 2007-02-12
> **agiamba said:**
> hey i looked up NetworkManager, [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/) and I have it installed, but how to you get the GUI for the wireless networks shown in the pictures?

they are pre-instelled in edgy

---

### Post by lamalex on 2007-02-12
What version of Ubuntu are you running, I had a lot of trouble in edgy so i tried Feisty herd 3 and I havn't had a single problem. networkmanager is doing a great job for me.

---

### Post by lamalex on 2007-02-12
> **agiamba said:**
> hey i looked up NetworkManager, [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/) and I have it installed, but how to you get the GUI for the wireless networks shown in the pictures?

are you right clicking? I don't mean to be condescending but if you're seeing like enable wireless, enable networking, then you're right clicking and should try left.

Sorry if  I insulted you, but i watched my girlfriend pull up that menu for 15 minutes racking my brain how she broke it until i realized she was right clicking on it, something I had never done. :lolflag:

---

### Post by vash469 on 2007-02-14
im using edgy

---

