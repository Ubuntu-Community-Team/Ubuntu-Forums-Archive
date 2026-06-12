---
title: "Ubuntu on HP Problem with Wi-Fi"
date: 2009-06-22
forum: Hardware
---

### Post by hyperbrowser on 2009-06-22
I got my sisters old HP Laptop (I don't know the product number but if you need it to help me then ask and I can check). I installed successfully Ubuntu but I can not connect to the wireless internet on because the button that turns the Wi-Fi on the Laptop on, apparently does not work with ubuntu. How can I get the Laptop's Wi-Fi to work again so I can use the Laptop's Wireless Function?

---

### Post by IcarusR on 2009-06-23
Some more info would be helpful.... 
What laptop model is it ?
Which version of ubuntu ?
What WiFi card is it ?

To find wifi card post output of...
```
lspci
```

I do not think the wifi switch will necessarily stop it from working, as long as it is switched on.

---

### Post by rob2uk on 2009-06-23
Refer to this page to find your model number: [http://welcome.hp.com/country/us/en/support/prod_info.html]("http://welcome.hp.com/country/us/en/support/prod_info.html")

A few of the DV series of laptops, and the corresponding Compaq Presario models have BIOS problems that prevent them from detecting the wireless cards...

---

### Post by hyperbrowser on 2009-06-28
It's an HP Pavillion zv6000 notebook
its product number is: EC356UA#ABA
And i installed: Ubuntu 8.04.2 LTS Desktop edition
The wi-fi card is a: broadcom corp. bcm4306 802.11b/g wireless lan controller (rev 03)

---

### Post by hyperbrowser on 2009-06-28
I want to figure out how to turn the wi-fi on and off by touching the button because it is not working that is the point of the thread

---

### Post by hyperbrowser on 2009-06-28
I found a possibly helpful article that may help me:

[http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/](http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/)

---

