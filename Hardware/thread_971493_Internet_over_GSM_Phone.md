---
title: "Internet over GSM Phone"
date: 2008-11-05
forum: Hardware
---

### Post by MeanEYE on 2008-11-05
Hi,

I have motorola ezx based phone which I want to use to connect to internet. Ubuntu recognises phone correctly and I can probably use it as standard dialup modem. What I want is to use GPRS connection from my phone.

When I click connect in ubuntu, my phones modem status reports "Carrier not found".

I've found some instructions online for using **wvdial** but I dont like typing commands in console each time I want to connect.

So my question is, is there a way to somehow temper the settings manually. Seems to me that ubuntu has wrong information about networks in my country (which is no strange thing, they change every year or so).

---

### Post by MeanEYE on 2008-11-11
:/ anyone?

---

### Post by sparkix on 2008-11-26
"Carrier not found" usually implies that it didn't detect a dial tone.  There should be an option to disable carrier detect.

Also, it is easier to get it working by command line first... and then implement a graphical way to do it.  Once you get wvdial to work, GnomePPP can provide a graphical interface for wvdial.

I recently got my laptop to connect to my blackberry with bluetooth and use it as an internet connection... by command line.  Now I am going to figure out how to make it easier and graphical.

---

### Post by napsterved on 2008-11-27
Can u help me out, from where do I get its drivers???
Usinng motorola L7i

---

### Post by MeanEYE on 2008-12-03
> **napsterved said:**
> Can u help me out, from where do I get its drivers???
Usinng motorola L7i

Sorry for late reply, there's a forum motorolafans.com... you can find all sorts of things there... among others drivers for L7... If not, you can find them @ modmymoto.com (I think)...

Last solution is... to install motorola phone tools... they include drivers for your and all other motorola phones...

---

