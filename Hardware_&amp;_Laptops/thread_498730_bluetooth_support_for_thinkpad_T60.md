---
title: "bluetooth support for thinkpad T60"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by shred_thrash on 2007-07-11
Hey all,

I recently installed ubuntu 7.04 on my thinkpad T60.  I have managed to get everything working (including the X1400, which was...fun :P ) and now the last thing on my list that I am having a lot of troubles with is connecting my bluetooth headphones.

I have been trying to get them to work and troubleshooting the matter for a while on my own with no success.  I later tried searching the web for related documentation but none of it was successful.  I now come to you guys to see if you would be able to help me sort this matter out.

As I mentioned earlier I have a new thinkpad T60 and the bluetooth headphones that I am trying to connect are the Sony DR-BT30Q stereo headphones.  I have scanned for the device using "sudo hcitool scan" and it shows up with the model number as well as the MAC address for my device.  I then proceeded to use "sudo hcitool cc --role=m <macaddress> however that proved unsuccessful.  I then loaded "sudo bluetooth-applet" set it all up in the preferences and let it sit in my task bar while I turned on my headphones.  I saw a bubble pop up saying that ubuntu saw it and I proceeded to click and entered in the default pin for my headphones (default is 0000) after that, I thought everything was connected however my audio was still being output through my sound card.

I hope that I have provided enough information to maybe get to the bottom of this issue.  I very much appreciate your time and any and all information regarding this subject would be extremely useful to me.

Thanks a lot,

Cheers!

---

### Post by linuxwizard on 2007-07-11
Not sure if this will help you.

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by shred_thrash on 2007-07-12
Cheers mate,

I'll check it out and let you know what happens.

Thanks a lot!

Take it easy.

---

