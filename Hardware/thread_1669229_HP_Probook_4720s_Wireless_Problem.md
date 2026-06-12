---
title: "HP Probook 4720s Wireless Problem"
date: 2011-01-17
forum: Hardware
---

### Post by golfpr089 on 2011-01-17
Hello,

I have an HP ProBook 4720s, and can't get my wireless card to work. I have the machine dual-booted and have no trouble in Win7 Pro64. The WLAN button won't toggle on. I'm pretty much a novice user of Linux. Most of my experience is with Windows. Any help would be appreciated. 

Thanks

---

### Post by Identity on 2011-01-20
I have the same problem, or at least a similar one. I've just installed Ubuntu 10.10 32-bit on my HP Probook 4720s (WS912EA) and cannot connect to the W-LAN.  It does display the networks, but it fails to accept the correct password.

The notebook has a WLAN toggle key with a little LED that can be orange or blue, meaning that the WLAN is off or on, respectively. This is blinking rapidly (orange-blue-orange-blue). If I hit the key, it goes orange and the WLAN turns off.

---

### Post by Identity on 2011-01-22
If I wait long enough I get a "Connection Established". However, the browser still doesn't work and the "WLAN device on" LED is still blinking (on/off/on/off...). A few minutes after "Connection Established" I then get a "Connection Lost" message, then later again "Connection established" etc.

When I press the appropriate key on the keyboard it stops blinking blinking and the LED permanently goes to "off". Hitting the key again does NOT turn it back on (it does in windows).

lshw keeps showing the WLAN adapter als "DISABLED"

---

### Post by Identity on 2011-01-22
Updating the driver for the RT3090 wireless adapter alleviated the problem somewhat. I can now go online. I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=1600498](http://ubuntuforums.org/showthread.php?t=1600498)

However, websites still take a very long time to load, much longer than under Windows... also the "Additional Drivers" GUI element which usually is used to install the proprietary graphics drivers now displays rt3090sta, saying "This driver is activated but not in use", strange...

---

### Post by Pifilatakanemu on 2011-04-18
Hey,

what about the wireless? Any further fixes that helped you?

Are you satisfied with the notebook's functioning under ubuntu?

What about the Touchpad? I read that some people had problems with it.

I'm considering buying one so I would really appreciate your feedback.

Thanks!

---

### Post by golfpr089 on 2011-04-18
Yeah the wireless is working now. The touchpad is pretty goofy. I normally use an external wireless mouse with it though. The only problem (which I haven't spent much time on figuring out how to disable), is that the touchpad is so big on these that you bump it all the time unless you have perfect "hands up" typing posture (I don't know anyone who does). Other than those couple of nuisances, it performs very well with Ubuntu. I should mention that mine has the i7 and 8 GB RAM though, although Ubuntu seems to run pretty well on much lesser hardware in my experience. I mostly use the Win7 OS on it (I have it dual booted), and it runs great (of course Win7 needs good hardware). I disable the touchpad and use a mouse with it if I'm on it any length of time. I hope this helps.

---

### Post by Identity on 2011-09-17
I cant get the wireless to work well. Since that's the only way to access the net here, I'm not using ubuntu at all. I did all the guides about the rt3090

 ([http://ubuntuforums.org/showthread.php?t=1600498](http://ubuntuforums.org/showthread.php?t=1600498)
[http://georgovassilis.blogspot.com/2011/04/hp-probook-4720s-on-ubuntu-1104-64bit.html](http://georgovassilis.blogspot.com/2011/04/hp-probook-4720s-on-ubuntu-1104-64bit.html) 
and
[http://ubuntuforums.org/showthread.php?t=1481710](http://ubuntuforums.org/showthread.php?t=1481710))

but no dice; either I'd get a blinking wlan on/off led and wlan working at very slow (<1kb/s) speed and unable to even pull package list updates with synaptic successfully,

or I'd get stuck in an endless loop of "enter password", with several minutes between prompts, and the wlan symbol on the 11.04 gui 'blinking'

I dont understand how it's possible others have the same laptop and get it to work. Maybe it's because this is a Probook 4720s WS912EA#ABD and those that are getting it to work are using a different version of the probook 4720s. Either that or I did something wrong, but after >30 hrs dealing with this I suspect thats not the case

---

### Post by Identity on 2011-09-17
well there is another possibility: the wlan is actually working fine (at least under the setup induced by guide #2), but the wlan encryption or authentication isn't.

My current isp requires something called Dynamic WEP 802.1x with TLS. Uses a password, an identity, a certificate, a private key, and perhaps some module that isnt installed (opensc?) - i'll go see if any of the guides help the wireless work with an unencrypted wlan

---

### Post by Identity on 2011-09-17
then again why would authentication not work with one driver for the rt3090 and work with another? if i was lacking some component that handles that, it shouldn't ever allow any connecting no matter how slow or temporary

---

### Post by Identity on 2011-09-17
Ok now it works.

Installing 11.10 Oneiric beta with kernel v3 solved everything

---

