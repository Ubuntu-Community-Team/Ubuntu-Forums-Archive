---
title: "Making everything work in brazilian CCE Laptop (NCL-C2H4) - Everything Works (almost)"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by daigorobr on 2007-03-26
Okay, this is a post on how to make Wireless and Audio work completely in a budget brazilian laptop, CCE branded.
I just had to post it here because it is indexed on Google and it will hopefully help someone that's trying to migrate from the awful Linux flavour it comes preinstalled with (Insigne Momentum) to Ubuntu.
I use Feisty Fawn.

Wireless:
1. [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73)
2. sudo apt-get install wlassistant
3. sudo wlassistant

Audio:
1. Add "options snd-hda-intel model=laptop-eapd" to the end of "/etc/modprobe.d/alsa-base"
2. Control the headphone volume with the "Front" control and internal speakers with "Surround" control.

The rest worked out of the box in Linux for me. Even Beryl works great with the Intel graphics chipset!

Edit: the only glitch so far is this issue with the mixers.
Edit 2: I just found out that the laptop-eapd mode works in the alsa drivers that come with Feisty.
Edit 3: The "OZ128" Card Reader won't read any other media than SD or MMC (it should read xD and MS). And there's no sign of anything about it and linux throughout internet.
Edit 4: Apparently, this laptop is derived from some obscure model from Uniwill called L41iix.

---

### Post by rfariasbsb on 2007-08-04
There is a problem with resolution I found out that you need to install 915resolution package to make 1280x800 resolution(dont forget to follow the package instruction)

---

### Post by daigorobr on 2007-11-21
Well, it's almost perfect now.

With Gutsy (Ubuntu 7.10), resolution works out of the box, wifi works out of the box (tho I still go for ndiswrapper for stability), sound works 100% (installing "linux-restricted-modules" and adding "options snd-hda-intel model=acer-aspire" to "/etc/modprobe.d/alsa-base").
The only two things that are still left out are the card reader (only reads MMC/SD - but the nice people of tifm project are working in the MS driver) and the modem (never have to use it, so I never really tried to make it work).

---

