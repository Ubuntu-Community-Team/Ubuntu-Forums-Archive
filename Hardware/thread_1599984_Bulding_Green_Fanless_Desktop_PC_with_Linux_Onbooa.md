---
title: "Bulding Green Fanless Desktop PC with Linux Onbooard for less then 500."
date: 2010-10-18
forum: Hardware
---

### Post by Sylslay on 2010-10-18
I am looking for mobo with intel Atom procesor and 3-4 Sata.

Idea is bulding pc with that spec:

PSU - Fanless
ITX Mobo with low power CPU, and 3-4 sata

Found 
ASUS AT5NM10-I with 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131630](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131630)
HDD - SSD  64 GB, probably Kingston for less than 150euro.
HDD - 7200 rpm, 500gb
4 GB Ram
GPU - Nvidia with  pasive cooling, min 512 Ram

Goal is bulid PC with good speed, and less than 80 Watt.

---

### Post by cascade9 on 2010-10-18
Depending on what you call 'good speed', and intel atom isnt going to give you that. I cant see any intel atom really using 4GB (yes, possible, but really...who is goignt o run VMbox on an atom?) 

You might do better to look at low power AMD CPUs ('e' series) or intel laptop chip, like this- 

JetWay JNC64-LF Socket P
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813153174](http://www.newegg.com/Product/Product.aspx?Item=N82E16813153174)

A Whole Big Bunch Of Intel Socket 'P' CPUs- 
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100008599+600050023&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=759&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100008599+600050023&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=759&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

The motherboard you've linked only has a PCI slot, not PCIe. That really limits what nVidia GPUs you can run, and they are slower thanks to the slow PCI interface......and the choices you will have are normally about twice the cost of normal PCIe version.

BTW, almost all the standalone nVidia GPUs will push 40+watts TDP, and TDP is normally lower than the actual current draw. Its goingt o be really hard to keep under 80watts with a nVidia card, you might have to use an intergrated GPU to go that low.

8Edit- doh. I should have asked '500 whats? Euros, or is that converted into US$?'

---

### Post by Sylslay on 2011-01-09
Thanks for 
"
The motherboard you've linked only has a PCI slot, not PCIe. That really limits what nVidia GPUs"

I never notice this.

---

