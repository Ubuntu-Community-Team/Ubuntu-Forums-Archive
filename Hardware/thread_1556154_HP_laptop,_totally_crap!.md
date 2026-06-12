---
title: "HP laptop, totally crap!"
date: 2010-08-19
forum: Hardware
---

### Post by ~Aquatic on 2010-08-19
If a computer shuts down by itself it's usually because of the heat. Your computer is probably hot because of dust inside the laptop. Before I cleaned my laptop it could reach 127 C when playing a game. ;)

---

### Post by X5-655 on 2010-08-19
That laptop is pretty much the same as my Compaq CQ61..  I bet when it goes to suspend mode it never wakes, and requires pulling the battery and charger to actually correctly turn back on, because it'll never post again otherwise...  All fault of linux not using the powermanagement in the EFI correctly..

either way, mine gets super hot, but only in linux..  for some reason, my cpu usage never goes low, it's always hanging around 20% for me, per core..  Though when i look at processes, it's always the gnome system monitor causing it..  in windows, this laptop is a fairly cool laptop (in temp)..

---

### Post by utnubuuser on 2010-08-19
Yeah, most likely your fan-ducts are clogged.
Also, on my ThinkPad I'm able to manually switch on the fan with > # echo level 2 > /proc/acpi/ibm/fanor something to that effect from a root terminal. I'm only mentioning that because you might want to try to find a way to have the fan running while you're gaming to help keep the CPU cool.

> 
either way, mine gets super hot, but only in linux.. for some reason, my cpu usage never goes low, it's always hanging around 20% for me, per core.. Though when i look at processes, it's always the gnome system monitor causing it.. in windows, this laptop is a fairly cool laptop (in temp)..If your laptop is doing that, there's something wrong.
I came upon a couple threads that talked about a bug in the kernel that's causing CPU usage when idle.  I'm not sure how old that info/intel is though... and I've also read about the system monitor using a lot of resources. My laptop, which is a P4 only uses approx 1.2% CPU when idling on the desktop.

Also, try using powertop instead of top to get a read on what the system is doing. powertop suggests ways of reducing power usage

---

### Post by X5-655 on 2010-08-19
Powertop:  [http://img.photobucket.com/albums/v395/Evilweredragon/usage.jpg](http://img.photobucket.com/albums/v395/Evilweredragon/usage.jpg)

Don't know what it means, but that shows my keyboard and mouse causing the most usage..  ??

Perhaps the OP can use this app too and see if maybe something is just running rough to overheat (along with clogged vents)..

---

