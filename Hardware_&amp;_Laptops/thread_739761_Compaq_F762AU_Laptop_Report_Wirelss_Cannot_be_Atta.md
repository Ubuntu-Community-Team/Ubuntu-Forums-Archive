---
title: "Compaq F762AU Laptop Report Wirelss Cannot be Attach and low resolution in Ubuntu 7.1"
date: 2008-03-30
forum: Hardware &amp; Laptops
---

### Post by Peter_APIIT on 2008-03-30
Hello all expect Linux user, i plan to buy a new laptop which is Compaq F762AU.  

Dmesg report this for my pci wireless card. 

> 
BT 2 Final

wlan: 0.8.4.2 (svn r)

wifi%d: unable to attach hardware: 

'Hardware revision not supported' (HAL 

status 13)



Ubuntu 7.10

ath_hal: 0.9.18.0 (AR5210, AR5211, 

AR5212, RF5111, RF5112, RF2413, RF5413)
[   95.200000] wlan: 0.8.4.2 (0.9.3.2)
[   95.644000] ath_pci: 0.9.4.5 

(0.9.3.2)

wifi%d: unable to attach hardware: 

'Hardware revision not supported' (HAL 

status 13)



---

### Post by Peter_APIIT on 2008-03-30
I need to know the chipset of this card.

---

### Post by Peter_APIIT on 2008-03-30
When i boot this laptop with Ubuntu 7.10, i cannot boot into GUI mode cuz it is too low resolution. The available resolution during boot into GUI mode is 800X640 and 640X480. 

Anyway to solve this.

Thanks for your help. 

A billion thanks for your help.

---

### Post by Peter_APIIT on 2008-03-30
Any help is greatly appreciated by me and others. Thanks.

---

### Post by Peter_APIIT on 2008-04-19
I need some help. Please help.

---

### Post by Rewarp on 2008-05-02
I have the same laptop model, but the low resolution problem only requires a driver update.

Of course, I am using Hardy Heron, so I am not sure if this will work for you.

Go to the Hardware Drivers option and you should be able to download and enable the NVIDIA restricted driver.

The wireless card is also a huge problem for me, so I finally unscrewed the case and found out the wireless card for the Compaq Presario F762AU is the Atheros AR5BXB63.

I have yet to resolve the problem, but you are welcomed to try the steps [here]("http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html").

Tell me how it works out.

---

