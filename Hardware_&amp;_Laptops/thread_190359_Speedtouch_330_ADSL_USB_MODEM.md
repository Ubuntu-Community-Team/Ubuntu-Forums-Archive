---
title: "Speedtouch 330 ADSL USB MODEM"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by rb1978 on 2006-06-06
Basically, I have tried to other distro's of linux, and will try one more this one before i just give up and become a slave once again to XP.

I have a Speedtouch 330 ADSL USB MODEM, which is all i have to connect to the net, so am writing this message on xp. I need to somehow get the modem to work in linux, but I don't know how i do it. and if there are files to transfer or downlaod to linux how do i get them there from windows

oh I'm a NEW! user to linux.

---

### Post by bruce89 on 2006-06-06
Follow this [Howto]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html").  I have this modem too, and I used this howto to make it work.  I no longer use the modem though, I just use a router.

---

### Post by rb1978 on 2006-06-06
I have done that already, after writing my question in the forum, i found that page stuck everything i needed onto a cd/rw and copied it over. followed the instructions but nothing is happening. Is there a way to check the boot menu? to see whats loading and not loading up. like in xp you can goto services to make sure whats on or off?

---

### Post by notoriousdbp on 2006-06-06
I've used that howto many times and it works straight away every time.  To help I saved the web page so I could copy and paste the instructions.  You are using the right firmware for your modem aren't you?  Basically if you look at the modem while you boot up the lights should come on when you power up the pc, blink off and on again during the ubuntu splash screen and then just one light should flash while it connects.  This light should finish flashing about the same time or a little after the login screen has appeared and that's when you're connected and ready to go.

---

### Post by rb1978 on 2006-06-08
[QUOTE=notoriousdbp]I've used that howto many times and it works straight away every time.  To help I saved the web page so I could copy and paste the instructions.  You are using the right firmware for your modem aren't you?  Basically if you look at the modem while you boot up the lights should come on when you power up the pc, blink off and on again during the ubuntu splash screen and then just one light should flash while it connects.  This light should finish flashing about the same time or a little after the login screen has appeared and that's when you're connected and ready to go.[/QUOTE]

I've done something much better, to save all these problems am sorting out a d-link dsl 540 adsl router from a friend of my girlfriends for a tenner, so hopefully by the weekend i'll be up and running properly and be part of the ubuntu community:D

---

### Post by sooqing on 2006-06-17
To follow the Howto, I need to download a firmware from speedtouch.com which I assume in non free. Does anyone know where to get a free driver for ST330 on Ubuntu 6.06?

---

### Post by jeffreyvergara.NET on 2006-06-17
I think it's free. You can also try and google out "SpeedTouch330_firmware_3012.zip" that's the one I used with my Speedtouch.

I also made and backed up the files needed for installation. (secrets, dial, speedtch, firm-extractor and SpeedTouch330_firmware_3012.zip) so I'll only do the following steps to install my Speedtouch 330.
> 
unzip SpeedTouch330_firmware_3012.zip &&
chmod +x firmware-extractor &&
./firmware-extractor ZZZL_3.012
sudo cp speedtch* /lib/firmware/2.6.15-25-686
sudo install -m 600 secrets /etc/ppp/chap-secrets &&
sudo install -m 600 secrets /etc/ppp/pap-secrets 
sudo install -m 600 speedtch /etc/ppp/peers 
sudo install -m 744 dial /etc/init.d &&
sudo ln -s ../init.d/dial /etc/rc2.d/S95dial &&
sudo ln -sf ppp/resolv.conf /etc/resolv.conf 


I also copied "speedtch-1.bin" and "speedtch-2.bin" from  /lib/firmware/2.6.15-25-686 (or whatever your kernel version is) to  /lib/firmware/ directory because in my experience when I updated my kernel the speedtouch will not connect after reboot.

---

### Post by sooqing on 2006-06-18
oh, i am already using the driver from speedtouch.com to post this. however the driver is not under the GPL. i was told there is a free version of the driver and i hope to use it.

btw i copied the firmware directly to the ../lib/firmware since i do not upgrade my kernel..

---

### Post by dennislowe on 2006-09-16
I am new to ubuntu after reading good writeups but after trying to install my speedtouch 330 it reminds me of old dos. I thought installation had advanced at least to the state of XP, I am afraid I too will be reinstalling XP after tonight fiasco.

---

### Post by Markkreuzz on 2006-09-18
I too have this modem the silver one. it works just fine in my PC but IMHO it works better in windows. much better if you'd get a router.

---

