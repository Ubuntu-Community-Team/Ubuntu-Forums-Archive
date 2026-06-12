---
title: "Ubuntu killed 2 batteries (thinkpad x41t)"
date: 2009-03-10
forum: Hardware
---

### Post by wbonx on 2009-03-10
Hi,
everybody knows that linux have big problems managing power autonomy of laptops.
But what everybody doesn't know is that the modules that have to manage the battery charging program and powersupply are so bad coded that often battery life is reduced consistently after using a linux system (ubuntu) for just 2-3 month.
Personally i burned 1 battery using it just 3 month with ubuntu when under windows it gives about 5 hours of power (now 50 minutes).
Then I bought a new one, changed the modules, used modules built for my thinkpad x41t and the new battery lost 50% of his life in about 2 month.

How is it possible? I lost something like 200euros cause the 2 batteries where original IBM replacement.

Where I have to submit the bug? Is a kernel bug or the problem is that ubuntu is using not well written modules? or what else?

Thank you.

---

### Post by T.R. on 2009-11-25
Linux really isn't bad at handling laptop batteries. It's just a matter of having the right drivers and keeping the battery from getting damaged by heat. The best thing you can do is remove the battery when you aren't running on it or charging it. More info here: [http://www.thinkwiki.org/wiki/Maintenance#Battery_treatment](http://www.thinkwiki.org/wiki/Maintenance#Battery_treatment).

HTH

---

### Post by isbiyanto on 2010-05-17
:(

---

### Post by Tomi Neste on 2010-07-18
No. It really isn't about heat and drivers. There is something very wrong with the way Ubuntu handles laptops. I have also had a few laptops that had got their batteries completely killed after installing Ubuntu.

See [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/481576](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/481576) , essential part is "Apparently, draining a Li-on battery completely kills the battery (mine only has 9.8% of it's original capacity).".

Edit: Mine went from 2.5hr to barely 2min after two hibernations. Luckily my laptop is used constantly from AC anyway. Else I might be a bit angry...

---

### Post by PresenceofMind on 2010-07-18
I too did notice this "sucking of power" from my netbook, it's supposed to have 6-hour battery life....turned out i needed to disable the wireless to get the most out of it.

---

### Post by Tomi Neste on 2010-07-18
> **PresenceofMind said:**
> I too did notice this "sucking of power" from my netbook, it's supposed to have 6-hour battery life....turned out i needed to disable the wireless to get the most out of it.
It is not about how much power it sucks. It's about how much it drains your batteries total capacity.

Edit: it still has status of "Low" on the bugtracker.

Quoting Samuel Kogler:
May I ask why the priority of this bug is LOW? This can damage hardware seriously, and open work is just gone...

---

### Post by PresenceofMind on 2010-07-19
> **Tomi Neste said:**
> It is not about how much power it sucks. It's about how much it drains your batteries total capacity.

Edit: it still has status of "Low" on the bugtracker.

Quoting Samuel Kogler:
May I ask why the priority of this bug is LOW? This can damage hardware seriously, and open work is just gone...

My bad..... either way it still drained my batteries lol

---

### Post by ramujinius on 2010-07-19
Now I am really scared to use Ubuntu :-(... I was happy when i first installed and started using it. Now if it spoils the hardware, then its better for me to use Windows...

---

### Post by PresenceofMind on 2010-07-19
> **ramujinius said:**
> Now I am really scared to use Ubuntu :-(... I was happy when i first installed and started using it. Now if it spoils the hardware, then its better for me to use Windows...

Nooooo!!!!! Please don't lose yourself to windows!!! (That said I do run Windows on my second laptop for the same kinda reasons) I should've said this earlier: the battery life improved after a kernel update :D so all is good now. I get 3-4 hours when using WLAN and 6 hours without using WLAN. It used to be 1 hour with WLAN.

---

### Post by Grenage on 2010-07-19
If the laptop doesn't shut down before the battery is totally drained (I always thought the hardware cut out before that happened), then could well lose some capacity; reconditioning methods may fix it.  I've never seen this happen on any of our laptops, so it must be uncommon at the least.

Could you explain:

> Mine went from 2.5hr to barely 2min after two hibernations

---

### Post by Tomi Neste on 2010-07-19
I had already seen this happen on a few laptops so I was careful not to let the power go too low with my new laptop.

I _once_ let it accidentally hibernate after which the capacity went to 30%. It stood there for a few weeks until the battery was once more _almost_ empty (maybe a minute away from shutdown). After that capacity went down to 9%.

The battery worked fine before under Vista, now it naturally doesn't work there either.

---

### Post by Grenage on 2010-07-19
Ah, I now understand.  I wasn't aware that the penalty for a completely empty battery was anywhere near that harsh.  I've had one battery drain when it was on standby for a month or two, but it didn't affect it's capacity.  It's possible that it didn't drain 'completely'.

---

### Post by libssd on 2010-07-19
> **ramujinius said:**
> Now I am really scared to use Ubuntu :-(... I was happy when i first installed and started using it. Now if it spoils the hardware, then its better for me to use Windows...
It may depend on the laptop and the power manager settings. I have mine set for "When battery power is critically low shutdown". I have a year old Acer D150 with a 2200 mAh 3-cell battery, and a 5200 mAh 6-cell battery. Both are currently rated at about 95% of capacity, and each runs the machine for about the rated time (~2 hours and ~6 hours, respectively).

I think I remember a configurable setting for the "when battery is critically low" threshold in an earlier version of Ubuntu, but as far as I can see, this is not configurable through the gnome power manager GUI with 10.04. However, it **is** configurable using the Gnome Configuration Editor (gconf-editor):

apps => gnome-power-manager => general 
 [INDENT]use_profile_time = TRUE
 use_time_for_policy = FALSE
[/INDENT]

In my opinion, the default values for the first two are absurdly low (2), so I use thresholds that are much more conservative, giving me a low battery warning at 15%, a critical battery warning at 10%, and then shutting automatically down at 7%:

apps => gnome-power-manager => thresholds
 [INDENT]percentage_action = 7
 percentage_critical = 10
 percentage_low = 15[/INDENT]

Use whatever values make you comfortable. You can test these thresholds by setting them artificially high; e.g. 85,90,95

---

### Post by ramujinius on 2010-07-20
Thanks for the suggestion

But is it because if someone hibernates at a very low threshold, the battery capacity will be reduced? Is it common to all OSs?  Is this hibernate issue specific to Ubuntu?

---

### Post by IcarusR on 2010-07-20
Tomi Neste

> my laptop is used constantly from AC

Leaving battery plugged in when constantly powered from AC will decrease it's life.
To maximise battery life charge to 75% remove & store in a cool enviroment & only plug it in when it's going to be used.

---

### Post by libssd on 2010-07-20
I have been told that totally discharging a lithium ion battery shortens its life; getting down to less than 5% strikes me as awfully close to total discharge, which is why I re-set the thresholds to higher levels. Note that even with perfect maintenance, a lithium ion battery is capable of a limited number of charge/discharge cycles. 

Linux, in and of itself, has little to do with battery life, as the battery has no awareness of what OS it is powering. After a year of daily use with various versions of Ubuntu, both  rechargeable batteries for my Acer netbook have about 95% capacity.

Good article on lithium ion batteries:  [http://www.batteryuniversity.com/parttwo-34.htm](http://www.batteryuniversity.com/parttwo-34.htm)

---

