---
title: "Wifi card problems"
date: 2009-01-31
forum: Hardware
---

### Post by Axel-P on 2009-01-31
Hi all!

So, my problem seems to be something that bothers many users, but I still don't find any post that can solve it :(.

I have a Broadcom wireless networks card BCM4328 802.11a/b/g/n (rev 03), and my Ubuntu 8.10 doesn't sees any wireless connections :( even though my other partition (windows Vista) does. When I installed Ubuntu a message prompted saying that I could use the proprietary driver for my card, and it doesn't seems to help me at all xD. I also find out that when I try to bring up the wireless network with sudo ifconfig wlan0 up, this prompts:

wlan0: ERROR while getting interface flags: No such device

Can anyone help me??

Thanks:D

---

### Post by Axel-P on 2009-01-31
Please, this is not a private chat:smile:. I will hear anyone who can help.

---

### Post by nixscripter on 2009-01-31
If you can get Windows XP drivers (off the internet, for example), you can use Ndiswrapper. 

Instructions on how to do that are here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

One version of the XP driver to try is here: [http://www.wireless-driver.com/driver/broadcom/broadcom_43xx_drv_4102284.zip](http://www.wireless-driver.com/driver/broadcom/broadcom_43xx_drv_4102284.zip)

Hope this helps.

---

### Post by MarblePanther on 2009-01-31
I have the same card.  If you have an ethernet connection, plug it in then go to System, Administration, Hardware Drivers and install the driver.  You must have a cabled internet connection so Ubuntu can download the driver for your wireless card.

---

