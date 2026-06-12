---
title: "How do I share a Printer via a network?"
date: 2005-09-29
forum: Hardware &amp; Laptops
---

### Post by ygarl on 2005-09-29
Hello,

I have 2 PCs, both running Breezy (I know - this is a Hoary list, but I doubt the technique is any different...). My main PC is not connected to my printer (an HP PSC 1215 scanner/inkjet).

The printer works perfectly on the other PC, and they are networked together quite nicely, i.e. I can swap files, share directories, etc.

I was just wondering how to:
a) share the printer on the second PC, bearing in mind this is a USB printer
b) actually PRINT on the second printer from my main one.

I'm sure it's stupidly simple, but I haven't found any obvious way to do so...

Thanks!

---

### Post by xmastree on 2005-09-29
From memory...
First you need to edit /etc/cups/cupsd.conf on the one with the printer connected.
Find this bit:
```
#Port 80
#Port 443
#Port 631
#
Listen 127.0.0.1:631
```and uncomment the Port 631 line
Then, find this bit:
```
<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>
```And include the other computer's ip address in the  Allow section.
Then, on the other machine, edit /etc/client.conf and change 
```
#ServerName myhost.domain.com
``` to 
```
ServerName [COLOR="Red"]ip.address.of.server[/COLOR]
```
That's how I think I did it... Might have forgotten something along the way though.

---

### Post by Biased turkey on 2005-09-29
That FAQ on the Ubuntu Wiki should get you starting:
[https://wiki.ubuntu.com/FrequentlyAskedQuestions#head-31236fe6767d32d8849819b22f0da7da5026023b]("https://wiki.ubuntu.com/FrequentlyAskedQuestions#head-31236fe6767d32d8849819b22f0da7da5026023b")

You have to install the CUPS package first of course.

---

