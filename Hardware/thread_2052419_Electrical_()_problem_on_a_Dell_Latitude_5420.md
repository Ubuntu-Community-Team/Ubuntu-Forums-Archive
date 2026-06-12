---
title: "Electrical (?) problem on a Dell Latitude 5420"
date: 2012-09-03
forum: Hardware
---

### Post by etienoo on 2012-09-03
Hi,

I have a very annoying problem on my laptop **Dell Latitude 5420**.
It works perfectly fine when the battery is 100% charged (and plugged) or when it is unplugged (thus the battery is discharging).
However, when in charge (and lower than about 90%), the computer almost cannot be used: the mouse moves incredibly slow (similarly for the touchpad). Furthermore, it seems that the hard drive responds very slow: saving a tiny text document (which would usually take a few milliseconds) takes 10-20 seconds.

When I'm at work, the computer is always plugged, and this is not a problem; however, after I use the computer in a train or a plane (hence without power supply), I have to wait one hour before it becomes fully charged to use it &#8722; and this is really annoying.

I installed two systems one after the other
1) Ubuntu 11.10 64 bits
2) XUbuntu 12.04 32 bits

The problem was the same in both cases, from the first installation.

I wonder whether it comes from some incompatibility coming from Ubuntu (although this model has been certified for Ubuntu), or from a hardware problem in the computer.

Thanks for any hints

---

### Post by SlugSlug on 2012-09-03
I'd have a poke round in the BIOS

---

### Post by etienoo on 2012-09-03
What could be the problem?
I mean, what could I investigate in the BIOS?

Thanks!

---

### Post by SlugSlug on 2012-09-03
look into power management see what options are there, maybe disable it ?

---

### Post by etienoo on 2012-09-04
I looked into the BIOS, where there is little option (not even the possibility to disable anything).

However, this BIOS is a modern system where one needs a mouse and, strange enough, the mouse works perfectly well, even if the computer is charging. But booting XUbuntu right after will create the problem with the mouse in XUbuntu.
So this problem might (partially) come from the OS.

Did anyone experience a similar problem?

---

### Post by andriansah on 2012-10-06
Could it be it's battery life problem?
[http://ubuntuforums.org/showthread.php?t=2040722&highlight=5420](http://ubuntuforums.org/showthread.php?t=2040722&highlight=5420)

---

### Post by etienoo on 2012-10-16
I don't think so, because it does so since the first boot of the computer (which was new when I got it), and it doesn't work until the battery is charged 90%.

However, when unplugged, the computer lasts for at least 3 hours (until the battery is almost 0%).

---

### Post by typhoon_tip on 2012-10-16
Can you write here how many watts does your power supply unit have ? It is written on a label in the back of it.

---

### Post by etienoo on 2012-10-24
No, I can't find it.

I read the following:
```
Input :100-240V ~ 1.5 A 50-60 Hz
Output: 19.5V ~ 4.62A
```

But no watts…

---

### Post by typhoon_tip on 2012-10-24
Well enough, just multiply Volts * Amperes, = 90W. It should be enough to recharge your battery while using the laptop at the same time ! Some laptop have this protection, they are not recharging if they detect the power is not enough to recharge and use at the same time, or they scale down the power of the system. In your case, seems a bit on the extreme of the latter.

The 90% "threshold" is because when the battery is below 90% it usually get pumped much current in than otherwise.

Also, can you write down your battery specs ? If you go to the battery menu, click "Battery" then "Laptop battery", tab details will show you the capacity. Post that content as well !

---

### Post by ahallubuntu on 2012-10-25
Could be a bad power adapter.  Dell laptop power adapters are notoriously unreliable and prone to fail in unpredictable ways; I have seen many.  Hope it's the power adapter, as you can buy a generic replacement off eBay for about $8 USD shipped.  If it's a motherboard power problem, you are in for a much more expensive repair, most likely.

Here's why I suspect a bad power supply: when you are charging the battery *AND* using it, you are drawing the most current through the power supply.  (And the battery won't charge unless charge level drops below a certain threshold.)  Dell laptops are designed to charge the battery just as quickly when in use than when powered off (unlike some e.g. some model Toshiba laptops which will charge the battery very slowly when in use but quickly when off).  So charging + using puts the biggest load on the supply.  This also seems to cause weird issues with failing power supplies; sometimes the laptop will complain that it can't recognize the type of charger anymore and just refuse to charge the battery (but will run the laptop).

Your E5420 seems to use a generic Dell PA-12 (65W) or PA-10 (90W) power adapter, if you want to risk $8 and try a new one.  Get the PA-10 to be safe, you can't have too much power, you can only have not enough...

---

### Post by etienoo on 2012-10-25
Actually, the computer can be used (strictly speaking) while charging (and it does charge), but mouse and disk seem to respond extremely slowly, which in practice make the computer unusable.

Spec:
Model: 2VYF519
Technology: Lithium Ion
Full charge energy: 62.2 Wh
Empty battery: 0.0 Wh
Tension: 12.7V
Manufacturer: Sanyo
Serial number: 2767

---

