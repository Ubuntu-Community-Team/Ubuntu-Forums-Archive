---
title: "fan help!!! toshiba l305, 8.10"
date: 2009-06-21
forum: Hardware
---

### Post by kdreimiller on 2009-06-21
i cant find an answer or help anywhere.

for some odd reason today my fan won't kick on anymore and my computer is running hot!  like around 80c all the time.  i didn't do anything as far as i know.  i just want to make the fan run!  

if it helps, im on h20 bios insyde, v1.20, intrepid, satellite l305 3 gigs mem, dual core amd.

any ideas?

kevin

---

### Post by bondmatt on 2009-06-21
Have you installed ls sensors and configured it? I had a similar issue but it was with PCLinux and my HP.

ls sensors is just added in synaptic. To configure you just open a terminal and type 'sudo sensors-detect'. From there you just follow the prompts (answer yes or no) and then restart.

Regards,
MJB

---

### Post by kdreimiller on 2009-06-21
when i run "sensors-detect" it only scans my systems and tells me what's there.  it doesnt actually congifure anything for me.  unless i missed something, which is quite likely.

---

### Post by bondmatt on 2009-06-21
I know I rush through those kinds of processes and I did miss the last part myself. It gives code that can be manually added to a script or automatically added. I let it do it automatically because the one time I tried to do it manually I killed my GUI (it was KDE in PCLinux). I religiously back up files, especially if I modify anything, and it saved my butt that time.

I also found that I had to restart to see any effect from the sensors-detect configuration.

Good luck,
- Matt Bondy

---

### Post by Johnny B on 2009-06-21
lm-sensors won't help.  its a hardware problem, right? does the fan spin during BIOS? no?
get some dust-off and clean out your fan, and contact the manufacturer if its still under warranty .

---

### Post by kdreimiller on 2009-06-21
yup, it spins at bios, and it spins low after that, but never enough to properly cool.  im thinking the fan is clogged as you said.

---

### Post by morfic on 2009-07-11
ro quiet splash thermal.tzp=400 thermal.act=45 thermal.psv=90

my kernel command line, gets me decent idling unlike the high temperature i get w/o the above, those are just trip points and a polling frequency, 400 is every 40 seconds.
I can see it has trouble turning the fan off....every 40 seconds i get the message it can not enter state D3 (off)
It also never seems to run at full speed
This is certainly not a hardware issue like a dirty fan, i just have not found yet what *is* the cause.
I figured i bump this thread, gives you a chance to help me out if yours works better, or perhaps this makes things work for other people, the default trip points are WAY high and idling at 38-43C (based on ambient temperature is just much better than 60-70C as it did before.
I had this in 8.10, still have it in 9.04, have it with 2.6.30 kernel.....
using the omnibook module with 'modprobe omnibook ectype=11' does not improve things.

somehow this never showed itself when i ran ubuntu through wubi, since i neve bothered switching to ondemand scheduler and with performance scheduler, fan always ran full speed, so the full install of ubuntu with ondemand scheduler used kind of surprised me there.

---

