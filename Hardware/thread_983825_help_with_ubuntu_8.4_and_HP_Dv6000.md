---
title: "help with ubuntu 8.4 and HP Dv6000"
date: 2008-11-16
forum: Hardware
---

### Post by barnacles on 2008-11-16
Hello, 
I am a newer linux user and a new user to the forums. I am having a frustrating problem which others seem to have had in the past. I haven't found any recent threads on the topic though. 

So... I have a HP pavilion dv6000 laptop. It has a broadcom wireless card (bcmwl6.sys) 

Upon installing ubuntu, everything works except wireless. Previous threads suggested that ubuntu wouldn't work with this driver but that was back in previous versions. Any help would much be appreciated.

I have yet to plug it in wired, but there are some updates. Would updating add support for my card?

Thanks in advance.

---

### Post by barnacles on 2008-11-16
i came across this as well. 

[http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/](http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/)

come morning I plan plugging it in directly to the router. Is the above something I should try?

---

### Post by teaker1s on 2008-11-16
system>administration>hardware drivers see if there is a restricted driver as my bcm4311 has a driver. otherwise its the ndiswrapper route.

---

### Post by ravl on 2008-11-16
> **teaker1s said:**
> system>administration>hardware drivers see if there is a restricted driver as my bcm4311 has a driver. otherwise its the ndiswrapper route.

Exactly. I'd also add to press the hardware switch for you wifi on the laptop. On an HP ze2000 with a Broadcom 4318, I installed Hardy, and I had no wireless with the stock b43 driver.
I was about to install ndiswrapper, but I decided to press the wifi button out of curiosity. The light was on from the start, but the card was off, once I pressed the button everything worked. The wifi light didn't change, but now I had wireless access.

This also happened to me when I installed Hardy into a friend's Acer laptop with the same wifi card. I think the driver defaults the card to off after install.

---

### Post by barnacles on 2008-11-16
Alright so I got the driver to work. With all the updates I was able to enable it and after restart the blue light for wireless came on (which means its on). I am able to see a list of all available networks now, and am also able to connect. However once I am "connected" i still have no internet access... help?

---

### Post by teaker1s on 2008-11-17
if you open terminal and put this command in
```
iwconfig
``` post output and we can tell more what's happening.

---

