---
title: "hpdv6000 battery help."
date: 2008-06-21
forum: Hardware
---

### Post by Llewxam on 2008-06-21
been meaning to ask this for quite some time now. the battery on my laptop barely lasts when unplugged. usually lasts for 2 hours and 10 minutes now it only lasts 1 hour. 
from the device information in the power panel it reads that the capacity for the battery is at 47%(Poor) and the full charge at half of what it should be. 
```
Current charge: 42.1 Wh
Last full charge 46.1 Wh
Design charge: 88.8 Wh
```

i tried using a section in the wiki for longer lasting battery and it had no effect whatsoever. followed everything and it's still the same. anyone could point me out how to fix this? will be appreciated as always.

---

### Post by jo.angel on 2008-06-22
got the Same laptop - same problem

[COLOR="Red"]cat /proc/acpi/battery/BAT0/info[/COLOR]

tells me:

present:                 yes
design capacity:         6000 mAh
last full capacity:      3936 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 202 mAh
design capacity low:     122 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary


So 6000mh is meant to be the max capacity, in fact it has never loaded up to more than 3936 mAH.

Lasts an hour and thaz it...

---

### Post by Llewxam on 2008-06-22
glad i'm not the only one with this problem. anyone out there know if this has any resolution?

---

### Post by Llewxam on 2008-06-23
well i attempted to follow some threads dealing with this same problem and none have helped. battery is still in 49% capacity. this is really bugging and annoying me. anyone please know what exactly i gotta follow here to get this working fine in gutsy?:(:(

---

### Post by Llewxam on 2008-07-12
well... it keeps getting worse and worse. is there any fix for this at all?

---

### Post by sergiom99 on 2008-07-13
HP recommends that you "calibrate" your battery every three other months or so.
You do it by setting "do nothing" for low battery level in your power settings manager (In Kubuntu I do it by clicking the battery icon). So you leave your laptop on until it just shutdown and then when you press the power button nothing happens b/c the battery is drained.
Then you charge your battery with laptop off for 4-6 hours and there you are.

Hope this helps. 
PS: And post back if it worked for you.

---

### Post by evertmantel on 2008-07-13
There are two versions of batteries, the one that comes with the laptop is good for about two hours laptopping; it is possible to buy batteries good for about 3 to 3 1/2 hours; I always assumed that is why the capacity indicator never exceeds 66% or so... And this laptop has never seen anything else but ubuntu. Of course when you have less than one hour left, something else is going on..(battery wear, probably)

Mm, come to think of it: 50% capacity: you got one short circuiting battery cell :-(

---

### Post by Llewxam on 2008-07-14
well i let it die out and took out the shutdown thing in power manager. left it recharging while off. capacity went up to 52%. only provides 2 hours now. just gotta find how to raise that and what's causing it. thanks for the help and any more as always will also be appreciated.

---

### Post by sergiom99 on 2008-07-14
maybe you should ask the vendor and/or call for support.

---

### Post by Llewxam on 2008-07-15
well if my theory is correct keeping this up will keep raising the battery's capacity. having done it again, the complete drain and recharge, it added five more minutes. if i get 5 more after this one i guess i'll keep going on with this. if not then i'll definitely contact my vendor. otherwise, at least i got my desktop, granted i'm using a livecd with it for the moment.

---

### Post by foranjeff on 2008-07-16
I'm using a presario v3000 and have been having the same problem. I switched over from XP to Hardy a week ago and ever since the battery capacity has been around 45%. I'm going to try calibrating it and hoping that will add a few extra seconds but aside from that, I'd say we're going to have to talk to HP. 

It's interesting that we're all experiencing a 50%-ish drop in capacity; there's got to be an explanation somewhere for this.


----
Update:
I've spoken with a HP online tech and they official stance is that they don't support the use of any other OS than what's pre-installed (windows). So, I'm sorry but that boat has sailed.

---

### Post by touchlikefire on 2008-07-28
Just wanted to say that I'm in the same boat with you guys: HP DV6000 bought off ebay from someone who had never used it, only to put on Ubuntu 8.04, walk away for an hour, and have it shut down.

Battery Icon shows an alarm at startup indicating 44% capacity, and ```
cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         6000 mAh
last full capacity:      2688 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 137 mAh
design capacity low:     83 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            LION
OEM info:                Hewlett-Packard

```

Glad to see I'm not the only one, but this is surely disappointing and irritating, especially when my Acer Aspire 5610 with Toshiba battery had a nice 3 hr charge to it.

If anyone comes up with a fix, or any enlightening knowledge, please pass it on.  I know from my Physics classes at the university that fully charging/discharging a battery 3 cycles when it's new increases battery life by about 20%, but since I'm not the original owner, I think the time has passed.

---

### Post by Llewxam on 2008-07-30
well i'm still having issues with it. lasting only 1hr 35 mins. i found this site: 

[http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops#laptop_mode](http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops#laptop_mode)

and been thinking about following that in the hopes that it'll help some.

---

### Post by touchlikefire on 2008-09-04
I've checked out the aforementioned link, and I think it's at least good advice.  Moreover, I did some reading of the HP information on the battery and their document calls it a "SMART Battery."  It is my understanding from the description that this means the battery itself has some fancy way of reporting to the OS it's capacity in real time, dependent on myriad factors including specific laptop model and current current draw. So instead of the OS calculating battery life based on whichever criteria, the battery does it by itself and tells the OS.

With that said, I got a new batter from HP under warranty, and after power cycling it three times Windows Vista shows *about* 2:30 full charge, and linux shows less--whatever that may indicate.

Here's the cat /proc/acpi/battery/BAT0/info
```
present:                 yes
design capacity:         6000 mAh
last full capacity:      4064 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 207 mAh
design capacity low:     125 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            LION
OEM info:                Hewlett-Packard

```

You can compare this with my previous post and see that the new battery does have some improvements, though  (according to linux) it is still not charging to full capacity.

I have concluded, then, that:
a) my previous battery was defunct
b) Windows shows longer battery life than linux with this battery (however, I don't know if there is an *actual* difference in life)
c) This business about my new battery not charging to capacity is unresolved

---

### Post by Llewxam on 2008-09-28
and it keeps getting worse and worse. now i only got 1hr 40 mins of batt life. i've tried everything there is to find and i can't get this higher. even the recal which i ran recently didn't help at all.

---

### Post by jader2toesbumpy on 2008-10-22
I just went of to college, and started using my laptop's battery. I have a hp dv 6646us. Two weeks ago I was getting 2 hours plus (which is horrible to start with). Today I had to leave class early because my battery only lasted 40 mins. This is insane. I will try the recalibration and will post the results here. Hopefully Intrepid Ibex will help this out.

---

### Post by shak541 on 2008-10-22
i have an hp dv6622CA and well.. same thing.. exept mine lasts 2.5ish hours with compiz on and all.. battery shows 67%capacity... it used to show 46ish...mine has also never made it to the fullest no matter what i do. so far im thinking its ubuntu.... :(...

---

