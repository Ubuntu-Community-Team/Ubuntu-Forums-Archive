---
title: "Wireless connection problem"
date: 2010-04-30
forum: Hardware
---

### Post by edfoxx36 on 2010-04-30
Hey guys
I just installed 10.04 on my new Toshiba Satellite L510, and I cant seem to get the wireless to connect to anything. I'm able to see wifi connections, but nothing connects. The card is a Realtek RTL8191SE card. The ethernet connection works fine

Has anyone experienced the same problem, or know how to fix it?

E.F

---

### Post by dpsousa on 2010-04-30
LG R510 here.

RaLink RT2860 and the same problem. I tested with both 32 and 64 bits version. Works fine on 9.10 (I had to reinstall it :(). Ethernet also works fine.

---

### Post by RobGThai on 2010-04-30
I have the same problem with Lenovo G460, it's like the OS doesn't know the function exists at all.

---

### Post by Yoghoo on 2010-04-30
The Medion E1210 also has this problem. Worked in 9.10 and 9.04 but doesn't work anymore in 10.04. It also has a RaLink RT2860 network controller btw. Haven't found a fix yet.

---

### Post by edfoxx36 on 2010-04-30
I found this post [http://ubuntuforums.org/showthread.php?t=1460740&highlight=toshiba+l510](http://ubuntuforums.org/showthread.php?t=1460740&highlight=toshiba+l510)

The poster had a problem with Karmic, but Im wondering if the fix would work, just by changing the card model number.

Could someone try it out and post if they had success?

E.F

---

### Post by Rodney9 on 2010-05-13
I bought yesterday a Toshiba Satellite L500 Laptop with 500Gb hard drive and Intel Dual Core 2.20GHz. It has 2Gb Ram, Intel Video chipset and Realtek wireless.

I installed Ubuntu 10.4 64bit on it and it works perfectly.

Sound, wireless (after updating), sleep everything I have tried so far works beautifully and looks beautiful.

Rodney

PS: Make sure you update

---

### Post by whughes on 2010-06-02
Hi:

I have a Toshiba Satellite L550.
I installed 10.04

I had a lot of problems until I changed the default settings
of my account from custom to administrator.

In particular, this fixed the wireless connection (before
I could see the network but not access it)

At a terminal type 

   sudo users-admin

wait a while, for the gui to become active

pick your account

change to admistrator

---

### Post by i0950 on 2010-08-10
Rodney9    post#6
 Re: Wireless connection problem

================================

whughes post#7
 Re: Wireless connection problem

==================================

Rodney9 + whughes -- many Thanks

I was tearing out hair in an attempt to establish wireless on the wife's new L500
You have the total solution between the 2 of you

Thanks again :D

---

