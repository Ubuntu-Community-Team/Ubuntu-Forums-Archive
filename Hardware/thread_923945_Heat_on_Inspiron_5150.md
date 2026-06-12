---
title: "Heat on Inspiron 5150"
date: 2008-09-18
forum: Hardware
---

### Post by tcoffeep on 2008-09-18
Hello. I've a simple question.
Currently, I'm running Ubuntu 8.04 on an Inspiron 5150, and so far, it's not running too bad. There are occasional freeze times. But, this is going off-topic.
I'm simply wondering what internal temp is normal?

Currently, I'm averaging out at 55-59 C.

When should I begin to worry?

---

### Post by Sef on 2008-09-19
>  Currently, I'm averaging out at 55-59 C.

That sounds ok.  My desktop runs around 52 C.

---

### Post by tcoffeep on 2008-09-20
> **Sef said:**
> That sounds ok.  My desktop runs around 52 C.

I always thought desktop systems were more forgiving given the space generally in between, whereas a laptop is all put together closely, and a simple overheating can damage multiple things in one blow.
I'm in the process of gathering the funds needed to replace the heatsync and thermal (?:gel|glue), as from reading over a few things, at the time of release for the specific model in question (Dell Inspiron 5150) the heatsync and thermal (?:gel|glue) was recalled.
It seems to run smoothly in Windows (generally maintains a 40-50C during system-intensive programs) whereas Ubuntu can reach 70C during a system-intensive program.

---

### Post by nanotube on 2008-09-22
hey
i've got a 5150 too, running feisty for now
on idle, it is basically at about 50 c, because that's when it's set to turn on/off the cpu fan. if i manually turn on the fan and keep it from turning off, then at idle it will go down to about 35C.

at continuous full processing load, it can go up to 69-70 C

the trick with the 5150 is that you gotta blow out the heatsink with some compressed air a couple times a year (maybe more, depending on how dusty your environment is). their heatsink has the fins pretty close together, and they tend to trap dust and clog up. so turn on the fan full blast, and put your hand behind the fan exhaust, and feel the air flow. if it's not really blowing, then your heatsink is clogged and needs a cleaning.

now, a question for you, somewhat off-topic, but: what video card do you have on your 5150? i've got the "ati mobility radeon 9000", and when i try to boot hardy livecd on it, it fails to start - only works from "safe graphics mode" (using the vesa driver). so, if you have the same video card, tell me how it works once you install, can you get it to run with the ati driver, or do you have to use the vesa driver?

---

### Post by tcoffeep on 2008-09-29
I have a Nvidia driver ... -is confused-

Did they release the specific model with different internals?

Also, to keep this semi-ot, my system seems to freeze out (lol irony) when heat hits about >70C.

---

### Post by nanotube on 2008-10-01
> **tcoffeep said:**
> I have a Nvidia driver ... -is confused-

Did they release the specific model with different internals?


choice of video card an option at time of order.

> 
Also, to keep this semi-ot, my system seems to freeze out (lol irony) when heat hits about >70C.

definitely needs a blow-out of the heatsink, then. :)

---

### Post by tcoffeep on 2008-10-22
> **nanotube said:**
> choice of video card an option at time of order.



definitely needs a blow-out of the heatsink, then. :)

I won't need any thermal gel, though, for a simple blow-out will I? Everything I look at needs canned air/thermal gel. I can't find these around town.

---

### Post by nanotube on 2008-10-22
> **tcoffeep said:**
> I won't need any thermal gel, though, for a simple blow-out will I? Everything I look at needs canned air/thermal gel. I can't find these around town.

hi
no, you only need thermal gel if you take off the heatsink. but you don't need to do that to blow it out. all you need is a can of air. 

bend back the monitor all the way, and take off the plastic strip at the top of the keyboard (the one with the power button), starting from the right (you'll see a slot on the right where you can pry it with the screwdriver, and then carefully lift, it will snap out gradually).

then, unscrew four screws holding the keyboard, at the top of the keyboard, and carefully tilt the kb forward, and lay it upside down on the palmrest.

then, unscrew one screw (close to the middle) that holds down a metal shielding plate, and lift it out. 

once you are there, you can see the fan from the top, and the heatsink is at the back of that. stick in the compressed air nozzle, and blow things out of the heatsink toward the back. (it's best to do it during the day, so you can hold it up to the light and see if it's clear between the heatsink fins).

then, put it all back together in reverse order. :)

and here's a dell service manual, which has helpful pictures:
[http://support.dell.com/support/edocs/systems/ins5100/en/sm/index.htm](http://support.dell.com/support/edocs/systems/ins5100/en/sm/index.htm)

---

