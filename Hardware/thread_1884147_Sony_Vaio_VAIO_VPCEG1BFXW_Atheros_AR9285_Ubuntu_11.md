---
title: "Sony Vaio VAIO VPCEG1BFX/W Atheros AR9285 Ubuntu 11.10 Wireless Driver Issue"
date: 2011-11-20
forum: Hardware
---

### Post by JF382 on 2011-11-20
So I installed Ubuntu 11.10 64 bit on my Sony Vaio laptop and I have no wireless driver. If I click enable wireless under the network icon, it just won't do it. No matter how many times I click it. Is anyone else having this issue? My wireless worked fine on WIndows 7. I need to get this wireless driver going or Ubuntu is useless for my laptop. Thanks, any help would be VERY MUCH appreciated.

---

### Post by searchfgold6789 on 2011-11-20
See this:
[http://askubuntu.com/questions/67437/how-do-i-install-a-driver-for-an-atheros-ar9285](http://askubuntu.com/questions/67437/how-do-i-install-a-driver-for-an-atheros-ar9285)
Let us know if you need further assistance beyond that.

---

### Post by connor111 on 2012-01-02
I'm having the same issue and blacklisting has not worked for me. I'm running an asus k53ta and had to install using the alternate disk. When I click on connections it says "device not managed", I can however connect to my home network (even though it says I'm not) because this was the network used during the installation. I cannot connect to any other networks however. Do you have any other ideas about this issue?

---

### Post by librechick on 2012-01-03
> **connor111 said:**
> I'm having the same issue and blacklisting has not worked for me. I'm running an asus k53ta and had to install using the alternate disk. When I click on connections it says "device not managed", I can however connect to my home network (even though it says I'm not) because this was the network used during the installation. I cannot connect to any other networks however. Do you have any other ideas about this issue?

This chipset definitely works. I used it the other day without an issue. It sounds like a problem specific to your setup.

When you edited the black list file what did you put in it?
/etc/modprobe.d/blacklist.conf   This:

  blacklist acer_wmi [FONT=Verdana]
is probably not correct for your laptop. My guess is you probably need to do:

blacklist asus_wmi

Also make sure you are editing the right file and doing so with administrator permissions. It might be the file was not actually saved and you missed the error indicating this. 

Run the following from the terminal:

gksu gedit [/FONT]/etc/modprobe.d/blacklist.conf

---

### Post by D1382 on 2012-03-06
I'm having the same problems.  I've tried the above with no luck.

when I run rfkill list nothing is blocked yet my wireless still does not work.

---

