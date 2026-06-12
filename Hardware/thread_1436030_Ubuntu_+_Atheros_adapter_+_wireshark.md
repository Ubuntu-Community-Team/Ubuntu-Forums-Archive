---
title: "Ubuntu + Atheros adapter + wireshark"
date: 2010-03-22
forum: Hardware
---

### Post by NorthDakota91 on 2010-03-22
Hi to all! 

I've got a little problem with my Acer Aspire 5220 laptop and Ubuntu 64bit. Actually I can't use Wireshark with my WiFi adapter (An Atheros AR5BXB63). The adapter works well (I am connected through it) but Wireshark's interfaces list is just empty and there is no way to make it work. Can someone help me please?

I'm a beginner so please be comprehensive with me ^^ and sorry for my english

---

### Post by NorthDakota91 on 2010-03-23
I found the solution - I just had to run Wireshark as root ^^ sorry for the stupid post, I'm an absolute beginner with linux..

---

### Post by ryan461 on 2010-07-09
> **NorthDakota91 said:**
> I found the solution - I just had to run Wireshark as root ^^ sorry for the stupid post, I'm an absolute beginner with linux..

Not a stupid post, helped me figure it out. and ive been using linux for a few years off and on haha.

---

### Post by thekat on 2010-07-20
> **ryan461 said:**
> Not a stupid post, helped me figure it out. and ive been using linux for a few years off and on haha.

I totally agree.. 
When I didn't get any interfaces.. figured I had munged it up..
but.. decided to try running from the command line..

```
sudo /usr/bin/wireshark &
```

Need a Super User Option on the Menu ...LOL

---

### Post by balaji31d on 2010-10-21
Thanks buddy, you helped me :KS

---

