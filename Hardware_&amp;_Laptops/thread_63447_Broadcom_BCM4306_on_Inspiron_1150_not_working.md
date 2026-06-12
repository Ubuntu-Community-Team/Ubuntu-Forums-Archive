---
title: "Broadcom BCM4306 on Inspiron 1150 not working"
date: 2005-09-07
forum: Hardware &amp; Laptops
---

### Post by thulben on 2005-09-07
Hi all,

Alright, here's the story.  I've got an Inspiron 1150 that I really want to get wireless working on.  I know it works because it worked yesterday (I had previously installed the drivers successfully).  The only change that I made was to install the kubuntu package overnight.  When I came in the morning, it just wasn't working.  I couldn't get it working to save my life.  Not having invested much into the configuration of the system up to that point, I just re-installed.  I still can't get it up and running.  Here's what I've tried:

Using ndiswrapper and drivers that I downloaded from Dell, I'm able to get the card to be recognized by the OS.  However, I'm unable to find my router.  Even if I try to set the essid with iwconfig manually.  Using iwevent, I can see that it's at least trying to set the essid to my router.  I'm at a loss as to what might be happening.

Thanks in advance,
Ben

---

### Post by eggshape on 2005-09-12
if you know your router's essid and encryption key and you are using dhcp:

>cd /etc/network
>sudo nano interfaces

now enter the following:

#auto wlan0 (get rid of the pound sign if you only use wireless at home)
iface wlan0 inet dhcp  #replace "wlan0" with your interface name
wireless-essid your-router 
wireless-key your-key

save and exit nano (or whatever editor you used)

>sudo ifup wlan0 
(or whatever your interface name is)

static IP is similar:
iface wlan0 inet static
address ...
netmask ...
gateway ...

if you have multiple wireless routers; download ifscheme and check out how you can configure the interfaces file for easy ifup

if this doesn't work, are you sure your card is working?

---

