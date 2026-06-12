---
title: "Bluetooth  headset"
date: 2005-12-14
forum: Hardware &amp; Laptops
---

### Post by redman5087 on 2005-12-14
Hi,
I installed the bluetooth-alsa driver succesfull.
I "modprobe snd-bt-sco" successfully.
Then I did "hciconfig hci0 voice 0x0060"
I made a bluetooth pin file:
echo '#!/bin/sh' > /etc/bluetooth/pin
echo 'echo "PIN:0000"' >> /etc/bluetooth/pin
chmod +x /etc/bluetooth/pin

Restarted hcid

When I do:
btsco -v 00:0D:44:03:6B:8A
I get
btsco v0.4c
Device is 2:0
Voice setting: 0x0060
Can't connect RFCOMM channel: Resource temporarily unavailable


I did everything by another thread on this forum:
[http://ubuntuforums.org/showthread.p...bluetooth-alsa](http://ubuntuforums.org/showthread.p...bluetooth-alsa)

Can someone help, please

Kind regards,
redman

---

### Post by PaganHippie on 2005-12-15
You don't say what BT headset you're trying to pair to your computer.  Is it one designed for, say, a wireless/cellular phone?  Are you trying to use it to listen to music?  With Skype?

There are a lot of different BT profiles, and not every device supports every one of them.  Your particular headset may not be compatible with what you're trying to do with it.  Then again, it might, but just may not be configged right (yet).  BT devices can be very temperamental.

What specific hardware are you working with (PC and headset), and what, specifically, are you trying to accomplish?  (BTW, PIN: 0000 doesn't work with all BT configs; sometimes you have to supply [or create] a unique PIN.)

---

### Post by redman5087 on 2005-12-15
Dear PaganHippie,

Thank you very much for your reply.
Yes, I'm also trying to play music with my headset.
The Bluetooth dongle I use is the Cellink BTA-6030 (2.0 class 1). 
It supports the "headset" and "a2dp" profile.
As for my Bluetooth stereo headset it's difficult to say which manufacterer it made.
I imported it from China. It support the "a2dp" and the "headset" profile. You can take a look at the headset on "http://www.mobile21cn.com/product.asp?ClassId=96". It's the bta-068.
I must say, the headset works without any problem on my windows xp machine.
I can perfectly listen to music with my headset on my windows machine.

I really appreciate if you could help me.

Kind regards,

Redman

---

### Post by redman5087 on 2005-12-21
The problem is solved now.
I had to install Breezy. I used Hoary

---

