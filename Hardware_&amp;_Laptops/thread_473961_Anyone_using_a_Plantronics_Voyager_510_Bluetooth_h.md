---
title: "Anyone using a Plantronics Voyager 510 Bluetooth headset?"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by MetalMusicAddict on 2007-06-14
I was looking at getting a [Plantronics Voyager 510 Bluetooth headset]("http://blog.tmcnet.com/blog/tom-keating/gadgets/plantronics-voyager-510usb-bluetooth-headset-review.asp") from [Amazon]("http://www.amazon.com/gp/product/B0009B0IX4%3ftag=techstuff01-20%26link_code=xm2%26camp=2025%26dev-t=151BWK97V0S8BGYJ8F02"). It's exactly what I want but I cant find if it has support.

If anyone knows of another headset that works in linux please let me know. :)

---

### Post by MetalMusicAddict on 2007-06-16
Gonna bump this one. :)

---

### Post by nievo on 2007-07-19
Hello MetalMusicAddict,

I can confirm that the Plantronics Voyager 510 Bluetooth headset works in Ubuntu Feisty, although I haven't really tested that much so am unsure of how well it will work.

So far I have only done the 'Skype Test Call' which worked ok. Sound was a little fuzzy though. Not sure if that's just the headset or the way it's set up.

To get it working all I did was: 
[LIST=1]Plug in the bluetooth dongle
dmesg output the following:
```
[ 2150.796000] usb 1-2.3: new full speed USB device using ehci_hcd and address 17
[ 2151.116000] usb 1-2.3: configuration #1 chosen from 1 choice
[ 2151.128000] 17:1:1 : no or invalid class specific endpoint descriptor
[ 2151.132000] 17:2:1 : no or invalid class specific endpoint descriptor
[ 2152.608000] input: Plantronics Plantronics BT Adapter as /class/input/input10
[ 2152.608000] input,hiddev96: USB HID v1.11 Device [Plantronics Plantronics BT Adapter] on usb-0000:00:02.1-2.3
```
[*]Pair it with the headset by pressing buttons on both devices as indicated in the user manual.
[*]Then select it as the audio device in the Skype options.
[[IMG]http://img375.imageshack.us/img375/2482/skypeplantronicsvoyagerwe5.th.png[/IMG]](http://img375.imageshack.us/my.php?image=skypeplantronicsvoyagerwe5.png)
[/LIST]
Nice and easy :cool:

The version of Skype I'm using is 1.4.0.74 Beta from the Skype site. It's more up to date than the one in the Ubuntu repository's. You can get a .deb [here]("http://www.skype.com/go/getskype-linux-ubuntu")
I will probably give it a test run tonight to see how it holds up in a proper call and report back later with my findings.

Hope this info is helpful in making your decision.

nievo

---

### Post by nievo on 2007-07-19
> **nievo said:**
> So far I have only done the 'Skype Test Call' which worked ok. Sound was a little fuzzy though.

I take back what I said before about the sound quality. I had a conversation for over 40mins and the sound was really clear. Must have been something to do with the test call in skype? It only started to break up after I moved 10-12m away from my computer in the next room.

One small thing to note is that it you have the possibility of receiving it with one of two dongles, one of which (IP15) doesn't work in Vista. This was the model I received, and as I run a dual boot system I sent Plantronics an email about it and they offered to exchange the dongle for a model that did work (IP23). As a result I never got round to testing the original dongle in Ubuntu.

Anyway, I highly recommend it, especially for the price.

---

### Post by MetalMusicAddict on 2007-08-05
Awesome man. Ill remember to look for the IP23 dongle. Thanx a bunch

---

