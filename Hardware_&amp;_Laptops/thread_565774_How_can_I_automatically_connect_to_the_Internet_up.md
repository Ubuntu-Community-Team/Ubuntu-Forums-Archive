---
title: "How can I automatically connect to the Internet upon inserting Vodafone HSDPA card"
date: 2007-10-02
forum: Hardware &amp; Laptops
---

### Post by Bubbel on 2007-10-02
Hi there,

Since a while I use a Vodafone HSDPA card.
Connecting works file with a pppd call configuration, exept for the update of /etc/resolv.conf, witch I have to do manually.

The specs of the card are as follows:
```

It's for the Dutch market, called a Vodafone Mobile Connect HSDPA/UMTS/EDGE/GPRD data card.
The card is in fact from Option, model GT 3G+ EMEA
As expected it creates devices /dev/noz[0-2]
lspci identifies the card as follows:
 03:00.0 Network controller: Option N.V. Qualcomm MSM6275 UMTS chip

```

I know Linux can trigger events with help of hal, dbus and udev. But how do I proceed to create an event/rule to start the ppp daemon and automatically update resolv.conf in the process?

Bubbel

---

### Post by jjj_uk on 2007-10-24
I'm getting a UK vodafone data card soon so it would be great if this query could be answered (not that I'm being selfish or anything....)
Just seen this - [http://mybroadband.co.za/vb/showthread.php?t=66785](http://mybroadband.co.za/vb/showthread.php?t=66785) I'll give it a try when the card arrives.

---

### Post by Bubbel on 2007-10-24
Here is a simpler solution to just connect. Vodafone hackers made a program similar to the Windows program.
It has some glitches with suspend, I have noticed, but these aren't big.

I suggest you give it a try.

[http://www.vodafonebetavine.net/web/linux_drivers](http://www.vodafonebetavine.net/web/linux_drivers)

Greetz

---

