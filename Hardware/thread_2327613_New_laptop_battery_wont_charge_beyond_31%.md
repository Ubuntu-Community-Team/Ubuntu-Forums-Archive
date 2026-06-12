---
title: "New laptop battery wont charge beyond 31%"
date: 2016-06-12
forum: Hardware
---

### Post by oisin_nz on 2016-06-12
Hi, 

I have Ubuntu 14.04 installed on a Dell Latitude E6410. I have found that when on AC power the battery will charge to only 31% and then it stops, the battery icon at the top of the screen lists the battery state as 'charging' but it never gets past 31% no matter how long I leave it plugged in. If I unplug the AC power the battery will start to discharge as normal and when it gets critical I can plug back in the AC power and the battery starts to charge but again it stops once it reaches ~31%. See the screen captures below:
[ATTACH=CONFIG]269550[/ATTACH][ATTACH=CONFIG]269551[/ATTACH]
In the first few calls to acpi the laptop is on external power the battery is only 31% charged and it lists a ridiculous 2500+ hours 'until charged'. I then plug out the AC power and dont plug it back in until the battery has fallen to 15%, it then starts to charge normally, but notice that the closer it gets to 31% the longer hours 'until charged' value becomes. The battery GUI output confirms this, it plots the rate at which the battery is charging and you can see that this is steadily falling as the charge approaches 31%. The rate then abruptly falls to zero and the time 'until charged' jumps back to 2500+ hours. So does anyone know what is going on here or how to fix it ? 
The charger is clearly working as it can charge it from 0 to 31%, but at that point the charging current is clearly being cut off, what could cause this? Are there any other tests I could perform to diagnose the problem ? The machine still has a Windows 7 machine if there are any utilities there that might be of use ?
The value of 31% also seems significant, suspiciously close to 33%, might the battery be composed of 3 cells internally and only one of them is charging ? The battery itself is 'new', I got it about a month ago and I think this is a new development (ie I suspect is was charging to full capacity initially) but it is hard to be sure as I mostly use it on AC power. The battery details look perfectly normal in Ubuntu and in the Dell BIOS:
[ATTACH=CONFIG]269552[/ATTACH] 
Any suggestions ? 

Thanks, 

Usjes.

---

