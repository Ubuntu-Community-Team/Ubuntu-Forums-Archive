---
title: "soundcard driver help"
date: 2009-02-14
forum: Hardware
---

### Post by Snake64 on 2009-02-14
Hi, I'm not sure if I am posting in the right section but I just installed ubuntu for the first time and everything seems fine except my soundcard does not work. I have checked in terminal and it did detect the hardware (Sounblaster X-Fi Fatal1ty). I went to the creative website and downloaded the driver for linux  (did i download the right one?) at 

[http://support.creative.com/Products/ProductDetails.aspx?catID=1&CatName=Sound+Blaster&subCatID=208&subCatName=X-Fi&prodID=14065&prodName=X-Fi+Platinum](http://support.creative.com/Products/ProductDetails.aspx?catID=1&CatName=Sound+Blaster&subCatID=208&subCatName=X-Fi&prodID=14065&prodName=X-Fi+Platinum)


I have extracted the folder to my desktop but I don't know how to install it!!! The readme file doesn't help it just says:

In terminal,


1) Goto source directory

2) Execute make command as root

   make

   make install


I can get the directory opened but make install does not work...

Any help would be much appreciated.

---

### Post by glotz on 2009-02-14
You'll need to input the last command as root, i.e.```
sudo make install
```

You might want to check out a package by the name of checkinstall too.

---

### Post by Snake64 on 2009-02-14
Tried that and it says:

Copy module files...
Update module dependency relationships...



for a very very long time...left it for half an hour at least.

---

### Post by Snake64 on 2009-02-15
Anyone know what to do? Or about someone walk me through how to get my soublaster x fi card to work. It detects intel soundcard or something but my speakers are connected to my sounblaster card.

---

### Post by glotz on 2009-02-15
Well, one thing worth trying is to disable the onboard card in BIOS setup at boot time. I hope you get it sorted out. I think the folk at Creative should help you with their product.

---

