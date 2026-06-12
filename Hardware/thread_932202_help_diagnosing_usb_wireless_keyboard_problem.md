---
title: "help diagnosing usb wireless keyboard problem"
date: 2008-09-28
forum: Hardware
---

### Post by tobycatlin on 2008-09-28
Hello everybody,
i have a small wireless keyboard for the media centre i have setup. a BTC 9116URF [http://www.amazon.co.uk/Wireless-Black-Keyboard-BuiltIn-Joystick/dp/B000MCUVMI/ref=sr_1_1?ie=UTF8&s=electronics&qid=1222597216&sr=8-1](http://www.amazon.co.uk/Wireless-Black-Keyboard-BuiltIn-Joystick/dp/B000MCUVMI/ref=sr_1_1?ie=UTF8&s=electronics&qid=1222597216&sr=8-1). I bought it because it had a good set of reviews saying the range was good for 10 m. Seeing as my sofa is 2m from the tv this should be plenty. it certainly doesn't have a 10m range but it worked ok.

I was also having problems with a nova-t 500 tv tuner so updated the drivers which fixed the tv card but now the range of my keyboard is about 20 cm from the receiver and even then misses letters. I have changed the batteries to some fresh 2700 mah ones so it should have plenty of juice. It could be a hardware problem but would be a big coincidence if it was. The main reason i think it is a usb issue as the tv card is essentially two usb tuners with a hub on a card, so they come up on lsusb as follows:
```
Bus 007 Device 009: ID 0781:a7a8 SanDisk Corp. 
Bus 007 Device 001: ID 0000:0000  
**Bus 008 Device 002: ID 2040:9950 Hauppauge **
Bus 008 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
**Bus 002 Device 003: ID 046e:5251 Behavior Tech. Computer Corp. **
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 001 Device 001: ID 0000:0000  
```

is it possible that a usb/driver issue can reduce the range of the keyboard but not stop it working totally?

also when i looked at my logs it was filled with the following:
```
Sep 28 11:13:21 media-box kernel: [568784.274677] evbug.c: Event. Dev: usb-0000:00:1d.1-1/input0, Type: 1, Code: 15, Value: 0
Sep 28 11:13:21 media-box kernel: [568784.274680] evbug.c: Event. Dev: usb-0000:00:1d.1-1/input0, Type: 0, Code: 0, Value: 0
Sep 28 11:13:21 media-box kernel: [568784.295684] evbug.c: Event. Dev: isa0061/input0, Type: 18, Code: 2, Value: 0
Sep 28 11:13:21 media-box kernel: [568784.295696] evbug.c: Event. Dev: isa0061/input0, Type: 18, Code: 1, Value: 0
Sep 28 11:13:22 media-box kernel: [568785.256979] evbug.c: Event. Dev: usb-0000:00:1d.1-1/input0, Type: 4, Code: 4, Value: 458792
Sep 28 11:13:22 media-box kernel: [568785.256992] evbug.c: Event. Dev: usb-0000:00:1d.1-1/input0, Type: 1, Code: 28, Value: 1
Sep 28 11:13:22 media-box kernel: [568785.256997] evbug.c: Event. Dev: usb-0000:00:1d.1-1/input0, Type: 0, Code: 0, Value: 0

```

several of these messages are generated every time i hit a key or move the mouse.
Also about 50% of the time when i reboot the mouse will only move and down and moves to the right when i press the mouse button. Othrs have had the same problem but none of the solutions have worked for me.

Any help working out what is happening would be great and a solution even better.

thank you 

toby

---

