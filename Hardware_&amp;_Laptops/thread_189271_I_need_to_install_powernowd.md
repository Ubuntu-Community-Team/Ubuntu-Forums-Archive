---
title: "I need to install powernowd"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by frank_y on 2006-06-05
I have a dual boot toshiba laptop with windows/dapper, and I've noticed that the battery life for windows is about 3 times as long as it is for ubuntu, and the laptop doesn't get as hot either. That's probably because of all the toshiba power management software that comes with the laptop.

I don't think powernowd or any form of it is running on ubuntu and I'd like to get it to work, but apparently I need to install the cpufreq module, and I'm not sure how.

Any help would be appreciated.

---

### Post by nanotube on 2006-06-05
[QUOTE=frank_y]I have a dual boot toshiba laptop with windows/dapper, and I've noticed that the battery life for windows is about 3 times as long as it is for ubuntu, and the laptop doesn't get as hot either. That's probably because of all the toshiba power management software that comes with the laptop.

I don't think powernowd or any form of it is running on ubuntu and I'd like to get it to work, but apparently I need to install the cpufreq module, and I'm not sure how.

Any help would be appreciated.[/QUOTE]
cpufreq should be installed by default. to see if it's there, run command "modprobe -l cpu*" and see if cpufreq stuff comes up. if it does, cpufreq is already there for you.

so then all you need to do is "sudo aptitude install powernowd"

---

### Post by frank_y on 2006-06-05
Okay, but the laptop still gets very hot and it freezes a lot. Just half an hour ago I had to use fsck because the laptop crashed and I had to cut the power and reboot. Every time I use ubuntu on the laptop for more than an hour or so it starts slowing down and eventually it freezes. Is there any sort of other utility out there to really tune down the performance to keep it cool?

---

### Post by nanotube on 2006-06-05
[QUOTE=frank_y]Okay, but the laptop still gets very hot and it freezes a lot. Just half an hour ago I had to use fsck because the laptop crashed and I had to cut the power and reboot. Every time I use ubuntu on the laptop for more than an hour or so it starts slowing down and eventually it freezes. Is there any sort of other utility out there to really tune down the performance to keep it cool?[/QUOTE]
what kind of laptop is it? if it's a dell, you could install i8kutils, and have it control the fans and stuff. there must be similar stuff for other makes of laptop...

---

### Post by Johnsie on 2006-06-05
I have exactly the same problem on my HP Pavilion ZE4404ea.


Hard drive light looks buys and computer eventually hangs.... Myfan is always on too :-/

I think a few people might be having these peroblems with Dapper. Mine worked ok with Breezy but obviosuly I'd like to keep up to date.

---

### Post by frank_y on 2006-06-05
Ack... I removed and reinstalled powernowd and ...
---------------
Unpacking powernowd (from .../powernowd_0.97-1ubuntu1_i386.deb) ...
Setting up powernowd (0.97-1ubuntu1) ...
 * Starting powernowd...  * CPU frequency scaling not supported                                                                       [ ok ]
-----------------
But I'm sure frequency scaling is supported because the laptop came with this disc of toshiba power saving software for windows and it works while I'm running windows. I really want to use Ubuntu because i've been using for the past year or so, but I don't want to have my laptop hang again ... 

I tried seeing if the bios would let me lower the clock speed but there's no option for that in the setup.

So now I'm thinking the only way to go is to somehow get powernowd to work.

Any ideas? Because I have no idea what to do.

edit: The processor is a Celeron M if that helps.

---

