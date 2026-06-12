---
title: "PSX to PC converter"
date: 2006-07-07
forum: Hardware &amp; Laptops
---

### Post by zbyte64 on 2006-07-07
Recently I bought a converter at fry's. Its made by some company called vastech and it works perfectly with the vanilla drivers in windows xp (no need to insert a cd or anything). According to: [http://www.qbik.ch/usb/devices/showdev.php?id=3774](http://www.qbik.ch/usb/devices/showdev.php?id=3774) this device should work on linux, but from the digging i've done it seems people have had mixed results. 

Anyevent, when i run jstest i get the following:
```

zbyte@zbyte128:~$ jstest --normal /dev/input/js0
Driver version is 2.1.0.
Joystick (GreenAsia Electronics  4Axes 12Keys GamePad ) has 12 axes (X, X, X, X, X, X, X, X, X, X, X, X)
Segmentation fault

```

The seg fault is rather unsettling... FYI im using DDR mats

When i run stepmania or a calibrator program, it deson't detect any buttons getting hit. Other thing of interest is when i plug two DDR mats into the device, there is still only one joystick device. Also if there are no DDR mats plugged in, i get the exact same results.

Thx in advanced.

---

### Post by cracker on 2006-07-07
Have you tested DDR mats on a windows machine? Often, these types of adapters only support some of the controllers. I have a combination PSX/N64 controller adapter, and it only supports the original grey N64 controllers, not even the official colored ones. Try using the mats under windows, and try using a normal PSX controller under linux, to see if you get different results.

---

### Post by zbyte64 on 2006-07-08
I did mention that it worked perfectly under windows xp, so yes, these DDR mats work on windows, they don't seem to work on linux though. Well, more accurately the vastech converter doesn't work. I've built a parrallel port converter for PSX controllers and the DDR mats work with that, but my other computer doesn't have a parallel port so i need a usb converter. I don't have any normal PSX controllors but the DDR mats i have are two different brands. I do not think however, that using a normal PSX controller will have any effect because the two mats deliver the same performance with the parallel port adapter and with the usb converter on windows. I find it interesting that the default window's drivers work and yet the linux one's don't - so I am not looking at anything exotic.

---

### Post by zbyte64 on 2006-07-09
Just an update, I tried this on my gentoo box which uses kernel 2.6.16 and I have the exact same problem. Normally I would just return the equipment but the fact it runs perfectly using the default window's drivers makes me a little upset.

---

### Post by CronoDekar on 2006-07-09
I don't have one of those so I can't directly help you unfortunately, but I do have to say that if you're considering trying a different one, I have a [RadioShack PSX->USB controller adapter](http://www.radioshack.com/product/index.jsp?productId=2036260&cp=&origkw=playstation+pc&kw=playstation+pc&parentPage=search) and it works great for me in Linux with no driver installation necessary (I do of course note that "for me" may for some reason not work for you.). Though, it only receives input from one controller.

I too don't think the type of controller used should matter if they work just fine under Windows.  This may sound like an odd suggestion... but have you tried unplugging the USB adapter and plugging it back in?  I had a few issues with my adapter, but once I did that everything was working fine and dandy.  May be a longshot, but hey, couldn't hurt.

---

### Post by pamplemousse on 2007-05-22
I also have the Radio Shack PSX-to-USB converter.  I'm using FeistyFawn.  I play StepMania but there's a joystick axes problem.  How do I fix it?

---

### Post by oiler920 on 2007-06-10
I have another problem. I have one of these crappy PSX+N64 adapters, and when I run jstest, or any other program, the thing inputs a million continuous button presses. I have an original grey N64 controller.

---

### Post by Stingray8989 on 2007-06-18
I have the Joystick axes problem too! joy2key has been no use! PLEASE HELP Somebody!

---

### Post by nonlinear on 2007-07-17
> **oiler920 said:**
> I have another problem. I have one of these crappy PSX+N64 adapters, and when I run jstest, or any other program, the thing inputs a million continuous button presses. I have an original grey N64 controller.

i know this sounds like a dumb answer, but try flipping the switch on the side.   it presses 45984375489 ccontinuous buttons if you got it on ps but using n64  :o

---

