---
title: "Wifi on Ubuntu 12.10"
date: 2013-01-22
forum: Hardware
---

### Post by ecceccecc on 2013-01-22
Hi people, I'm currently using Ubuntu 12.04 LTS on my MSI notebook. Once I tried the latest release, 12.10, it worked pretty well, but I can't say the same thing about wifi internet connection. Sometimes it worked, most of times it doesn't worked at all.
Since it works fine on 12.04 LTS, is this a bug on 12.10?

---

### Post by ahallubuntu on 2013-01-22
Wireless issues are specific to individual hardware.  What wireless card are you using successfully in 12.04?

In a terminal type:

```
sudo lshw -C network
```

---

### Post by ecceccecc on 2013-01-22
According to the command above, it's a RT3090 Wireless 802.11n 1T/1R PCIe by Ralink corp.

---

### Post by lkz6998 on 2013-01-22
I also have a Ralink RT3090 and my wireless is horrible.  It disconnects frequently and when it does work I only get 100-200kbps even though my Win 7 laptop sitting right next to it gets 15-20Mbps and never disconnects.  I have spent hours trying to fix it but I don't know what to do.

---

### Post by natesymer on 2013-01-22
Just get a new card. They are less than $20 and they are easy to install. Just make sure you know if you have a half sized or a full sized card.

If you also want bluetooth, you can go get the Intel wireless module from the GA-Z77N-WiFi logic board. It's actually a good card, just not hackintosh compatible (I usually like hackintosh compatible hardware, for the flexibility).

---

### Post by ecceccecc on 2013-02-03
> **lkz6998 said:**
> I also have a Ralink RT3090 and my wireless is horrible.  It disconnects frequently and when it does work I only get 100-200kbps even though my Win 7 laptop sitting right next to it gets 15-20Mbps and never disconnects.  I have spent hours trying to fix it but I don't know what to do.

As I said before, my RT3090 works fine if I use Ubuntu 12.04 LTS and based distros like Linux Mint 13, in example. The wifi problem occurs when I use Ubuntu 12.10 and Linux Mint 14 - I've read that the Network Manager included in Ubuntu 12.10 comes with some kind of bug. I've seen that the problem occurs just when I turn on the machine and the system starts up: sometimes wifi works, sometimes not.

---

### Post by ahallubuntu on 2013-02-03
Is there a compelling reason to use 12.10 instead of 12.04 LTS?  Some people do need to use 12.10 (need the newer kernel for their hardware, need something new to 12.10, etc.), but for many 12.04 LTS is a better choice.  It will be supported longer than 12.10 (only supported until next April).  12.04 LTS will be supported until 2017.

---

