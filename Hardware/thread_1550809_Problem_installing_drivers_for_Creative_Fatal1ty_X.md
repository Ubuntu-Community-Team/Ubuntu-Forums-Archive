---
title: "Problem installing drivers for: Creative Fatal1ty X-FI Titanium Champion"
date: 2010-08-11
forum: Hardware
---

### Post by gnomey on 2010-08-11
Hey guys,

I'm having problems installing the drivers for my new sound card. Its a: Creative Fatal1ty X-FI Titanium Champion Edition.

There is an open source Linux driver provided by Creative for this card: [http://opensource.creative.com/soundcard.html](http://opensource.creative.com/soundcard.html)

I'm trying to make the driver, but I get the following:

```
marcus@uBlazr:~/XFiDrv_Linux_Public_US_1.00$ sudo make
make -C /lib/modules/2.6.32-24-generic/build M=/home/marcus/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/marcus/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/marcus/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: error: sound/driver.h: No such file or directory
/home/marcus/XFiDrv_Linux_Public_US_1.00/xfi.c: In function ‘ct_card_probe’:
/home/marcus/XFiDrv_Linux_Public_US_1.00/xfi.c:55: error: implicit declaration of function ‘snd_card_new’
/home/marcus/XFiDrv_Linux_Public_US_1.00/xfi.c:55: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/marcus/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/marcus/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [all] Error 2
marcus@uBlazr:~/XFiDrv_Linux_Public_US_1.00$ 

```

Can anyone help me install this driver?

Thanks guys!

---

### Post by gnomey on 2010-08-12
Anyone have any idea on how to fix this?

---

### Post by gnomey on 2010-08-13
Sorry to bump this, but I paid &#8364;200 for this sound card just a few days ago, and its very annoying as I can't get this driver installed.

I would be very grateful to anyone who can find out what I'm doing wrong.

---

### Post by lidex on 2010-08-14
This, perhaps
[http://ubuntuforums.org/showthread.php?t=1448394](http://ubuntuforums.org/showthread.php?t=1448394)

---

### Post by renatotptr on 2011-05-24
After try a lot I do the instal editing some files. (thank you open souce software)

Download it [XFiDrv_Linux_Public_US_1.00.tar.gz]("http://support.creative.com/downloads/download.aspx?nDownloadId=10792") on creative support page extract and edited 2 files

on **xfi.c** I erase the line

> #include <sound/driver.h>

and erase this expression


> card = snd_card_new(index[dev], id[dev], THIS_MODULE, 0);
	if (card == NULL) {
		return -ENOMEM


On **ctatc.h** I erase this line 

> #include <sound/driver.h>

And works like a charm, Works in Ubuntu and Debian ,I belive it may work in any debian-like

---

### Post by nymusicman on 2011-06-05
I know you figured this out. But did you try ./configure

Secondly you do not have to sudo make, just make should work just fine, unless you have problems then sudo make (It's really a moot point but it helps with cleanup :)).

---

