---
title: "Underclocking nvidia on Lenovo G550?"
date: 2009-12-30
forum: Hardware
---

### Post by Tmi on 2009-12-30
Hi.

I recently bought a Lenovo G550 laptop, and to my large disappointment this model has a fan problem where the bios controlled fan only has two possible speeds, fully on or off. The fan is triggered when the GPU temperature reaches 46 degrees celsius, and then as mentioned goes on at full speed. The crappy thing is that the fan will stop immediately when the temperature sensors report it being less than 46 degrees. Since the idle temperature of the GPU is slightly above 46 degrees this then results in an irritating "on/off regulation" where the fan will go to max for a second every ten seconds or so. As you probably understand this is very irritating when you sit and read or work in a quiet environment.

Lenovo has acknowledged the problem, but I'm not very hopefull to see a bios update in the immediate future.

So what I was thinking was to look at the Nvidia settings and try to minimize heat generation as much as possible. I have the latest drivers from the nvidia ppa and the automatic scaling works well. The lowest setting the card goes to automatically is 169-100 (MHz) (NV Clock - Memory clock).

What I'm wondering now is if it is possible to go even further below those values in order to lower the temperature?

I've enabled coolbits in order to access the overclocking tab in nvidia settings, but the problem is that when I slide the bars down to decrease the frequencies the settings just "jump back" when I hit the apply button. Does this mean that there are no possible lower settings I can use? Or is PowerMiser (the automatic scaling) interfering?

Any tips would be appreciated. Apart from the irritation factor I'm worried that this behaviour will wear my fan motor down and thus reduce the lifetime of the laptop.

---

