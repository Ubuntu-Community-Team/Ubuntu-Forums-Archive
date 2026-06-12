---
title: "Need Guidance With Drivers"
date: 2007-02-28
forum: Hardware &amp; Laptops
---

### Post by Prometheus.172214 on 2007-02-28
Hi,
     Firstly, I am a total novice when it comes to Linux. I managed to setup the wired network and am able to go online using a wired connection (Intel Pro NIC). The problem, starts when I try to go Wireless. I did go to the Network Configuration tool and when I select properties, I have options for the ESSID Name, which I gave as the Wireless Network name, for the password, I entered the WEP Hexadecimal Key for my Linksys Router. (Now assuming that this is close to reality and you are not laughing your head off at my total lack of Linux knowledge) Here is the problem.  The system has a small quick access button, that can be pressed to switch on and switch of wireless. When the laptop had Windows, activating wireless made the button glow in blue. Then I just had to give it a minute and it would readily connect to my home wireless network. In Ubuntu, this button is non responsive, which gives me an idea that the driver may not be present. Also, the modem (Conexant MDC) and the Wireless had a minus sign before them and the wired NIC had a check mark on it, when I first launched this applet. So, I am suspecting a driver issue. I have the modem drivers a tar.gz and I can compile them (Not that I actually need the modem drivers). However, the Wireless Drivers are what I need. Is there a way to identify the wireless nic in Linux?

---

### Post by Prometheus.172214 on 2007-03-02
All right here I go again. This time around I have the details of the Wireless Controller in my notebook pc. It is a Broadcom Controller and the exact details can be seen from the images seen below. I have tried a few programs like Wireless Assistant, Wireshark (as root) Wifi Radar, however they do not detect any wireless network. As explained I believe the wireless drivers are not installed, but I am at a loss of what to do.

---

### Post by Prometheus.172214 on 2007-03-02
Allright ! Here is an answer that I found from a different user in a differnet thread. 

[http://www.ubuntuforums.org/showthread.php?t=197102](http://www.ubuntuforums.org/showthread.php?t=197102)

Thanks to Kobalt for this response !

Cheers :-)

---

