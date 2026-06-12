---
title: "Battery Problem Asus X501A"
date: 2015-03-16
forum: Hardware
---

### Post by soma094 on 2015-03-16
Hi everyone!

Im using Ubuntu 14.04 LTS and i recognised that there is a problem with my battery. My notebook is an Asus X501A.
So it doesnt charge. When it is plugged in it shows that it is being charged but it will remain on a random percentage.
When i plug out it says a random time that i have left which is unrealistic, usually 10 hours, then after 20 minutes it just
blacks out without any warning. When i turn off the notebook and take out the battery and then back it works fine for
a short time.

Any ideas what the problem could be? Is it a sign that my battery is dying or is there a way to fix it?

Im using ubuntu for about a month now and in the beginning it worked  fine.

Thanks :)

---

### Post by topcoder on 2015-03-16
A similar problem affects me as well on an Acer 5755G laptop. My battery works fine in Windows, but not in Ubuntu.

When plugged in, sometimes I have the blinking battery indicator showing that the battery is discharging and is at critical percentage. When I pull the plug, my computer shows my battery is at 3 percent and discharging, then my computer powers off (brown out, not a clean shutdown). However, I am able to subsequently restart my computer and I have almost full battery.

Because the hardware battery low indicator turns on, I suspect that this may have something to do with the ACPI code in the kernel, but I'm not sure. Any help with regards to how I may debug this issue is welcome.

I'm on Ubuntu 14.04.2 LTS.

---

### Post by tgalati4 on 2015-03-16
If you click on the battery icon, you can display the discharge history.  Post a screenshot of it.  It should be a smooth linear line downward.  If it drops steeply, then that could mean you have a weak cell that is causing a sudden voltage drop and that will trigger an emergency shutdown by the BIOS.

Install *acpitool* and post the data as well:

> tgalati4@Mint17 ~ $ acpitool -B
  Battery #1     : present
    Remaining capacity : unknown, 75.91%, 00:00:00
    Design capacity    : 4000 mA
    Last full capacity : 2350 mA, **58.75% of design capacity**
   ** Capacity loss      : 41.25%**
    Present rate       : 1732 mA
    Charging state     : Discharging
    Battery type       : Li-ion 
    Model number       : GARDA71
    Serial number      : 1315


---

### Post by soma094 on 2015-03-17
Here are the acpi data ```
 acpitool -B
  Battery #1     : present
    Remaining capacity : 7414 mWh, 39.39%, 00:32:35
    Design capacity    : 48400 mWh
    Last full capacity : 18821 mWh, 38.89% of design capacity
    Capacity loss      : 61.11%
    Present rate       : 13651 mW
    Charging state     : Discharging
    Battery type       : Li-ion 
    Model number       : X401-44 
```
There is the pic. Where there is a little straight line there was a blackout, and it was when i started a game to make the battery discharge faster.
[ATTACH=CONFIG]260683[/ATTACH]

---

### Post by tgalati4 on 2015-03-17
When a Lithium Ion battery gets below 50% capacity it is considered "shot".  Your battery is less than 40%, so it is more than "shot".

Don't use it on battery for more than a few minutes because it can't generate enough current to keep the voltage up.  If voltage drops too steeply you will get an emergency shutdown and you will lose data and damage your hard disk.

---

### Post by soma094 on 2015-03-18
Thanks :) :/ so i suppose i have to buy a new battery to solve this problem... If it is okay for topcoder then i would like to set this thread as solved.

Thanks for the help. I really appreciate it.

---

### Post by soma094 on 2015-03-18
This is the data from this day. Is it possible to get the capacity back? its almost a 10% better than it was. I know it is still under 50% but still :) . So 

i would like to ask that is it possible? or is it a software problem that it measures it incorrectly?

```
 acpitool -B
  Battery #1     : present
    Remaining capacity : 13222 mWh, 56.09%, 00:26:25
    Design capacity    : 48400 mWh
    Last full capacity : 23573 mWh, 48.70% of design capacity
    Capacity loss      : 51.30%
    Present rate       : 23496 mW
    Charging state     : Charging
    Battery type       : Li-ion 
    Model number       : X401-44

 
```

---

### Post by tgalati4 on 2015-03-19
Yes, you can regain capacity under certain conditions.  Very slow charging and very slow discharging will keep the battery cooler and that will lower the internal resistance and lower the losses associated with internal heating.  But, with a laptop, it's hard to control the discharge current without making the laptop unusable.  

You have a new battery in your future, otherwise you are tethered to the power outlet.

---

### Post by soma094 on 2015-03-19
Thanks once again :) then im buying a new battery :)

---

