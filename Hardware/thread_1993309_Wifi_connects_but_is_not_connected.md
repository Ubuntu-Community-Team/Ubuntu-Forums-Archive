---
title: "Wifi connects but is not connected"
date: 2012-06-01
forum: Hardware
---

### Post by pfindan on 2012-06-01
Hello,

I have a Lenovo Thinpad T420. When I look at my wireless, my network is there and I can type in my password, and it will connect. But nothing is actually connected, or so it seems. I can't load pages in we browser ( hangs on " connecting" and times out after a while). I also cannot ping google.

Pleae help!

Thanks in advance!

P.S. I'm on Ubuntu 12.04 64bit

---

### Post by rolltide101x on 2012-06-01
If you are still using 11.04 I would say just move up to 12.04 and see if that resolves the issue or possibly trying in a different desktop environment it may just be a glitch in XFCE.

---

### Post by steeldriver on 2012-06-02
we need to know some details about the particular wireless card(s) and driver(s) on your system, there's a guide for how to collect this info here

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

(taken from the sticky threads in the Networking and Wireless subforum)

---

### Post by pfindan on 2012-06-02
I'm on 12.04... Apparently I don't have enough "beans" to edit my profile info, I am also on regular Ubuntu. I will get that information for you.

Thanks!

---

### Post by pfindan on 2012-06-02
[EDIT] Turns out there was personal info in this post, so I have removed it. For reference the laptop in question was a Lenovo Thinkpad T420 with a Intel Centrino Advanced-N 6205 WiFi card.

---

### Post by steeldriver on 2012-06-02
great thanks for taking the time to post that

if you search the forum for 'iwlwifi' you will see there are a few people having issues with those cards/drivers however before we go there can we do one more thing, run the nm-tool command:

```
 nm-tool
```just to see what says

BTW can you ping by IP e.g.

```
ping 8.8.8.8
```

---

### Post by pfindan on 2012-06-03
I have fixed the problem...

Upon some searching around it turns out some support for this driver is bad. So this is how I fixed it...

I made a new file called iwlwifi.conf in /etc/modprobe.d, and added the line "options iwlwifi 11n_disable=1" to the file(without the quotes) and restarted the computer the problem seemed to be solved.

Thank you all for the help you gave me.... Hopefully someone else will benefit from this solution as well.

---

