---
title: "X-Fi Audio driver, Screen Resolution and Boot problems"
date: 2009-12-25
forum: Hardware
---

### Post by logiq on 2009-12-25
Hello everyone. 

First of, sorry for making this post so long. I hope you bear with me.

I'm using a X-Fi XtremeGamer Fatal1ty Pro Audio card, and having issues installing the driver.

There's a driver already in ubuntu 9.10 and that works, but I don't think it supports the fully capability of this card.. The sound doesn't sound as it used to under Windows Vista. I figured this might be because of the driver, and so I tried to install this one from the creative support site:

Creative Sound Blaster X-Fi and X-Fi Titanium Series Linux 32-bit / 64-bit Driver Source Release 

[http://support.creative.com/Products/ProductDetails.aspx?catID=209&CatName=X-Fi&subCatID=208&subCatName=X-Fi&prodID=15854&prodName=X-Fi+XtremeGamer+Fatal1ty+Pro+Series&bTopTwenty=1&VARSET=prodfaq:PRODFAQ_15854,VARSET=CategoryID:209](http://support.creative.com/Products/ProductDetails.aspx?catID=209&CatName=X-Fi&subCatID=208&subCatName=X-Fi&prodID=15854&prodName=X-Fi+XtremeGamer+Fatal1ty+Pro+Series&bTopTwenty=1&VARSET=prodfaq:PRODFAQ_15854,VARSET=CategoryID:209)

But I can't seem to be able to install it. I extract it to my desktop, then fire up terminal and type in "sudo make" but all it gives me is a couple of errors:

```

thomas@thomas:~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo make
make -C /lib/modules/2.6.31-16-generic-pae/build M=/home/thomas/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic-pae'
  CC [M]  /home/thomas/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/thomas/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: error: sound/driver.h: No such file or directory
/home/thomas/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c: In function ‘ct_card_probe’:
/home/thomas/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:55: error: implicit declaration of function ‘snd_card_new’
/home/thomas/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:55: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/thomas/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/thomas/Desktop/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic-pae'
make: *** [all] Error 2

```

I used to have an application to this card as well. Sort of control panel, where you could set various options like mix, bass, etc etc.

Does anyone know if there's a linux version of this application? Maybe any way of settings these settings through a config file?




My second problem is that I'm having trouble with my screen resolution. I'm using dual view, a monitor with 1680x1050 and my main monitor, which can support 1900x1600. But I can't seem to set my main monitor higher than 1680x1050. I did have it on 1900x1600 before I plugged in my second monitor, which is rather strange.

So I googled around, and found a thread that suggested to edit the xorg.conf file. 

```

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1680x1050"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1680 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1680x1050"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

```

So I tried putting in 1900x1600, but it didn't seem to do anything at all..

My final problem is that I'm having trouble booting up ubuntu. I've got various errors like "GNU GRUB Loading Read Error", "Kernal Panic" and sometimes I'm able to choose which I want to boot with, but after I've pressed enter it just hangs for like 30sec, nothing happens. After couple of restarts I get in.. 




I'd really appreciated if any of you could give me some assistance to these problems.

Thanks in advance, and happy holidays!

---

### Post by logiq on 2009-12-25
Bump.. Anyone?

---

### Post by logiq on 2009-12-26
Bump..

---

