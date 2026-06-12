---
title: "Broadcom 4318 wireless driver"
date: 2009-07-15
forum: Hardware
---

### Post by Rule2 on 2009-07-15
I have an HP Pavilion dv 5000, and I cant connect to my home WLAN network.
Please ask for more information, if required.
Thank you

---

### Post by Ayuthia on 2009-07-15
If you have a working connection in Ubuntu, you can try installing b43-fwcutter from Synaptic or from the Terminal:
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```

---

### Post by Rule2 on 2009-07-15
> **Ayuthia said:**
> If you have a working connection in Ubuntu, you can try installing b43-fwcutter from Synaptic or from the Terminal:
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```
It is done through restricted drivers. Updated.
I am using jaunty. I tried many tutorials on this site and I am at my wits end.

---

### Post by Ayuthia on 2009-07-15
> **Rule2 said:**
> It is done through restricted drivers. Updated.
I am using jaunty. I tried many tutorials on this site and I am at my wits end.

Glad to see that it was found in Hardware Drivers.  From what I have heard with the 4318 cards, it has not been found there.

Can you check:
```
dmesg|grep b43
```
It will help us see if the wireless card is activated or not.

---

### Post by pvnbg on 2009-07-18
Hi. I have the same problem with my Acer. The card is BroadCom 4318. Yestarday,i did the same steps:

> 
sudo apt-get update
sudo apt-get install b43-fwcutter


After restart,network manager found the wireless card,scan and found my wireless router.But,when i connect,no replay from router,no ping and etc. 
The laptop is with static addresses: 192.168.2.100,255.255.255.0,192.168.2.1
Wireless router: 192.168.2.1,255.255.255.0.

dmesg | grep b43 shows no problems...

ifconfig wlan0 shows the card is active,with shown IP addresses,but...there is no connection between them.

what's wrong?

Ubuntu 9.04
Kernel 2.6.28-11

---

### Post by pvnbg on 2009-07-19
I found the solution ... [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

