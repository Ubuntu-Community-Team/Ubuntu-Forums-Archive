---
title: "Black Screen on Lenovo x60 tablet"
date: 2009-07-27
forum: Hardware
---

### Post by jbingle on 2009-07-27
Hi, I am new to Ubuntu and this is my first posting. I often get a black screen when I am on various websites. My machine runs on XP professional and it is regularly updated with lenovo updates and windows updates, virus checked and all the normal stuff like that. 

When the screen goes black it does not crash the hard drive as I can still hear it working and if on skype for example I can still talk. 

It is still under a three year warranty but before calling Lenovo I was wondering if anyone would know of this error and what the solution is. Sometimes, the screen goes white instead of black.

many thanks for your help in advance. I have seen similar postings but on different Models of lenovo machine.

jbingle

---

### Post by Favux on 2009-07-27
Hi jbingle,

Welcome to Ubuntu!

You don't mention which version you are using.  Is it Jaunty (9.04)?  I ask because there are some issues with Intel motherboard graphics in Jaunty.  I think the X60t has Intel video, doesn't it?  To check in a terminal enter:
```
lspci | grep VGA
```
It involves the change from EXA to UXA acceleration in the Xorg Intel drivers I think.  There's threads dealing with how to configure it to work better or update it.  You might be better off posting in the Multimedia & Video forum.

Hopefully someone who knows more about (Intel) video will help you out, but at least this may be a start for you.

---

