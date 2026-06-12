---
title: "Sick of fan noise?  Here's how I fixed it!"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by kvonb on 2007-10-20
Are you sick to death of fan noise driving you around the bend?

I certainly am, and here is how I solved it:

**WARNING:  Do NOT attempt this unless you are competent with electricity, and understand the dangers.  ALWAYS unplug electrical equipment from the mains, and discharge power supply capacitors before sticking your fingers inside them!  Also don't use hardware that is still under warranty, as it will void it.  Damage MAY result from experimenting, you were warned!**

All I did was swap ALL my fans from 12volts to 5 volts!  Simple as, and they work perfectly :).

My temperatures are all well below maximum levels and actually very close to the original levels.

I can actually hear my hard disk access now :).

I have done this on several machines, and all work properly.

AMD XP2000 - 5v CPU fan, 5v PS fan, 5v GPU fan
P4 1.6 - 5v PS fan, 5v GPU fan
AMD Duron 600 - 5v CPU fan, 5v PS fan
P3 800 - 5v CPU fan, 5v PS fan, 5v GPU fan

I'm also a believer in the "upside down fan" method.  I believe that a big contributor to failed capacitors is the fact that CPU fans blow hot air downward ONTO the mainboard and components, rather than pulling it up and away from the mainboard.

You can change the direction your CPU fan spins by swapping the pulsed power feed lines (inside the fan).  It is quite awkward to do, but I have done it successfully on Intel fans.

But that is another story that really needs pictures :).

Of course if I was rich I could have spent hundreds on water cooling and fancy fans, but why bother?

---

### Post by Toffeeapple on 2007-10-20
[http://www.silentpcreview.com/article6-page1.html](http://www.silentpcreview.com/article6-page1.html)

shows you how...

---

### Post by Mike Chin on 2007-10-20
Funny this link should show up just when I'm starting to experiment with Ubuntu. :)

You can go much farther than just slowing fans to 5V. Choosing the best sounding fans to run them slow, and choosing the best sounding, quiet components, and..... There's 5+ years worth of info on the topic of quieting computers, mostly from a DIY/enthusiast PoV at SPCR. My own machines are inaudible, and they're not the only ones.

---

### Post by kvonb on 2007-10-21
Great links there, thanks people :).

I have mild ringing in my ears, and I swear it's from many years of being bombarded by damned PC noises :(.

It seems to be around the 60hz mark (a G I believe), which is why I blame electronics/computer equipment, and having PC noise seems to make it worse!

---

### Post by aaahotdog on 2007-10-21
A word of caution.   Monitor for overheating cpu.  The 12 supply is designed to run motors only.   The 5 volts is for the logic side of things.   Motors on fans often produce electrical noise which would feed back into your logic circuits (not a good thing).   The other would be how many watts would the fans draw from the 5v power?   Power supplies are designed to hold a constant voltage.   The additional draw might put stress on the power supply.   A better solution would be to put a rheostat inline with the fan connections.   This way you could run the fans off of 12v as they should be and control their speed accordingly.   I also agree with the pull-up method of heatsinks.   I believe Dell has this right by the cooling shroud exhausting the heat out of back of computer.   However, w/o the shroud, up or down doesn't seem to make a difference at least in the cases I have monitored.

---

### Post by drmatty on 2007-10-21
Great links!:)

---

### Post by Mike Chin on 2007-10-21
> **aaahotdog said:**
> A word of caution. Monitor for overheating cpu. The 12 supply is designed to run motors only.   The 5 volts is for the logic side of things.   Motors on fans often produce electrical noise which would feed back into your logic circuits (not a good thing).   The other would be how many watts would the fans draw from the 5v power?   Power supplies are designed to hold a constant voltage.   The additional draw might put stress on the power supply.   
There's a ***lot ***of misinformation here. 
1) *The 12 supply is designed to run motors only.* Just not true. The PSU doesn't "care" what it runs.Besides, almost everything in a modern computer runs off the 12v line. This is why you'll see a 400W PSU with 300W capability on its 12V line alone. 
2) *The 5 volts is for the logic side of things.  * Also not true. It's used a bit in 3.5" HDDs, and some portions of the motherboard.
3)  *The other would be how many watts would the fans draw from the 5v power? Power supplies are designed to hold a constant voltage. * Yes, voltage regulation is designed to be within +,-5% (of the target voltage), which any PSU can do running umpteen numbers of 12VDC fans at 5V. The power draw is extremely small -- in the order of 1-2W, if that. 
(For more complete info on power supplies see [**PSU Fundamental**s]("http://www.silentpcreview.com/article28-page1.html") at SPCR)

In essence, there's no risk of overloading the PSU running 12VDC fans on the 5V lines. 

A rheostat works fine, but the speed range of a fan varies depending on the interaction between specific fan and rheostat. Better yet is a voltage regulator that can provide the same voltage range more precisely to any fan load. A Zalman fanmate is a good example -- 5~11V to any fan when inserted between fan and fan connector -- and it's cheap -- maybe $4-5 these days.

---

