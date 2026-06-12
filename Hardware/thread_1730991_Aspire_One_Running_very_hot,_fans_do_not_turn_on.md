---
title: "Aspire One Running very hot, fans do not turn on"
date: 2011-04-16
forum: Hardware
---

### Post by cafejunkie on 2011-04-16
I am running an Acer Aspire One D255 netbook, 1.6Ghz Atom N450, 1GB of RAM., Ubuntu 10.10, 2.6.35-28.
I have installed lm-sensors, and loaded the required kernel modules. The sensor now reports the coretemp correctly. However, at idle the netbook runs at around 52-54 degrees Celsius. In an attempt to have the fans kick on I opened up multiple tabs in chromium, had music playing via mpd and started playing a game. At that point the temperature shot up to 70 degrees C and the fans still did not turn on (it has a max of 100 degrees). In an effort to determine the cause I tried a couple other distros (mainly Debian (sid) and Arch Linux both with 2.6.38-2) both of which has the fan on full speed 100% of the time (not desirable either)
When windows 7 was on the netbook when I first got it, the idle temp stayed around 40 degrees Celsius and under a heavy load never got above 57 degrees at which point the fans clicked on. 
Packages I have installed to manage power settings:
acpi, lm-sensors, powertop, cpufrequtils. 
Has anyone else experienced this with this (or other) netbooks? I've only ever used old laptops (PIII and PIVs) which never had a similar problem with any of the many distros I've used. Any suggestions? I'd like to know if I should exchange the netbook for something more Linux friendly or if it's just a kernel/distro issue that will be fixed soon :) (I refuse to run Windows).

---

### Post by marin123 on 2011-04-16
after a fresh install, did that happen or did you install lm-sensors and everything immediately?
newer laptops have acpi to take care of temps... try booting livecd (or usb) and see what happens without installing sensor packages...

---

### Post by cafejunkie on 2011-04-16
Thanks for the quick rely!
It happened on the fresh install, that's what prompted me to install lm-sensors and such (and to improve the battery life).

---

### Post by GTMoraes on 2011-04-17
Acer Aspire netbook here, not the "One" though. Fan works OK, when hot spins up, when cool spins down, Although looks like Ubuntu cannot control the fans, but does the BIOS.
Have you thought about updating your BIOS? If so, hope you still have your Windows installation, because that's the only possible way to update it =(

Just for the kicks, try running the Live versions of Maverick and Natty... see if any of them can control your fan

Also, there's an option available on HP Minis BIOS's called "Fan Always On". If I were you, I would check if that option is available on the One too =)

Good luck, and be careful when playing around with the bios!
[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | 6:30hrs Battery | Ubuntu Natty
[size=1]|[color=#7FFF00]Microsoft WMM 4000[/color]|[/size]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE="1"]**Ubuntu Powered.**[/SIZE][/CENTER]

---

### Post by cafejunkie on 2011-04-17
Thanks for the advice.
Unfortunately I dumped the windows install not too long after I had it (been Windows/Mac free since 1999 :P). I did make sure the BIOS was up do date before doing that though. Sadly, the One's bios (at least on this model) doesn't have the "Fan Always On" option. 
One thing I did notice though, in the output of sensors:
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +29.0°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +53.0°C  (crit = +100.0°C)   
```

When the "virtual device" starts to get hot, the fans click on (although not at a super high speed). I'll blacklist that module so it only reads the coretemp and see if that fixes it. I'll report back the findings for anyone else who might have this issue!

---

### Post by GTMoraes on 2011-04-17
> **cafejunkie said:**
> Thanks for the advice.
Unfortunately I dumped the windows install not too long after I had it (been Windows/Mac free since 1999 :P). 
I always send them back for Windows removal and refunds =)
Windows costs alot here (If I'm not wrong, the 7 Ultimate cost something close to 4 digits, around 350, 400 US dollars). It's good having the money back =P

Back on topic.. I'm wondering what would happen if your Ubuntu installation couldn't see the temperatures at all..
Have you tried uninstalling it?
[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | 6:30hrs Battery | Ubuntu Natty
[size=1]|[color=#7FFF00]Microsoft WMM 4000[/color]|[/size]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE="1"]**Ubuntu Powered.**[/SIZE][/CENTER]

---

### Post by cafejunkie on 2011-04-17
Okay, did a bit more research. Turns out the acpitz-virtual-0 is an acpi thermal zone, read from /proc/acpi/thermal_zone. I cannot find if it's a kernel module, blacklisting both "acpitz" and the full name didn't work. Whenever I reboot the fan will turn on once ubuntu boots up (if its around the 55*C range) for about 10 seconds, then turn off. I'd chalk it up to hardware if it behaved the same across distros/windows but it seems to be a different behavior across them. 
I'd like to have the fans go off of the real coretemp not just a thermal zone, as that acpi thermal zone doesn't always report correctly (as in I have a hard time believing when the netbook is hot to the touch and the coretemp is close to 80 that the thermal zone is only 29*C lol).

Oh, and about uninstalling it. I have uninstalled it, even let the netbook just sit and run without any OS and the fan was on full speed 100% of the time. So I think the BIOS defaults to have it run all the time, the OS overrides it. If only I can figure out how to set the fans to turn on/off based on my core temp and not the thermal zone.
Thanks for the help so far though!

---

### Post by GTMoraes on 2011-04-17
for the sake of conscience, there's no way to activate any kind of "SmartFan" thru BIOS, right?
I'm kinda new to Ubuntu, not sure if it's possible but.. Can't we just redirect the fans for the correct position?

I've remembered something, I've had a similar issue with a K8 Brisbane core processor, which reports temperatures 20ºC less than the normal (it's a known processor bug). A patch forces it to read 20ºC more from the core and the fans works as they should. If the ACPI thermal zone and the core temp from your net are proportional, you could resort to this...

Wish I could help more, I barely have a month of Ubuntu knowledge
[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | 6:30hrs Battery | Ubuntu Natty
[SIZE=1]|[COLOR=#7FFF00]Microsoft WMM 4000[/COLOR]|[/SIZE]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE=1]**Ubuntu Powered.**[/SIZE][/CENTER]

---

### Post by pyrforos on 2012-03-01
ok guys.. exact same problem here
sorry  to  bring up this old thread but i  didhnt find any solution  to my problem 
any  suggestions?

EDIT:
Found  this [http://ubuntuforums.org/showthread.php?t=1730991](http://ubuntuforums.org/showthread.php?t=1730991)
Worked for me!

---

