---
title: "Mobile broadband dongle in teh UK"
date: 2011-11-24
forum: Hardware
---

### Post by foxy123 on 2011-11-24
I need to buy a mobile internet dongle and I wonder if theer are any on th emarket which will NOT work with Ubuntu. I remember reading an overview of dongles in Linux Format few months ago and it practiacally said that all of them should work ok with Linux, but I just want to check.

---

### Post by PaulW2U on 2011-11-24
I only have experience of Vodafone's older PAYG offering, the which is truly PAYG and not subject to a daily minimum. It works with my Samsung N130 netbook and as an experiment I've just plugged it into this 6-year old PC of mine. The dongle was recognised, a box was displayed for me to select the network and tariff and within a minute I was connected much to my amazement.

I'm posting with it now. :)

---

### Post by foxy123 on 2011-11-24
> **PaulW2U said:**
> I only have experience of Vodafone's older PAYG offering, the which is truly PAYG and not subject to a daily minimum. It works with my Samsung N130 netbook and as an experiment I've just plugged it into this 6-year old PC of mine. The dongle was recognised, a box was displayed for me to select the network and tariff and within a minute I was connected much to my amazement.

I'm posting with it now. :)

Thanks a lot.

---

### Post by foxy123 on 2011-11-24
I have bought a Vodafone dongle and I cannot connect. It is recognised ok but does not connect. I tried both Prepaid and TopUp and Go options to no avail.

---

### Post by PaulW2U on 2011-11-24
Hello foxy123, have you forced a connection?

In my Unity top panel I have a network icon. Clicking on that reveals a Mobile Broadband section with an entry "Vodafone Top up and Go". If I click on that a connection is started.

I think that's pretty much how this one works in Windows, the dongle registers itself on the network automatically but doesn't actually connect to the network until you ask it to.

---

### Post by foxy123 on 2011-11-24
> **PaulW2U said:**
> Hello foxy123, have you forced a connection?

In my Unity top panel I have a network icon. Clicking on that reveals a Mobile Broadband section with an entry "Vodafone Top up and Go". If I click on that a connection is started.

I think that's pretty much how this one works in Windows, the dongle registers itself on the network automatically but doesn't actually connect to the network until you ask it to.

Yes I try to connect but it disconnects immediately.

---

### Post by foxy123 on 2011-11-24
I wonder what lsusb gives you? Mine is

```
Bus 001 Device 004: ID 12d1:14c9 Huawei Technologies Co., Ltd. 

```

---

### Post by PaulW2U on 2011-11-24
I've quoted a little more for my lsusb output.

```
Bus 001 Device 007: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270/E870 HSDPA/HSUPA Modem

```E220 is the model which I think is very common. 

It even has its own Wiki page on the Debian web site - [http://wiki.debian.org/Huawei/E220]("http://en.wikipedia.org/wiki/Huawei_E220"). If yours is the same you might find something of help there although for me it was just a simple plug in and go.

---

### Post by foxy123 on 2011-11-25
> **PaulW2U said:**
> I've quoted a little more for my lsusb output.

```
Bus 001 Device 007: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270/E870 HSDPA/HSUPA Modem

```E220 is the model which I think is very common. 

It even has its own Wiki page on the Debian web site - [http://wiki.debian.org/Huawei/E220]("http://en.wikipedia.org/wiki/Huawei_E220"). If yours is the same you might find something of help there although for me it was just a simple plug in and go.

Thanks. It looks I have a different model, K3770

---

