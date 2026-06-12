---
title: "Ricoh r5u870 driver Webcam HP, Sony Vaio Ubuntu 11.10"
date: 2011-10-18
forum: Hardware
---

### Post by novatillasku on 2011-10-18
I need configure my webcam with Ricoh r5u870 driver in Oneiric.

Some idea?

---

### Post by teb on 2011-10-23
Hi,

I&#7743; having the same issue here. Sony Vaio SZ now runs Ubuntu 11.10, but the webcam isnt being recognised somehow. Or let me be more precise: 

lsubs shows:
Bus 001 Device 004: ID 05ca:1830 Ricoh Co., Ltd Visual Communication Camera VGP-VCC2 [R5U870]

So apparently the device is being recognised. But it doesnt show up in dmesg, nor in cheese or any webcam app.

Did you find out how we get this thing to work?

cheers,

teb

---

### Post by treminy on 2011-10-23
hey there,
i had the same problem under oneiric on
Sony Vaio VGN-SZ71MN with the webcam:
05ca:183a Ricoh Co., Ltd Visual Communication Camera VGP-VCC7 [R5U870]
i installed r5u87x in following steps:
1. sudo add-apt-repository ppa:r5u87x-loader/ppa
 2. sudo apt-get update
3. sudo apt-get install r5u87x
4. sudo /usr/share/r5u87x/r5u87x-download-firmware.sh
( check: [https://launchpad.net/~r5u87x-loader/+archive/ppa](https://launchpad.net/~r5u87x-loader/+archive/ppa) )
webcam works now. maybe it helps you?

---

### Post by kirpitis on 2011-11-13
> **treminy said:**
> hey there,
i had the same problem under oneiric on
Sony Vaio VGN-SZ71MN with the webcam:
05ca:183a Ricoh Co., Ltd Visual Communication Camera VGP-VCC7 [R5U870]
i installed r5u87x in following steps:
1. sudo add-apt-repository ppa:r5u87x-loader/ppa
 2. sudo apt-get update
3. sudo apt-get install r5u87x
4. sudo /usr/share/r5u87x/r5u87x-download-firmware.sh
( check: [https://launchpad.net/~r5u87x-loader/+archive/ppa](https://launchpad.net/~r5u87x-loader/+archive/ppa) )
webcam works now. maybe it helps you?
Hey!

This worked for me with Ricoh r5u870 webcam on Sony Vaio VGN-FZ31E

---

### Post by pspworld123 on 2011-12-14
thanks

---

### Post by uBantuRocks on 2012-01-13
Awesome, trying from lot of days to get it worked and almost in the verge of posting the new post.
This procedure worked for me and its really good ubuntu forum....
I had "Bus 001 Device 003: ID 05ca:1836 Ricoh Co., Ltd Visual Communication Camera VGP-VCC4 [R5U870]"

---

### Post by androphi on 2012-03-23
Great work!. 

This worked for me with Ricoh r5u870 webcam on Sony Vaio VGN-FZ11S

but i got flipped picture.

any suggestion?

---

### Post by morpet28 on 2012-03-26
Does anyone know if this will work on a vaio vgn-fe21h?

---

