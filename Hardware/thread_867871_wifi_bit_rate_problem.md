---
title: "wifi bit rate problem"
date: 2008-07-23
forum: Hardware
---

### Post by rawtin on 2008-07-23
Hi.  My wifi shows only a rate 1M.  I have tried "Iwconfig wlan0 rate 54M".  This does change the rate, yet, this higher rate stops access to the network and it will not allow use of the signal.  The signal _is_ there and is read by the card. I use a broadcom 4311 and am using b43 and appropriate firmware.

---

### Post by evets25 on 2008-07-23
Well check to see if your card is "802.11g" or just "802.11b". g does 54Mps, and is backwards-compatible with b, but b only does 11Mps. So, if you tried to set a card that only does b to do 54Mps, it wouldn't work. In that case, you'd run this instead: 

```
sudo iwconfig wlan0 rate 11M
``` 

Also, note that the sudo is necessary, as well as the fact that it's case-sensitive, as always. You should be able to tell what the rate is set to by running just running "iwconfig".

---

### Post by rawtin on 2008-07-23
I never knew the difference between the letters at the end.  thank you for that info.  I have a 802.11g, so it should go to 54 as you said.  Also, I can change the rate to the proper number and the card looses the connection.  Thank you for responding.

---

### Post by evets25 on 2008-07-23
well then perhaps you want to try ndiswrapper. Here, read [this thread]("http://http://ubuntuforums.org/showthread.php?t=281990") and also [this page]("http://https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)") for more information about your wireless card.

---

### Post by wizardfait on 2008-07-23
My card is a little different, (4306 I beleive) and it does the same thing, I've found if you use b43 and the firmware, you HAVE to keep it at 1Mbit or else you can't connect, maybe you can get away with 2, but in the end, it's no worth it. And my previous experience with ndiswrapper and this card, it totally failed... and even broke my original install of the driver/firmware... Hopefully you'll have better luck. :D

---

