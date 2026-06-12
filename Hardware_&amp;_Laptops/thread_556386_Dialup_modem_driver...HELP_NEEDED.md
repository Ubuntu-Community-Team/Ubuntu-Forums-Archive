---
title: "Dialup modem driver...HELP NEEDED"
date: 2007-09-21
forum: Hardware &amp; Laptops
---

### Post by ibbiprince on 2007-09-21
I have Lucent(Agere system) dialip modem amd an Intel HaM modem (Ambient technologies)...

I installed Ubuntu 7.04 Fiesty Fawn few days ago and I am not able to find drivers for my modem..

Infact I have found itmodem driver for lucent and i also have a driver for my intel bet the problem is that I am a new one in linux world and dont know about codes and all those drivers were in form of scripts..

So can you people please help me in giving me instruction on that or may u tell me about a binary driver that dont needs much codes....

**also can intel HaM modem use 536ep driver?**

also how can i make sure that my modem is installed or not?

So plz help me out because I am tired of Windows and want to switch completely to Ubuntu linux...

---

### Post by geraldm on 2007-09-21
there is a howto
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
follow that as far as you can, and post if you find a place where that Howto can be improved
or need to ask.
On the HaM modem, you could try loading the driver and see if the log file identifies
the hardware as found.  There are quite a few threads on the lucent modems you could
search for. 

Gerald

---

### Post by ibbiprince on 2007-09-22
Thx...

When it say..
run make or Make install how to do this because these script type drivers are in form of text...how i run these??

Also I have found a .deb driver of lucent but when i try to install it say dependency error:kernel-image-2.6.12-10-686|linux-image-2.6.12-10-686

do i have to install thse too? and where to find these components..  I am using Ubuntu 7.04 on i386 type computer...
:confused:

---

### Post by Chilongola on 2007-09-22
I did battle with the same modem and had to give up.  I think that was the first time something beat me!!!   I ended buying an external Cnet modem.  Plug and play........ If you succeed kindly post.  I got in touch with the makers and they confirmed to me that it would not work.  They work good in Suse, Red Hat, Fedora but not in Ubuntu.

---

### Post by ibbiprince on 2007-09-22
lucent or intel?

---

### Post by ibbiprince on 2007-09-22
I have found a driver for my intel modem but it say that i should have kernel 2.6.20-16generic

I am currently using Fiesty..kernel 2.6.20-15generic..

How can i upggrade it?

---

### Post by Chilongola on 2007-09-23
I was making reference to Agere, sorry!!

---

