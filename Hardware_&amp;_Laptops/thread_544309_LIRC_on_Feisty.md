---
title: "LIRC on Feisty"
date: 2007-09-06
forum: Hardware &amp; Laptops
---

### Post by james25182 on 2007-09-06
Hi.

I'm trying to set up a media centre using MythTV on my IBM Thinkpad T40. I've installed Feisty and Myth and got my USB DVB-T receiver working but I'm struggling to get any sort of remote control working. 

I have 4(!) IR devices I could use. These include:

Belkin SmartBeam USB adapter
Inbuilt IR adapter in Thinkpad
Mobile Action MA-600 Serial adapter plugged into USB-RS/232 adapter
IR adapter in Freecom DVB-T USB Stick

The only one I've managed to get any success with is the DVB-T stick with the included remote. However, this does not provide enough control or flexibility in Myth; for instance there's no up, down, or OK buttons. 

Ideally I want to use my Windows MCE remote (or my All-In-One Khameleon) to control Myth.

Can anyone provide an idiots guide to getting this working?

---

### Post by 505 on 2007-09-06
First, thy this command:

sudo irrecord -d /dev/lirc0 lircd.conf

It should receive signals from any device, and you can store each signal's name. If this does not work, LIRC is not set up properly. If is does work, the problem is with the remote functions settings. You might have already seen this, but nevertheless: [a good guide...](https://help.ubuntu.com/community/Install_Lirc_Feisty)

---

