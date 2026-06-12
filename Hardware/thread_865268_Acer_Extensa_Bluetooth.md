---
title: "Acer Extensa Bluetooth"
date: 2008-07-20
forum: Hardware
---

### Post by SuperMike on 2008-07-20
I have a brand new Acer Extensa 4420 laptop and the latest Ubuntu 8.04. I noticed that the Bluetooth light does not turn on by default, and if I choose this key on the front of the laptop to flip it on, it does nothing but put this entry into /var/log/messages:

Use 'setkeycodes e054 <keycode>' to make it known.

I made certain I had installed the bluez-utils, bluez-audio, and bluetooth drivers with apt-get, and I also went into preferences to ensure that bluetooth services were started there under the Bluetooth control panel. I also went to /etc/init.d and bounced the bluetooth service.

I want to mate my Motorola earpiece with the bluetooth system but it can't find it. I also tried to see if I could do some Blackberry mating with it and it also couldn't find it.

---

### Post by dlstyley on 2008-09-20
Does your specific model have a Bluetooth card installed?  Apparently all Extensa 4420's have a switch to turn Bluetooth on/off, but not all of them have a Bluetooth card installed.

For example, I have the 4420-5963, which does not have a Bluetooth card in it.  So I have a completely useless switch and a light for my non-existant bluetooth.  

If you do fall into this category, I believe you can purchase Bluetooth cards and install them yourself... haven't looked into it though.

---

