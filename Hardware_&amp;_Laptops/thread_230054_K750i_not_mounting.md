---
title: "K750i not mounting"
date: 2006-08-05
forum: Hardware &amp; Laptops
---

### Post by khaledaboualfa on 2006-08-05
I've read all over the place that the Sony Ericsson works with DD, but for some reason when I connect the phone via usb it doesn't mount. Doesn't show anything whatsoever. Are there drivers/programmes I've got to try and install? I can't seem to find any linux information on the official website, and in the posts and a few articles I've read on the web, it should be as easy as plugging the thing in. Any ideas?

---

### Post by Ziede on 2006-08-07
Hi there 

I have a w800i, almost same phones, im not sure if u mean paired 
but to pair the devices i had to change my bluetooth hcid.conf (/etc/bluetooth) and change security to user and pairing to multi.
To send and receive files u also need to install Obex. 

Hope this helped

Zie

---

### Post by khaledaboualfa on 2006-08-11
Thanks for that Ziede. Definitely in the right track. For those having similar problems just install obexftp and you should see the usbdisc icon appear. Absolutely brilliant :).

---

