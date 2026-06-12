---
title: "AVerTV TwinStar (dvb-t) support in ubuntu"
date: 2009-11-12
forum: Hardware
---

### Post by username-username on 2009-11-12
Hello everybody.

I would like to use **AVerTV TwinStar** (A825) dvb-t card in linux, but I couldn't find any tutorial or something like it in google.
I hope that there is a way how to run this device in linux.
Please advise me how can I do it.

dmesg:
```

[ 8837.765553] usb 1-2: USB disconnect, address 5
[ 8842.332550] usb 1-2: new high speed USB device using ehci_hcd and address 6
[ 8842.489155] usb 1-2: configuration #1 chosen from 1 choice
```

lsusb:
```

Bus 001 Device 006: ID 07ca:0825 AVerMedia Technologies, Inc. 
```


link to product homepage:
[http://www.avermedia.com/avertv/Product/ProductDetail.aspx?Id=491]("http://www.avermedia.com/avertv/Product/ProductDetail.aspx?Id=491")


Thank you in advance for any help. :)

btw I use:
Kubuntu 9.10 64bit
*2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64 GNU/Linux*

---

### Post by XavierGr on 2009-11-13
I am in search for an answer about this too.
Any hints?

---

### Post by pedja_portugalac on 2009-11-13
My dvb-t card is different from yours but if it's detected by ubuntu, and it is as I see, following thread can help you
[http://ubuntuforums.org/showthread.php?t=1324744](http://ubuntuforums.org/showthread.php?t=1324744)

---

### Post by username-username on 2009-11-14
it is **not working**, because there wasn't any DVB-T card found :

```
iii@laptop:~$ w_scan -ft -c DE -X -R N -O N >> ~/.mplayer/channels.conf
w_scan version 20090808 (compiled for DVB API 5.0)
using settings for GERMANY
DVB aerial
DVB-T Europe
frontend_type DVB-T, channellist 4
output format czap/tzap/szap/xine
Info: using DVB adapter auto detection.
main:2898: FATAL: ***** NO USEABLE DVB CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.
iii@laptop:~$ 
```

---

### Post by pedja_portugalac on 2009-11-14
Restart computer and try again. What is Ubuntu version you are using? If it's not Karmic try upgrading.

---

### Post by username-username on 2009-11-16
hi,

These instructions not worked for me ( even I have the latest version of Kubuntu - 9.10 Karmic (upgraded) )

---> I found information that the chip inside is AF9035, I hope it might be helpful for running under linux. <---

---

### Post by tominated on 2009-12-19
If anybody has figured this out, it would be awesome if they could post it here!

---

### Post by shawe_ewahs on 2010-01-03
I have the same problem.

---

### Post by shawe_ewahs on 2010-01-03
I found this information:

[http://linuxtv.org/wiki/index.php/TerraTec_Cinergy_T_Stick#Method_B](http://linuxtv.org/wiki/index.php/TerraTec_Cinergy_T_Stick#Method_B)
[http://patchwork.kernel.org/patch/61950/](http://patchwork.kernel.org/patch/61950/)

I can't do that it work for me.

---

### Post by elchebud on 2010-09-11
it doesn't work for me... any new ideas?

its a great card with double dvb-t tuner, and i rather install windows again just for watching TV then buy another one...

so... if possible...

could someone tell me how to get this thing to work?!

---

### Post by cta.pruebas on 2010-11-11
Anybody got this USB TV Turner working. I have tried installing Mythbuntu 10.10 and followed the steps described on previous post, but I couldn't install it. I need help.
 
Regards

---

### Post by jimmers on 2010-11-12
I run the AverMedia Volar A815 using Kaffeine, but I had to install DVB-Apps, w-scan, and 
download the driver, also I found that to watch TV using Kaffeine I hade to install Gxine, I cannot get the A815 to work with any other TV Programme, but works, it gives me 40 TV Channels and 20 radio Stations.

May not work for you, but worth a try

Luck

---

