---
title: "Lack of Hardware support when partitioned, vm instead?"
date: 2013-03-08
forum: Hardware
---

### Post by evol4g on 2013-03-08
Ok so I have a HP Envy m6-1105dx laptop
specs
amd a10 quad-core processor
6gb of ram (about to upgrade to 8)
and other features that really shouldn't matter


point is, there are basically no drivers for support. Here are the issues i'm facing when using my ubuntu on it's own partition

Lack of HDMI support, (it works but with no sound)
Battery life is AWFUL (2 hours on a brand new computer, 1 hour when compiling android roms) 
HP CoolSense doesn't work so the laptop gets extremely hot
AMD Turbo-Core doesn't enable either


So I was wondering, do you think it would be better in a virtual machine enviroment to preserve the over all length of the life of the laptop, given the major overheating issue mentioned above.. Also I was hoping my ROMs would compile faster with turbo core, but one thing i was also looking at was the system monitor when compiling, most of the time the processor isnt' using over 50% of it's capability, but using all the RAM, if anyone knows how compiling works will upgrading my ram up to the extra 2gb help on my times, and will turbo core help with my compile times at all? and i'm already assuming my battery life will go down to about 4hrs with a vm because i'm currently getting about 6 on windows.. but about 4.5-5 with performance mode enabled.


thanks for taking the time to read this and i'd love to see your guy's responses :)

---

### Post by Lisiano on 2013-03-08
For the laptop

[LIST=1]
[*]Have you tried installing the [ATI Proprietary drivers]("apt://fglrx")?
[*]Battery life depends on your settings. Logically maximum brightness, active WiFi/Bluetooth, etc will drain the battery faster. Install [PowerTop]("apt://powertop") (CLI app) so you can tell exactly what is using the most power (And enable some "tunables" that will increase battery life). It might also increase if you install the [ATI Proprietary drivers]("apt://fglrx") as they might be better at managing power usage.
[*][COLOR=#000000]HP CoolSense is simply a marketing name for a simple fan speed control override. You are better off letting your PC manage the fan speed by setting it in your BIOS to either Auto or Maximum speed (if you don't mind the noise).[/COLOR]
[*]AMD Turbo-Core is a marketing name for self-overclocking. This is usually controllable from inside the BIOS. It is also not-OS-specific. If your CPU features self-overclocking, it will overclock by itself, unless that feature is disabled in the BIOS.
[/LIST]
For compiling in general
[LIST=1]
[*]You should use ```
make -J4
```This will cause make to use 4 threads to compile stuff. Experiment a bit by increasing -J to 5, 6, 7, 8... Once you see you are getting 90~100% utilization (Give or take), you hit the sweet spot.
[*]Android is fat. All source is fat actually... With more RAM, your laptop can hold more stuff in memory, having to touch the disk less often. Ofc having a faster disk is even better, an SSD more so.
[/LIST]

---

### Post by evol4g on 2013-03-08
ok, my bios is lame and doens't have all these settings for fan speeds and such, i am using the ati drivers, i always do when available.. so i'll look up a tutorial for upgrading my bios, the only reason i really haven't looked into it was because i'm worried i might lose my windows 8 product key since it is stored in bios... BUT it must be able to be done. and good lookin on PowerTop! i'm gonna try that out a lil later tonight when i reboot into ubuntu to do a compile. :D 

any thoughts on getting audio for hdmi working? i tried one fix but now when i plug it in to charge i get no display at all.. its quite awkward

---

