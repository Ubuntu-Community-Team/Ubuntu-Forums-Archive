---
title: "Installing USB Driver Belkin F507050"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by mcclunyboy on 2009-09-11
Hi

I am trying to install my USB Network adapter - the Belkin F507050 - Version 4000

I have read a few articles on this website about similar adapters without much success.

I have successfully installed the ndiswrapper but the .inf I suspected was the driver is apparently wrong.  Apart from that file I cannot find any other .inf's.

The CD has no .inf's on it.

I am new to Ubuntu so would like a response in simple terms please.

thanks for ur help...alex

---

### Post by spcwingo on 2009-09-11
Open a terminal and post the output of this command:

```
lsusb
```

This will give us more information on the chipset of the adapter.

---

### Post by mcclunyboy on 2009-09-12
ID-050d:705c Belkin Components F5D7050 v4000 Wireless adapter


Sorry a D not a 0

---

### Post by spcwingo on 2009-09-12
The only info I could come up with is the guide on Ubuntu wifidocs.  Here's a link:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver)?highlight=(WifiDocs%2FDevice)]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver)?highlight=(WifiDocs%2FDevice)")

---

### Post by mcclunyboy on 2009-09-12
anyone give me a nice and easy link to a cheap wireless adapter that works on a dual boot machine with ubuntu 9.04 and windows xp..;.

considering getting windows 7 too.

if its going to be a hastle with this device i may just get an easier one.

---

### Post by spcwingo on 2009-09-13
As long as you stick with realtek chipsets you'll be good.  I've personally had nothing but good luck with the rtl8187 chipset based adapters.  I look around and see if I can hunt you up a good one.  In the meantime you might want to give ebay a look.

---

### Post by spcwingo on 2009-09-13
Sorry, double post.

---

### Post by mcclunyboy on 2009-09-14
thanks I shall have a look.

I should point out it anyone has an internal wireless card then that is good.  I have a few PCI and PCIe slots free.

Anyone got a link to a cheap one?

---

### Post by mcclunyboy on 2009-09-15
Hi again

Any experience of using a ZyXEL G-302 v3 ?

I am probably going to buy one!

---

### Post by Alan F on 2009-09-15
As you have ndiswrapper installed you are almost there.

Download the DRIVER ONLY package from BELKIN (<1MB) from website below to a Windows (wash my mouth out!) machine.

Extract the files from the .exe file and transfer them (.cat, .sys, .inf) to the Ubuntu box. Now install them.

[http://www.belkin.com/uk/support/article/?lid=enu&pid=F5D7050uk&aid=6121&scid=283](http://www.belkin.com/uk/support/article/?lid=enu&pid=F5D7050uk&aid=6121&scid=283)

---

### Post by mcclunyboy on 2009-09-16
Hi

Thanks for the reply.

I did try this but it turns out I had tried it already.  The .inf file is not recognised - i used the GUI for ndiswrapper because I couldnt remember how to do it the other way.  Anyway it picked it up then said the driver was not recognised.

Annoying - especially because I need low profile cards which are harder to get on ebay.

---

### Post by mcclunyboy on 2009-09-24
someone must use ubuntu 9.04 wirelessly...what device u got?

low profile wireless adapter or usb adapters please

---

