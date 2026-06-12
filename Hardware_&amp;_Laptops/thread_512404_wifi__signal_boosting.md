---
title: "wifi  signal boosting?"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by zabien1970 on 2007-07-29
Is there a way to improve the signal on a built in wifi, I have a dell inspiron 6000 with an intel prowireless card
My signal strength constantly fluctuates from excellent to no signal, when I first installed Ubuntu it worked great, now I lose signal more and more.
On a sidenote, My neighbor has the router and doesn't mind me using signal but won't move or change anything, he hasn't moved it or anything else and I haven't moved my laptop except to try for a better signal, I also just switched from network manager to wicd but same thing, shame there isn't a plug for an antenna.

---

### Post by walkerk on 2007-07-29
> **zabien1970 said:**
> Is there a way to improve the signal on a built in wifi, I have a dell inspiron 6000 with an intel prowireless card
My signal strength constantly fluctuates from excellent to no signal, when I first installed Ubuntu it worked great, now I lose signal more and more.
On a sidenote, My neighbor has the router and doesn't mind me using signal but won't move or change anything, he hasn't moved it or anything else and I haven't moved my laptop except to try for a better signal, I also just switched from network manager to wicd but same thing, shame there isn't a plug for an antenna.

you could buy a wireless repeater... something like [this]("http://www.amazon.com/Linksys-Wireless-G-Range-Expander-WRE54G/dp/B00021XIJW") perhaps..

---

### Post by zabien1970 on 2007-07-29
I'll definitely look into it, was mostly wondering if there was something that changed in my computer ie. the updates I regularly install that may haved caused my system to go from a steady signal the first couple months to the fluctuating one I have now

---

### Post by walkerk on 2007-07-29
> **zabien1970 said:**
> I'll definitely look into it, was mostly wondering if there was something that changed in my computer ie. the updates I regularly install that may haved caused my system to go from a steady signal the first couple months to the fluctuating one I have now

i don't think that **software** updates will screw up your signal. unless of course you installed a new driver for your wifi card recently.. a lot of things can contribute to lose of signal strength.. most of which are physical.. did your neighbor install a 2.4ghz wireless phone next to the router perhaps? that would mess with the routers signal strength.. something must have changed or maybe your card is going bad :/

---

### Post by Nuverde on 2007-07-29
I got an improvement in my signal by choosing a different WiFi Channel.  I think my router had defaulted to 6.  When I switched to 11, I got a much cleaner signal.  I had assumed that there was something in my apartment or the surroundings that was causing interference in channel 6's frequency range.

---

### Post by zabien1970 on 2007-07-29
How do I switch channels? I don't see an option in wicd and I don't remember seeing it in network manager

---

### Post by Nuverde on 2007-07-29
> **zabien1970 said:**
> How do I switch channels? I don't see an option in wicd and I don't remember seeing it in network manager

I had to do this in my wireless router.  I have a Linksys wireless router that I configure through a web interface.  In my case, I browse to [http://192.168.1.1](http://192.168.1.1) and after entering the proper password, go to the "Wireless" tab.  You will need to see the documentation for your particular wireless access point on how to do this.  Your laptop/PC should automatically detect what channel is being used, so there should not be anything you need to do in Ubuntu.

---

### Post by ramadhian on 2007-08-18
I have changed my channel from 6 to 12, it increase signal from 54% to 64%

In Windows XP Signal detected so Excelent in Channel 6 ,,

What make it look different in Ubuntu ?

---

### Post by fvds on 2007-08-18
Perhaps another wireless network in your neighbourhood is causing the loss of signal? You could try airsnort or a simmilar tool to see which wlans are active and what channel they use. This can help you to determine a better channel for your wlan.

---

### Post by ramadhian on 2007-08-20
kenzo@ramadhian:~$ airsnort 
/sbin/wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable > /dev/null
sh: /sbin/wlanctl-ng: not found


Did I missed somethin here ?

---

