---
title: "Wireless LAN - dell vostro 1510"
date: 2010-09-06
forum: Hardware
---

### Post by fahadkk on 2010-09-06
Hi
 I am beginner in Linux . I wnt to know how to install Wireless Lan driver for Kubuntu netbook.
Downoaded the linux driver file from this URL** [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)**
**system 32 bit**
** Help pls properly**
 
**With regards**
**fahad k.k**

---

### Post by kelvin.illa on 2010-09-06
Hello.

I had this same problem on my sister's Dell 11z. If you go to "Hardware Drivers" (as far as I know) you will be shown two possible drivers for your Broadcom: one is "b43" and, the other, "STA." You could install only either one of them by clicking on a button to activate. Based on personal experience, b43 sucks; it's almost like not having a functional driver at all. So I say, go for the STA. The problem, however, with STA is that you're "NetworkManager Applet" doesn't work well with it (only currently because there's a workaround).

[[COLOR="Blue"]**_This_**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9729877&postcount=792") is a list of instructions if you're having trouble installing STA. This happens when you've already installed b43 beforehand and -- for some reason -- STA gets blacklisted (I think that's the term). If have have already successfully installed STA, skip to the bottom and add the PPA.

---

### Post by kelvin.illa on 2010-09-06
Oh yeah, I forgot. Just ask away if you need more clarification especially with 'adding a PPA.'

Cheers.

---

