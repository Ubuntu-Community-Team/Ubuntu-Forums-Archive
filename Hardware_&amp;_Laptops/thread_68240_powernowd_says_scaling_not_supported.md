---
title: "powernowd says scaling not supported"
date: 2005-09-22
forum: Hardware &amp; Laptops
---

### Post by Bender NZ on 2005-09-22
Hi,

I'm trying to use powernowd to reduce my laptop's CPU speed while on batteries as it rips through them very quickly with the CPU and fan running full blast when I'm not doing any heavy work.

When I start powernowd I get:

 * Stopping powernowd:                                                   [ ok ]
 * Starting powernowd...
 * CPU frequency scaling not supported                                   [ ok ]

However my laptop is an Asus A6000 - A6U with an AMD Turion MT-30 processor which I know supports speed stepping as I was doing it under windows.

Would anyone know what module needs to be inserted for this to work or would anyone have any other suggestions?

Thanks.

---

### Post by locutus42 on 2005-09-22
try adding the powernow_k8 module. This works for me running Ubuntu on a Sempron 3000+. If it does work, just add it to the end of the /etc/modules file and it'll be loaded on each boot automatically( from a root window: echo "powernow_k8" >> /etc/modules ).

You should be able to look at the current CPU speed here:
sudo cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq

---

### Post by Bender NZ on 2005-09-22
That worked perfectly, thanks.

Is there any good little gnome applets that can be added to control the speed?

---

### Post by kingsidy on 2005-09-22
yeah, when you right click on the top panel, select "add to panel", a window is going to pop and in the list there is a "frequency scaling monitor" select it. and it will be placed on the panel.

---

### Post by locutus42 on 2005-09-22
[QUOTE=Bender NZ]That worked perfectly, thanks.

Is there any good little gnome applets that can be added to control the speed?[/QUOTE]

Not that I'm aware of since most are just CPU freq monitors and not able to control the speed. But something might be out there. I'm just not aware of it yet.

Glad to hear that worked for you.

---

### Post by kashms on 2005-09-23
[QUOTE=Bender NZ]That worked perfectly, thanks.

Is there any good little gnome applets that can be added to control the speed?[/QUOTE]

There is emifreq, which should be in the repositories.

---

### Post by Bender NZ on 2005-09-23
[QUOTE=kashms]There is emifreq, which should be in the repositories.[/QUOTE]

No worries, managed to play with the settings on powernowd so that I have the CPU running at 800MHz all the time and only bumping up to 1.6GHz if the cpu load exceeds 90% which is working nicely.

Thanks for all the help.

---

### Post by kashms on 2005-09-23
[QUOTE=Bender NZ]No worries, managed to play with the settings on powernowd so that I have the CPU running at 800MHz all the time and only bumping up to 1.6GHz if the cpu load exceeds 90% which is working nicely.

Thanks for all the help.[/QUOTE]

Sounds cool! How did you manage that? What changes did you do?

---

### Post by Bender NZ on 2005-09-23
[QUOTE=kashms]Sounds cool! How did you manage that? What changes did you do?[/QUOTE]

Create /etc/default/powernowd

Put in it:

```
OPTIONS="-q -m 2 -u 90"
```

q = quiet
The 90 designates 90 as the 'cpu maxed out' level, so at 90% it bumps the cpu up to full power, and immediately reduces the cpu speed once the usage falls again.

Not sure how well it works with other CPU's - I'm using an AMD Turion.

---

### Post by Hairy_Palms on 2005-09-23
anyone know how to do these kind of things on a p4 with speedstep?

---

### Post by Bender NZ on 2005-09-23
[QUOTE=Hairy_Palms]anyone know how to do these kind of things on a p4 with speedstep?[/QUOTE]

Apparently powernowd can do it with most speed stepping CPU's - can't hurt to try, the program is only a few KB.

---

### Post by bealud on 2005-09-29
Hi.
I have the same problem as Bender on my laptop (based on turion MT32).
I don't know how adding the powernow_k8 module ? How can I do that ?

I have an other problem, but I don't know if it's bound:
The CPU load is up to 50% when I do nothing with my laptop.

---

