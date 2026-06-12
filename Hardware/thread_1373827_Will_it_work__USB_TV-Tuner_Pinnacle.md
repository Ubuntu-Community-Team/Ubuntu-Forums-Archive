---
title: "Will it work ? USB TV-Tuner Pinnacle"
date: 2010-01-06
forum: Hardware
---

### Post by WannabeFantasma on 2010-01-06
Hey all,

I'll be recieving my HTPC parts soon (YAY) and I was thinking of using a USB TV-Tuner for it so I could watch tv on my pc later on. (USB because it's a mini ITX motherboard with a MINI PCI-E slot (Zotac IONITX)

I searched this forum and couple of others, but still not a real answer for the current version.

I found this usb **Pinnacle PCTV Hybrid Stick Solo** and so I wanted to know if it would work.. (and if someone knows how I'm going to get it to work)...

I found this [http://linuxpc.info/node/51](http://linuxpc.info/node/51) but that's for Kubuntu 8.10 so it's kind of "old"...



Greets
Fantasma

---

### Post by theDaveTheRave on 2010-01-06
The chances are it will still work??

However.... it may also break (like the wifi cards often do during upgrades!)

My suggestion would be, if possible. To get a copy of 8.10 get the card working on that, then upgrade to the newer distro, (9.4) and see what happens, and then again upto Karmic.

If you have the card allready, then try it (on karmic) and see what happens.

Otherwise take your laptop (I am asumming it is a laptop) to the store, ad ask if you can test the stck.

Otherwise you may be best to search for a usb TV-stick that does definately work in karmic.

Also check on the MythTV pages, they may have someone with direct experience of the stick / chipset for the item.

David

---

### Post by WannabeFantasma on 2010-01-06
but Kubuntu isn't Ubuntu? or can a Kubuntu program be installed on Ubuntu?(without loosing performance?)

I don't have one yet, but I saw it on a site for Used goods..:lolflag:

It's not a laptop it's a normal desktop pc, but the motherboard only has a mini pci-E slot and it's used by a wireless internet card.... ( [http://www.cartft.com/image_db/Zotac_IONITX_D-E_440.jpg](http://www.cartft.com/image_db/Zotac_IONITX_D-E_440.jpg)) so I need a usb one...

I'll try to find some more info :D (or a different stick)

---

### Post by laceration on 2010-01-06
[http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page)

This is the definitive and most thorough resource, by the people who write the linux tv drivers.

---

### Post by WannabeFantasma on 2010-01-07
looked there couldn't find it

but if a **Pinnacle PCTV Hybrid Pro Stick** works
wouldn't a **Pinnacle PCTV Hybrid  Solo Stick**Work?

Just found a stick that is supported (Pinnacle PCTV USB Stick--Supported Em2880/Em2870 Based USB DVB-T devices --)

---

### Post by laceration on 2010-01-07
It could be the same thing, but you never know.  Get the one that you know is supported.

---

### Post by HappySmack on 2010-01-16
EDIT: I found the link and tried it. It Works !

[http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Pro_Stick_(800e)]("http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Pro_Stick_%28800e%29")

If you have any problems, I am more than happy to help.

This works for 32-bit ONLY (as far as I know).

I need help with getting it to work in 9.10 amd64.

---

### Post by WannabeFantasma on 2010-01-17
nice!

too bad the owner doesn't respond....
(going to buy it as used good, cheaper and stuff.... + i can't find them anywhere else :D )

---

### Post by HappySmack on 2010-01-25
Just a follow-up here. I DID get pinnacle 800e working on my 64 bit machine. For some reason, unknown to me, I had to extract the firmware on my 32 bit box and transfer to 64 bit box. Any attempt to extract on the 64 bit machine did not work. I did get the file, but it would error out stating something about AC'97 audio not starting or something.

---

