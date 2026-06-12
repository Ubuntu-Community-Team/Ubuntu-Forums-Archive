---
title: "Help can't get any networking"
date: 2010-08-02
forum: Hardware
---

### Post by Charltp5 on 2010-08-02
Newbie question

I have installed Ubuntu 9.1 on an old Dell Latitude C400 and all seemed fine except I cannot get any response from the 3Com 3C905 Network card.

Even after I try to create & configure a wired connection I get "No network connection" in the notification area.

Strangley I can plug in my O2 3G/GPRS dongle and it will connect to internet fine but I really need to get the network connection working. I don't think there's a  built-in wifi card in this laptop.

All help really appreciated.

---

### Post by mikewhatever on 2010-08-03
Start with the basics - post the outputs of the following:

ifconfig

sudo lshw -C network

lsmod | grep 905

---

### Post by Sef on 2010-08-03
How are you connecting to the network?  Wired or Wireless?

---

### Post by Charltp5 on 2010-08-03
> **Sef said:**
> How are you connecting to the network?  Wired or Wireless?

Wired laptop does not have built in wireless and I don't have a PCMCIA card.

---

