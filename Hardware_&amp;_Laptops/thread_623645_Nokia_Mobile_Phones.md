---
title: "Nokia Mobile Phones"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by subs on 2007-11-26
i have a nokia e50 mobile device....

is it possible for me to synchronise it with my ubuntu 7.10 using the data cable or bluetooth without using the nokia software....

i have checked online.... nokia does not have any software suite for any linux based system.... and i cant get the nokia software to work on wine......:(:(:(

---

### Post by erginemr on 2007-11-26
Hello,

I am not sure about Nokia E50, but I am using Sony Ericsson K700i. And when I connect it to my Ubuntu via a compatible cable, Ubuntu sees the phone as an external hard drive and allows me to view, add and remove images and music.

So, if you are looking after checking your address book, messages or syschronizing your schedule, it will possibly not work without a specific application, but with a data cable only, you may at least see and update the multimedia files in it.

There is also an interesting bluetooth application and a background deamon for bluetooth installed by default in Gutsy, but I have yet to try it. You need to have a bluetooth receiver for it to work though (most laptops already have it, and there are cheap bluetooth dongles available in the market.) I would go for the cable anyway, because it is much faster than bluetooth.

---

### Post by erginemr on 2007-11-26
Wow, unbelievable! Check this out!

There already was an application to handle mobile connectivity in Linux:
[http://wammu.eu/](http://wammu.eu/)

It is already available in the Synaptic repositories, so a simple: 
sudo aptitude install wammu
will do.

The bad news is that, the support for E50 is, according to their site, very limited in terms of functionality. But you may still give it a try anyway.

---

### Post by subs on 2007-11-26
> **erginemr said:**
> Hello,

I am not sure about Nokia E50, but I am using Sony Ericsson K700i. And when I connect it to my Ubuntu via a compatible cable, Ubuntu sees the phone as an external hard drive and allows me to view, add and remove images and music.

So, if you are looking after checking your address book, messages or syschronizing your schedule, it will possibly not work without a specific application, but with a data cable only, you may at least see and update the multimedia files in it.

There is also an interesting bluetooth application and a background deamon for bluetooth installed by default in Gutsy, but I have yet to try it. You need to have a bluetooth receiver for it to work though (most laptops already have it, and there are cheap bluetooth dongles available in the market.) I would go for the cable anyway, because it is much faster than bluetooth.

well... i have been able to use work on the files.... i have a memory card reader... which works on ubuntu....

however.. im not able to backup my contacts... etc

---

### Post by LordThundering on 2007-11-26
I've been fideling w/ using ubuntu and my n70 - never got it quite working, now i'm using a syncml-service online, it was way easier and i can access my stuff anywhere. There are some tools out there, that can do it. Look into Gnokii, etc - but i'm not quite sure how well the e50 or any symbian s60 is supported!

---

