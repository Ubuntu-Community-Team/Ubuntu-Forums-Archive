---
title: "Frequency Scaling on Gateway LT3103u"
date: 2009-08-27
forum: Hardware
---

### Post by gtwy on 2009-08-27
Officially the BIOS/ motherboard/ processor on this laptop does not support automatic throttling of frequency to conserve battery. However I have verified that utilizing Cool & Quiet (PowerNow!) is possible on this CPU using some software tools and can confirm that the AMD processor on this thing does scale to lower frequencies and voltages.

I have successfully undervolted and underclocked the using Rightmark RMClock (windows utility) with P states ranging from [800 MHz @0.67 V] to [1200 MHz @0.7 V] and have noted a very impressive extension in battery life :)

However under Ubuntu I haven't figured out a way to achive the undervolt and underclock leading to painfully short battery life. :(

Finally somone was able to underclock the AMD processor under LINUX to 800 Mhz :P (although not sure @0.67 V): 
[http://forum.notebookreview.com/show...393200&page=22](http://forum.notebookreview.com/show...393200&page=22)

I have the following queries:

1) How can one underclock & undervolt to 800MHz @0.67V under Ubuntu Jaunty? Please explain the steps.

2) Is it possible to re-write and test the AMD processor to go to even lower (unsupported) P states? possibly with a multiplier like 3x @600 Mhz or 2x @400 Mhz or even lower for super awesome battery life? :KS

---

### Post by Yellow Pasque on 2009-08-27
I'm pretty sure you can't use a multiplier lower than 4x for Turion

Anyway, there's a utility that allows finer-grained control of voltages/clocks on K8-based CPU's - cpupowerd. See: [http://ubuntuforums.org/showthread.php?t=852415](http://ubuntuforums.org/showthread.php?t=852415)

---

### Post by gtwy on 2009-08-27
> **Temüjin said:**
> I'm pretty sure you can't use a multiplier lower than 4x for Turion

The AMD processor on this seems to be an Ultra Low Voltage one (cream of the crop) since it works so beautifully at such low voltages, which leads me to believe that it should break no sweat operating at 3x and lower. Unless I have missed something really obvious, can you tell me why can't one use a multiplier lower than 4x?

> **Temüjin said:**
> Anyway, there's a utility that allows finer-grained control of voltages/clocks on K8-based CPU's - cpupowerd. See: [http://ubuntuforums.org/showthread.php?t=852415](http://ubuntuforums.org/showthread.php?t=852415)
Thanks for the link. I will check it out. 

I definitely want to give this AMD processor a chance to go to 3x@600 MHz and lower. :) (fingers crossed)

---

### Post by gtwy on 2009-08-27
> **gtwy said:**
> 

Finally somone was able to underclock the AMD processor under LINUX to 800 Mhz :P (although not sure @0.67 V): 
[http://forum.notebookreview.com/show...393200&page=22](http://forum.notebookreview.com/show...393200&page=22)



Correct link - [http://forum.notebookreview.com/showthread.php?t=393200&page=22](http://forum.notebookreview.com/showthread.php?t=393200&page=22)

---

