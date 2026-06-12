---
title: "[SOLVED] Jerky  Compiz Effects and High resting CPU rate"
date: 2008-09-19
forum: General Help
---

### Post by Seaicmac on 2008-09-19
Hey, I'm mega-noobular, but would really appreciate your help.

One of the things that drew me to Ubuntu was those nifty desktop effects from Compiz-Fusion, alas, they don't seem to be functioning anywhere near as smoothly as they ought to on my machine. Moving the windows is jerky with wobbly windows, and the minimizing, exiting and maximising animations are plagued by frameskipping, cutting and general jerkiness.

I'm running Hardy 8.04 on a Dell Inspiron 1520 (Laptop)  cpu:                                                            
              Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz, 2000 MHz
              Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz, 2000 MHz

graphics card:                       Dell GeForce 8600M GT

I installed EnvyNG for my Nvidia Driver as I read to do elsewhere.


Another perhaps related problem that I noticed is that my CPUs seem to be working excessively hard without any load on them. At rest, the CPUs average 20-25% EACH. This is also ballsuckular, as the efficiency of the OS was the other reason I turned to Linux.

I'm hangin in by hook or by crook with Linux, so I'd really be grateful if you could suggest ways to speed up my machine. Thanks again! Jack.**[B]**[/B]

---

### Post by prestomation on 2008-09-20
I have almost the same system.

Install fusion-icon, in the right click menu for fusion icon, enable both options under "Compiz Options", "Loose Binding" and "Indirect Rendering".

Also, under the general option in CCSM, disable the detect refresh rate and turn the refresh rate up.

Hope that helps

---

### Post by anotherdisciple on 2008-09-23
Open up the system monitor (System > Administration > System Monitor) to see what is using up all your CPU... or your can open a terminal (Applications > Accessories > Terminal) and run:

```
top
```

That will show you what programs are eating up your processing power.

Also, try to turn off things that you don't use. Go to (System > Preferences > Sessions) and uncheck programs that you know you aren't using (ex. evolution alarm notifier? I don't use it). Turn off services by going to (System > Administration > Services) and turn off whatever you don't use (ex. bluetooth if your computer doesn't have the ability to use it).

---

### Post by Seaicmac on 2008-09-23
Thanks a million to you both for the help- seems to have improved both problems!

Jack

---

### Post by anotherdisciple on 2008-09-24
Cool... glad to hear it!

---

