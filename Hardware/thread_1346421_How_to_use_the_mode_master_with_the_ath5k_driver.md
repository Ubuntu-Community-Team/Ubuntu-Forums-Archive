---
title: "How to use the mode master with the ath5k driver ?"
date: 2009-12-05
forum: Hardware
---

### Post by Eul_Mulot on 2009-12-05
Hello,

In [this page]("http://linuxwireless.org/en/users/Drivers/ath5k#features"), they says that we can use the AP mode with the ath5k driver since linux 2.6.31

I am using Ubuntu Karmic with : linux 2.6.31-16-generic

I would like to share my eth0 WAN connection creating a wlan0 LAN.
Browsing on the Internet, I saw that we can use hostapd to do that.

The main problem is this command :

```
$ sudo iwconfig wlan0 mode master
```

That returns :

```
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
```

How can I make my AP mode working with Karmic ?

---

### Post by darth_ru on 2009-12-13
I have the same problem. The cause is that it is impossible to put ath5k in master mode using iwconfig. But it is possible using hostapd.

---

### Post by Eul_Mulot on 2009-12-13
Thank you for your answer, I noticed this some days ago but didn't notify it on the thread, thanks anyway ;)

---

### Post by WOTHed on 2010-01-10
Can some one give me a quick cheat sheet of how to echo the right code into this hostpad.


:D

---

### Post by korgman_gr on 2012-03-07
(for historical reasons, since was on top of google search results...)

[http://wireless.kernel.org/RTFM-AP](http://wireless.kernel.org/RTFM-AP)

---

