---
title: "How hot is TOO hot for a graphics card?"
date: 2008-12-09
forum: Hardware
---

### Post by x C0MMAND0 x on 2008-12-09
1. Specifically, I have a 128MB NVIDIA GeForce 8400M GS, running on my XPS m1330.  It "idles" around 55 C, but when I play games through emulators, it has gotten up to 79 C, this worried me so I quit playing.  Is that TOO hot?  

2. How much can they handle? 

3. I have the sensor monitor in place so I can see the temperatures, but is there a way to regulate fan control?  

4. On that note, is it bad to run a fan harder than needed?

---

### Post by binbash on 2008-12-09
[https://bugs.launchpad.net/dell/+bug/243637](https://bugs.launchpad.net/dell/+bug/243637)

---

### Post by scorp123 on 2008-12-09
> **x C0MMAND0 x said:**
> it has gotten up to 79 C ... Is that TOO hot?
... is it bad to run a fan harder than needed? Yes and yes. 79° C is definitely too hot. You see: the problem with metal (and that's precisely what the innards of microchips are made of) is that it changes its shape depending on its temperature. If metal gets hot it expands. And given how delicate microhips are (we're talking about fractions of a millimeter: nanometers) even the slightest bit of expanding metal might tear something apart and cause the microchip to be destroyed. Hence there are fans which are supposed to blow out the hot air and cool things down by sucking in colder fresh air. But the problem is that fans are mechanical in nature ... and everything that is mechanical (e.g. it rotates) is subject to tear, friction, heat .... Keeping that fan on high rpm's might cause it to fail. If the fan fails then the chips in the inside are very likely to get too hot very quickly ....

If you really insist on gaming I'd suggest you buy an additional cooling pad, something like this:
[http://www.youtube.com/watch?v=54N7BKAEp10](http://www.youtube.com/watch?v=54N7BKAEp10)

This should help keeping your laptop cool.

---

### Post by scorp123 on 2008-12-09
[http://en.wikipedia.org/wiki/Laptop_cooler](http://en.wikipedia.org/wiki/Laptop_cooler)

---

### Post by sdennie on 2008-12-09
I have the same graphics card in my laptop and those are the same temperatures I get when idle/gaming.  They aren't abnormal numbers and, at that temperature you are still far from the temperature threshold where the card will slow itself down to prevent overheating so, you aren't likely to cause short term damage to the card.  In the long term, constantly running your machine that hot will certainly shorten the lifespan of the machine but, whether it will shorten it to such an extent that you will notice it is hard to say.

---

### Post by MonkeyPaw on 2008-12-09
While that's a bit on the hot side, I wouldn't say that you're in any immediate danger. GPUs have a much higher heat tolerance than CPUs. For example, Intel generally says over 60C is too hot, while nVidia and ATI GPUs can easily hit 90C and beyond. It's not unheard of for GPUs (especially nVidia's) to climb into the 100-110C range and not be damaged (though long-term use at those temps I wouldn't recommend).

That said, since it's a notebook, you might check for a BIOS update. Often OEMs adjust some voltages and fan settings to help with thermals.

---

### Post by scorp123 on 2008-12-10
> **vor said:**
> you aren't likely to cause short term damage to the card.  In the long term, constantly running your machine that hot will certainly shorten the lifespan of the machine but, whether it will shorten it to such an extent that you will notice it is hard to say. Please read the bug report "binbash" posted. There are links to other web sites which suggest that some Dell and HP laptops have highly defective Nvidia GPU chips which _will_ fry if you stress them too much.

Dell's BIOS update in that regard is a joke according to those stories .. it only causes the fan to spin up even more and try harder to keep the laptop cool, thus shortening the battery life and increasing the possibility of mechanical failure.

---

### Post by wfp on 2008-12-10
Well if you can not fry an egg on yet your probably ok. Ok enough of the antics.

---

### Post by Gausian on 2008-12-10
my 8400gs runs at 56-62 degrees in both windows vista and ubuntu.

---

### Post by maddog46113 on 2008-12-10
> **scorp123 said:**
> Yes and yes. 79° C is definitely too hot. You see: the problem with metal (and that's precisely what the innards of microchips are made of) is that it changes its shape depending on its temperature. If metal gets hot it expands. And given how delicate microhips are (we're talking about fractions of a millimeter: nanometers) even the slightest bit of expanding metal might tear something apart and cause the microchip to be destroyed. Hence there are fans which are supposed to blow out the hot air and cool things down by sucking in colder fresh air. But the problem is that fans are mechanical in nature ... and everything that is mechanical (e.g. it rotates) is subject to tear, friction, heat .... Keeping that fan on high rpm's might cause it to fail. If the fan fails then the chips in the inside are very likely to get too hot very quickly ....

If you really insist on gaming I'd suggest you buy an additional cooling pad, something like this:
[http://www.youtube.com/watch?v=54N7BKAEp10](http://www.youtube.com/watch?v=54N7BKAEp10)

This should help keeping your laptop cool.

dont forget about silicon melting :)
[http://www.youtube.com/watch?v=iX3lvOeei94](http://www.youtube.com/watch?v=iX3lvOeei94)

---

### Post by Artemis3 on 2008-12-10
The 8800GT usually hits 90c with its default bios settings, the limit is supposed to be 120c... But using nvclock -f -F auto you can still force it to behave, windows needs rivatuner...

---

### Post by RJARRRPCGP on 2008-12-20
With CPUs, with Intel, it appears 100C is the shutdown point. 

And likely somewhere around 120 C for GPUs.

---

### Post by mrsnacker58 on 2009-02-08
I dont know about your card, but ive had mine at 144 Degrees. It was pretty scary.

---

### Post by Slim Odds on 2009-02-08
> **mrsnacker58 said:**
> I dont know about your card, but ive had mine at 144 Degrees. It was pretty scary.

LOL     degrees F   maybe

---

