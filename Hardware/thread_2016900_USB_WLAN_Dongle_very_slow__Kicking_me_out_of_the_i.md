---
title: "USB WLAN Dongle very slow / Kicking me out of the internet."
date: 2012-07-04
forum: Hardware
---

### Post by netraameht on 2012-07-04
Hello,

First, I'm new here and I don't really know which commands can be useful here.

So, I made my own Ubuntu computer and I got a weird problem. I got a USB WLAN Dongle, it's from König Electronic (CMP-WNUSB32) and says it's compatible with Linux. So I installed the drivers (using a lot of time!) from internet because the disk didn't really work. It's kinda working (Network Manager says so) but when I try to load one simple website like google, it takes a long time or in most of cases it just kicks me out of my internet. BTW I'm using Ubuntu 10.04, and I had a little trouble with the network manager (disabled).

If you need more information just post it.

- Netra

---

### Post by apacketofsweets on 2012-07-04
As far as I'm aware, the latest version of the Linux kernel, found in versions 12+ of Ubuntu have a huge amount of drivers for USB dongles such as yours built in. There's a good chance that upgrading to the latest version of Ubuntu will correct this issue your having.

---

### Post by ahallubuntu on 2012-07-04
Some googling shows the chipset is a Realtek 8188/8192CU .

I have a couple of dongles with the same chipset.  I use them with Ubuntu 10.10 .  I had to download and install the driver from Realtek's website.  My connections are fairly good, even fair away from the router.

Where did you get a driver, and how did you install it?

I found this page:

[http://www.konigelectronic.com/de_de/55809312](http://www.konigelectronic.com/de_de/55809312)

but I got my driver directly from Realtek:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

This is probably the newest driver available.  But there is no Ubuntu package; you will have to make/install it in a terminal .  I am used to this but you may find it confusing.

---

### Post by netraameht on 2012-07-05
> **ahallubuntu said:**
> Some googling shows the chipset is a Realtek 8188/8192CU .

I have a couple of dongles with the same chipset.  I use them with Ubuntu 10.10 .  I had to download and install the driver from Realtek's website.  My connections are fairly good, even fair away from the router.

Where did you get a driver, and how did you install it?

I found this page:

[http://www.konigelectronic.com/de_de/55809312](http://www.konigelectronic.com/de_de/55809312)

but I got my driver directly from Realtek:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

This is probably the newest driver available.  But there is no Ubuntu package; you will have to make/install it in a terminal .  I am used to this but you may find it confusing.
I downloaded and installed the driver at the König website. But i'll try to install that driver and then Ubuntu 10.10. And I made a mistake, I'm supposed to make a (desktop)server. Just for local hosting (And maybe online). So I'll upgrade it to 10.10 server. Can it be a problem?

EDIT:
The old driver's version was v2.1, the driver you gave me is v3.4!

---

### Post by ahallubuntu on 2012-07-05
Try the newer driver available from Realtek.

I do not recommend upgrading to 10.10 - I was just pointing out that I was using this dongle successfully in Ubuntu.

Ubuntu version 10.10 is no longer supported.

10.04 LTS is supported for almost another year.  I recommend either staying with 10.04 LTS for now or upgrading to 12.04 LTS, not 10.10 .

---

### Post by netraameht on 2012-07-05
Okay, I installed the latest driver, but it's still very slow. It doesn't kick me out anymore :D

---

