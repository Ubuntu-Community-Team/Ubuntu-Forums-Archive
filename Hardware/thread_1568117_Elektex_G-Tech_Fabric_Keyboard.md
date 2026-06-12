---
title: "Elektex G-Tech Fabric Keyboard"
date: 2010-09-04
forum: Hardware
---

### Post by Walgaru on 2010-09-04
Hello all,

I'm wondering if anyone has gotten the Eleksen/Elektex G-Tech fabric keyboard to work on ubuntu, and if so how.

Ubuntu 9.10 on Toshiba Satellite P205-S6267
Using Rocketfish bluetooth dongle
Have bluez-utils, etc installed, have paired other devices successfully

The keyboard seems to pair through the wizard, or through the command-line process, but when I check its status, it doesn't appear to actually be paired. Needless to say typing does not produce result. The thing I've been reading is that there's a problem since it is SPP rather than HID...

Edit: First time in a year and a half of ubuntu use that I've had to post, almost always can use the forum to resolve whatever issue I'm having...

---

### Post by Walgaru on 2010-09-08
Using blueman, I was able to connect the keyboard in serial device mode. The keyboard stays on as if connected, and the connection status display on blueman on my laptop shows good signal strength. Unfortunately, kestrokes don't produce anything still. I'm a little stumped as to where to go from here.

---

### Post by ronsii on 2010-10-17
Hi Walgaru, I found your post while trying to find out how to make this g-tech keyboard work with osx... no luck so far. I did some investigating as to how the device works though it dosen't use the standard matrix type wiring like most keypads use this one only uses four wires to connect to the decoder so my guess is it is a resistance or other type of x/y location encoding pad (ie. touchpad), also I guess that the driver for it probably takes the coordinates given by the pad and converts it to a specific 'key' as evidenced by how you calibrate it and not being able to press more than one key at a time. If I get time to play with it more I will try to intercept the actual bluetooth data to confirm this or reverse the drivers for one of the other phones that are available... but knowing how busy I am that may never happen and this might just get stuffed into a box somewhere ;)

    Take care, RonSII

---

