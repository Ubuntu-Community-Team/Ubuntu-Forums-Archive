---
title: "HP 2-Megapixel Webcam"
date: 2009-11-28
forum: Hardware
---

### Post by gferreri on 2009-11-28
Hello

I am running 9.10 and was hoping to make this webcam work. HP does only provide drivers for Windows. Any chance to make it work or should I look for another webcam??? If so, any particular webcam that I should look for?

thanks

gferreri



[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?lc=en&dlc=en&cc=us&product=3636103&lang=en&]("http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?lc=en&dlc=en&cc=us&product=3636103&lang=en&")

---

### Post by Vostrocity on 2009-11-28
It is almost impossible to find a webcam manufacturer that provides Linux drivers. However most webcams will still work just by default. You might want to explain what apps you're trying to use your webcam with. There's an app called Cheese (find it Synaptics or Software Center) that does what Photo Booth does on Macs, it lets you take pictures and videos with effect filters through your webcam. There's a good chance it will work with your cam considering it worked with a 5-year-old DV cam I have that I couldn't even find Windows drivers for.

Also I find it amazing that you've been here for more than a year and this is only your first post. :D

---

### Post by gferreri on 2009-11-29
Vostrocity

Thank you for your information. I've been trying to get it working with skype. Yes, it works with that Cheese app. although there was no sound. So, it indicates that the problem is with skype and not with my web cam as I thought it was.

gferreri
2nd post :P

---

### Post by Vostrocity on 2009-11-30
Enter 'lsusb' in Terminal and paste what you get here. That shows what chipset is in your webcam and then you can know what drivers you need. [Here]("http://www.ovcam.org/ov511/cameras.html")'s a list of drivers that may include your chipset.

---

### Post by gferreri on 2009-12-02
Here it is:

Bus 004 Device 002: ID 045e:0029 Microsoft Corp. IntelliMouse Optical
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 012: ID 0bb4:0c01 High Tech Computer Corp. 
Bus 002 Device 006: ID 147a:e018 Formosa Industrial Computing, Inc. 
Bus 002 Device 005: ID 0411:00a2 MelCo., Inc. 
Bus 002 Device 008: ID 03f0:0f0c Hewlett-Packard Wireless Keyboard and Optical Mouse
Bus 002 Device 007: ID 0bda:0151 Realtek Semiconductor Corp. Mass Stroage Device
Bus 002 Device 004: ID 15b8:6002  
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 15a9:0004  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Vostrocity on 2009-12-02
Sorry I haven't found any drivers for that chipset. But according to [this post]("http://ubuntuforums.org/showthread.php?t=659540") it seems like the driver isn't the problem it's just that Skype can't support it. If anyone else has suggestions go ahead but I can't offer anything else. :KS

---

### Post by gferreri on 2009-12-03
Vostrocity

Yes, I suspected that skype is the software that "didn't like" my webcam but anyway, thank you for your interest in trying to help me. I really appreciate it.

gferreri

---

