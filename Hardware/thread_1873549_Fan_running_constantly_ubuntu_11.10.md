---
title: "Fan running constantly ubuntu 11.10"
date: 2011-11-01
forum: Hardware
---

### Post by oliver6899 on 2011-11-01
Hi,

I recently installed ubuntu because my fans were driving me mad while using windows. I have a new dell m310z inspiron laptop (theres no dust on the fans) and on windows the fan comes on every minute or so and is very loud. I haven't been able to fix this so I've installed ubuntu. However, now the fan runs all the time and is loud.

I've looked about and tried installing lm-sensors but this will not work. For some reason it says that the file cannot be retrieved.

Could someone please give me a very straightforward guide to controlling fan speed/temperature etc.


any help is much appreciated, thanks!

---

### Post by 2F4U on 2011-11-01
If you have the same problem in Windows, which certainly has proprietary drivers from the manufacturer, I doubt that you will get rid of the problem in Linux. If you have an ATI or nVidia graphics card, you could try the proprietary graphics drivers and see if it gets better. They are know for better power management than the default open source drivers.

---

### Post by oliver6899 on 2011-11-01
hmm, i've really tried everything else. dell even replaced the motherboard and fans. From what i've monitored in windows all i need to do is set the temperature at which the fans come on a few degrees higher and fan noise should be greatly reduced. at the moment the laptop is normaly around 52 degrees when is hits 53 the fan comes on higher. thats in windows.
linux is worse cause the fan just runs constantly at a high level.

---

### Post by heiko81 on 2011-12-05
If you use Ati opensource driver, not the fglrx driver, then you can see here..there's a workaround to slow down the fan..I havent' tried it, but I'm surely gonna try it soon because my laptop becomes very hot and the fan is always on and loud..

[http://javacolors.blogspot.com/2011/10/ubuntu-1110-ati-radeon-deal.html](http://javacolors.blogspot.com/2011/10/ubuntu-1110-ati-radeon-deal.html)

---

### Post by Mark Phelps on 2011-12-06
Ordinarily, I strongly advise AGAINST slowing down fans -- because they are running fast for a reason -- to try to cool down an overheated CPU.  Simply slowing down the fan is a surefire way to then burn out the CPU.

But in this case ... the link is NOT about slowing down the fan; instead, it is about the more sensible option of underclocking the CPU.  Since slowing down the CPU will cause it to run cooler, that will have the side-effect of slowing down the fan.

This is the RIGHT way to address noisy CPU fans in laptops.

---

