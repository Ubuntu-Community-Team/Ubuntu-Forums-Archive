---
title: "How do I check my Intel Chipset ?"
date: 2009-07-30
forum: Hardware
---

### Post by sml on 2009-07-30
I would like to find out the chipset on my Lenovo notebook with intel chipset. GM45, GL40, PM965 etc? 

[http://www.intel.com/products/laptop/chipsets/index.htm?iid=chipsets_body+nb_all](http://www.intel.com/products/laptop/chipsets/index.htm?iid=chipsets_body+nb_all)

a) lspci -v just provides this ...
Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Lenovo Device 3a00

b) using the intel chipset identification utility opens with wine win98 but is not up to date. using win xp, there is a wine issue requiring admin rights ...
[http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=861&lang=eng](http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=861&lang=eng)

c) tried wiping my whole ubuntu install & installing Win XP but it didn't like my Ext 4 partition and would not install.

d) tried the pci id list and it just says mobile 4 express etc etc
[http://pci-ids.ucw.cz/read/PC/8086/2a42](http://pci-ids.ucw.cz/read/PC/8086/2a42)

---

### Post by davidmohammed on 2009-07-30
I'm not at my jaunty laptop to try this... but

does 

sudo dmidecode

give you the info you require?

---

### Post by thezood on 2009-07-31
> **sml said:**
> I would like to find out the chipset on my Lenovo notebook with intel chipset. GM45, GL40, PM965 etc? 

[http://www.intel.com/products/laptop/chipsets/index.htm?iid=chipsets_body+nb_all](http://www.intel.com/products/laptop/chipsets/index.htm?iid=chipsets_body+nb_all)

a) lspci -v just provides this ...
Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Lenovo Device 3a00

b) using the intel chipset identification utility opens with wine win98 but is not up to date. using win xp, there is a wine issue requiring admin rights ...
[http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=861&lang=eng](http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=861&lang=eng)

c) tried wiping my whole ubuntu install & installing Win XP but it didn't like my Ext 4 partition and would not install.

d) tried the pci id list and it just says mobile 4 express etc etc
[http://pci-ids.ucw.cz/read/PC/8086/2a42](http://pci-ids.ucw.cz/read/PC/8086/2a42)

Try running this instead:
```
lspci | grep VGA
```

---

### Post by wojox on 2009-07-31
```
lspci -v | less
```

---

### Post by no_ordinary_funace on 2010-04-13
I can't remember now, but I was wondering the same thing about my chipset and I read something about using a terminal to enter

 ```
lspci | grep Network
```, 

which told me that my chipset is a Ralink RT3090 802.11n.

Wojox's advice about "less" gives A LOT of information (well it did for me) and I found it helpful pressing the "h" button which brings up A LOT more information about commands and whatnot.  

I saw someting about intel chipset, which is what I found when I did a search for my particular brand of computer, but it was only when I used the "grep Network" command that I saw something about my chipset being "Ralink".

I dunno why that is, though, and I don't know what "less" is, either, but golly gosh there sure is a lot to learn!

---

### Post by Zip247 on 2010-06-26
you could install sysinfo also.

sudo apt-get install sysinfo

after install it will be accessible from applications>system tools

---

### Post by COKEDUDE on 2010-06-27
This did the trick for me :). 
```
sudo lspci -v
```

---

### Post by IceKold0 on 2012-04-20
This just saved my day!

Work user was unable to boot to Windows and was stuck at the usual blinking cursor...

So, I popped in my Ubuntu 12.04 USB, "sudo lspci -v" and hey-presto "Intel 82801IBM/IEM - Intel ICH9M/ICH9M-E"... booted the XP CD "F6" for USB/Mass storage drivers and instantly could see the correct iaStor to load!

It turned out that when XP setup loaded I was shown an all too familiar first partition of "100MB"... the user didn't know what Windows was running and thank god I found this first! It was Windows 7!

Cut a long story short... the Gods and Goddesses of UbuntuForums.org have come to the rescue once again!

Thank you!

=D>

---

