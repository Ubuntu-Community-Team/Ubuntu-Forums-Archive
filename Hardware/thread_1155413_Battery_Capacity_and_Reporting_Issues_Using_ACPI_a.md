---
title: "Battery Capacity and Reporting Issues Using ACPI and Gnome Power Manager"
date: 2009-05-10
forum: Hardware
---

### Post by Shekibobo on 2009-05-10
Actual battery capacity vs. design capacity: can it be reported correctly using acpi or Gnome Power Manager?  Or is there another way?

I have a few questions and a kind of survey regarding battery management and information reporting using Gnome Power Manager and acpi.  If there are better applications for this, I'm definitely interested in trying them out.  I got a new battery after receiving warnings from Ubuntu, and was concerned with what it was telling me about my new battery.  Here goes:

After installing and starting Ubuntu 9.04 on my HP dv9535nr, Jaunty gave a warning that my battery capacity was less than 40%.  Since I first received this warning I have gotten a replacement battery and a bit more Linux know-how.  The new battery under Gnome Power Manager shows that a full charge will only reach 65% capacity, but I'm not entirely sure it means the battery is defective or failing.  When I run acpi -V, I get the following:

```
josh@ubuntu:~$ acpi -V
     Battery 0: Charging, 12%, rate information unavailable
     **Battery 0: design capacity 6000 mAh, last full capacity 3936 mAh = 65%**
  AC Adapter 0: on-line
     Cooling 0: LCD 0 of 10
     Cooling 1: Processor 0 of 10
     Cooling 2: Processor 0 of 10
```However, my battery, according to the information shipped with it, is **only rated for 4400mAh.  While both acpi and Gnome Power Manager are reporting a battery with 65% capacity**, I'm actually running a battery with about 90% capacity.  

[B]First question:  Should I be worried that a brand new battery is only charging to 90% capacity?

Second question: Is there a way I can recalibrate the battery to show it's actual (according to the advertised statistics) capacity, rather than the acpi/GPM measured design capacity?

Third question: Is there a way to charge the battery to its full design capacity as rated by acpi/GPM?[/B]  

Furthermore, I'm wondering what sort of charge/discharge times people are getting from their batteries based on mAh capacity (advertised stats and acpi/GPM reported) while using Ubuntu.  

On my battery, which charges to 3936mAh after 1:20 hrs, the discharge while running music with visualizations (Rythmbox) is approximately 1:20 hrs, though GPM estimated 1:40 hrs.  My computer is an HP dv9535nr with Ubuntu 9.04 running on a Wubi install in Vista.

It seems to me that my computer should be lasting quite a bit longer on a six cell Li-ion battery, but maybe I'm mistaken. Thanks everyone.  This is my first post, but I've learned tons from this community so far.

Also, on a side note, why might thermal information not get posted in acpi?

---

### Post by Adremelech on 2009-05-17
1) Generally most companies will consider anything > 80% to be a good  battery. You will need to charge/discharge it a few times to get the maximum capacity.

2) Not that im aware of. I had this problem with all the laptop's i've owned so far.

3) I'm sure that it is getting fully charged, acpi just isnt reporting it right.

The run time you get will vary depending on what you are using. I have a Compaq F756NR and i get about 1.5-2 hours just doing "normal" stuff. Also, the number of cells can be misleading, since there is no correlation between the number of cells and the milliamps, they can make a lithium-ion cell with as few or as many milliamps as they desire (technical limitations taken into consideration).

---

### Post by Zwack on 2009-06-20
My 4400mAh battery is also being reported as a 6000mAh battery.  Thus acpi is incorrect about it's status.  (it's reporting it as 49% rather than 75%.

Z.

---

### Post by jalt0n on 2009-07-01
You may have a bad battery.
 
I have two batteries: one new 4400 mAh and one old 4300 mAh.
 
Under Ubuntu 9.04, both show a design capacity of over 6000 mAh.
 
ACPI -V shows the new battery capacity at 95% when fully charged, with full capacity at just under designed capacity (both over 6000 mAh). This battery lasts around 5 hours.
 
ACPI - V shows the old battery capacity at 26% when fully charged, with the full capacity way under designed capacity (something like 1600 vs. 6000). This battery lasts close to 1.5 hours.
 
From this it would seem that while the actual values of mAh are not correct, the relative values (full vs. designed) are reasonably accurate. If ACPI -V shows 65% measured capacity, it is likely correct.

---

### Post by PatrickVogeli on 2009-07-01
so, you probably have a broken bios or dsdt table. And being ah HP, it isn't so strange.

I have a fujitsu siemens esprimo and the values I get are Ok.

---

