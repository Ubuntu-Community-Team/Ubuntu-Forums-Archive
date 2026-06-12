---
title: "Dell Studio XPS 13 Overheats and Shuts Down"
date: 2010-01-10
forum: Hardware
---

### Post by lawenlerk on 2010-01-10
Hi Im running ubuntu 9.10 64bit on a Dell Studio XPS 1340.

This laptop runs quite hot on both Windows 7 and Ubuntu.



**A) On Windows 7, it allows the computer to run up to a temperature of 70 celsius without shutting down.**

However, when i am in ubuntu, it shuts down at around 50-55 degrees celsius.

There are no settings in the bios that allows me to change temperature related stuff.
[I]
Does anyone know how to prevent ubuntu from shutting down until at least 65 celsius (or any other temperature)?[/I]



**B) Also, there is another situation. **

If i start the computer from a cool state (35c) and run it until 45c, the cpu scales to 1.60GHZ from 2.1GHZ and increasing the frequency from the cpu freq scaling applet doesnt work. 

If i change the governor from ondemand to performance, it shows that im in performance mode but the computer runs at 1.6GHZ (at least thats what i observed relatively)

but then, if i restart ubuntu when im at 45c, ubuntu comes back on with proper cpu scaling that really is "ondemand". It runs significantly faster before the restart.

*Anyone can explain this weird behaviour?*


Thank you.

---

### Post by bcbc on 2010-01-10
Try this:
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#CPU_and_motherboard](http://ubuntuguide.org/wiki/Ubuntu:Karmic#CPU_and_motherboard)

---

### Post by lawenlerk on 2010-01-10
thanks, i'll try this in a while.

btw, will this solve the auto shut down at 50+ celsius too?

---

### Post by Alex!!!! on 2010-01-10
One question: why the hell did you put a 64-bit OS?!

---

### Post by lawenlerk on 2010-01-10
> **Alex!!!! said:**
> One question: why the hell did you put a 64-bit OS?!

erm. because 64 bit support is now better and it provides benefits? so they tell me.

will 32 bit be better on this laptop?

---

### Post by Alex!!!! on 2010-01-10
32-bit doesn't ask the system to do as much as 64-bit. From my best knowledge. I have a 32 on a Dell 500 and it's sweet!

---

### Post by lawenlerk on 2010-01-10
> **Alex!!!! said:**
> 32-bit doesn't ask the system to do as much as 64-bit. From my best knowledge. I have a 32 on a Dell 500 and it's sweet!

okay, i'll try. i have a ubuntu 9.04 dell image. any idea whether it might improve the situation?

---

### Post by lawenlerk on 2010-01-12
I called dell and they sent someone over to replace the fan.

Didn't expect that to solve the problem but it did.

Now it still runs slightly hotter but it doesnt auto shut down anymore. weird.

Thanks anyway.

---

