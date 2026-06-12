---
title: "Limit WiFi transmit power"
date: 2010-06-24
forum: Hardware
---

### Post by punit_r on 2010-06-24
There is a command to set the transmit power 
iwconfig wlanX txpower ___

The value can be specified directly (in dBm) or number with mW postfix. I would like to know if there is a way to specify negative dBm or very low transmit power for wireless.

---

### Post by VH-BIL on 2010-06-24
You can check out:
[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html)

---

### Post by punit_r on 2010-06-24
Thanks for the link. I am aware of the wireless tools packages. 

Here are some more details about my setup: 
[LIST]
[*] The supported transmit powers listed by the command ```
iwlist wlanX txpower
``` start with 0dBm upto 19dBm on my Atheros AR5001X+ card. 
[*] If I try setting a negative dBm in iwconfig, the txpower setting takes the maximum power (19dBm). 
[*] On setting 0dBm in iwconfig, the txpower setting takes a value 'off'
[*] I am using multiple wireless cards (with both kernel stock drivers and madwifi) 
[*] The variables for txpower in madwifi (ath/if_ath.c) take values for mW in unsigned int. Hence, allowing for a low value of 0dBM --- 10log(1mW)
[/LIST]

What I want to do:
Set a very low transmit power 
  a) 0 < txpower < 1mW
  OR
  b) -ve dBm

---

### Post by vijaypoliset on 2010-12-22
hi punit,
were you able to find out a method to set transmit power in negative dBm. If so can you please share it with me. I'm in very urgent need for such setting.

Thanks
Vijay

---

### Post by punit_r on 2010-12-22
Hi Vijay,

I have not found any method to accomplish this. However, for the time-being, we use RF attenuators with the card antenna. 

This method works only if you have a card with external antenna / detachable antenna. Also, the most common RF attenuators are with SMA connectors.

A good place to look for attenuators is digikey.com

-Punit

---

### Post by vijaypoliset on 2010-12-22
Thanks a lot Punit. That is very helpful.

---

