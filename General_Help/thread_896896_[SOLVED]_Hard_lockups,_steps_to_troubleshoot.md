---
title: "[SOLVED] Hard lockups, steps to troubleshoot?"
date: 2008-08-21
forum: General Help
---

### Post by jerome1232 on 2008-08-21
My computer has started locking up after extended heavy disk usage.

Also sometimes it'll just lock up for no known reason.

I have two patterns it seems - heavy disk usage, and then it's also somewhat random.

I think either my PSU is dieing or my HDD is dieing, PSU can cause random lockups, and I've heard my HDD thunk once in a **great** while, the sound has never corresponded to a lock up, and it's very very rare that it does this (you've probably heard it, drop a HDD hard, turn it on and it just goes thunk, thunk, thunk repeatedly, maybe it's better described as tink, tink, tink) 

So my question is how can I diagnose a power supply without a known working one to swap out. (Have something that logs my voltages perhaps I can see a sag when the lock ups happen)

I have a second HDD but it's pata, so if it works that doesn't rule out my sata controller. Are there any good HDD diagnostic tools in the repos?

Any other opinions on culprits are welcome, I pass a memtest with flying colors. CPU temp tops at 50C full throttle after a full day in a 26+C room (according to google that's what 80F is) and my fan isn't set to really kick in until 60C.

---

### Post by Elfy on 2008-08-21
I have had both a power supply and a hdd - I caught the power supply when I was running xsensors - had it on the desktop and saw the volt drop as it locked up.

More recently - I have had some random lockups - shortly followed by a hard drive failure. 

You could install the smartctl tools - and see if there is sopmething amiss with the drive

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by jerome1232 on 2008-08-21
Okay well I think it's my PSU, I added the 2nd pata disk, and I couldn't even get logged in before everything would just lock up.

So I've disconnected all unnecessary devices, unhooked extra fans.

Until I can get a new PSU (me being out of a job might not be soon) I thought underclocking might help, but every time I do bootup just sits there at starting powernowd.

My cpu is 2.4ghz, I tried it at 2ghz 1.2ghz and at 800 mhz, all just kinda of sat there while loading powernowd, the computer is still running, I can get to other tty's, can even start gdm, but logging in complains about hal not being loaded and other things.
Works fine when at the full 2.4ghz

edit: thanks for the smartmontools link, I'm giving this hard drive funny looks because of the random noise thing.

---

### Post by Elfy on 2008-08-21
Wish I could help with underclocking but I've never done that :) as you say disconnecting things you're not using will help some.

Can't think of anything else that could help - other than making sure you're as ready as you could be for a potential hdd failure.

---

### Post by jerome1232 on 2008-08-21
Yesh I know a failing PSU is what took my HDD out 4 years ago, and thus I built this computer.

Underclocking down a notch, booting rebooting and going down another notch seems to do it, I guess it was just freaking out because of the sudden change. Down 800mhz and I'm can notice the difference but at least It shouldn't be as power hungry.

Hopefully it's not so much as failing but being a normal aging psu not putting out as much wattage as it used to, and just hit the point that my computer needs to work correctly. sad face.

edit: Xsensors doesnt' support my chips thanks though

---

### Post by Elfy on 2008-08-22
Did you run sensors-detect?

---

### Post by jerome1232 on 2008-08-22
Yeah, I ran sensors-detect, through some googling I found that lm-sensors config file has moved in hardy, when I run xsensor I get.

```
xsensors -c /etc/sensors3.conf 
Sensor 'k8temp' not supported by xsensors!
Sensor 'w83627ehf' not supported by xsensors!

```

edit: I'm off to bed now It's 1 am here thanks for the help thus far, I think smart showed no errors on my hard drive so that's good.

---

### Post by Elfy on 2008-08-22
Yep you're right - but there is a fix I found 

[http://www.linuxhardware.org/article.php?story=07/10/09/1854255&query=xsensors](http://www.linuxhardware.org/article.php?story=07/10/09/1854255&query=xsensors)

download and compile it would seem.

Good luck.

---

### Post by jerome1232 on 2008-08-22
Yup looks like compiling the new version did the trick. Only needed two dev pacakages, which is great with how much I love doing apt-cache searches lol.

---

### Post by Elfy on 2008-08-22
excellent - glad it worked for you.

---

### Post by jerome1232 on 2008-08-22
I see alot of red numbers on my power, is that bad? I don't see anything outputing 12v, I going to check in my bios to confirm these numbers I may be turning this computer off before that thing dies and fries everything.

vcore: 1.22v green
in1: 8.82v green
avcc: 3.38v red
3vcc: 3.38v red
in4: 1.33v red
in5: 1.5v red
in6: 5.86v red
vsb: 3.28v red
vbat: 3.28v red
in9: 1.63 red

---

### Post by Elfy on 2008-08-22
Not sure tbh - screenshot of mine, have you seen what terminal returns for ```
sensors
``` - I'll give you that as well

```
w83697hf-isa-0290
Adapter: ISA adapter
VCore:       +1.36 V  (min =  +0.00 V, max =  +2.08 V)
+3.3V:       +3.17 V  (min =  +0.53 V, max =  +0.26 V)
+5V:         +5.08 V  (min =  +3.52 V, max =  +0.00 V)
+12V:       +11.86 V  (min =  +1.95 V, max =  +0.49 V)
-12V:       -11.70 V  (min = -13.18 V, max =  -4.96 V)
-5V:         -5.10 V  (min =  -1.28 V, max =  -2.89 V)
V5SB:        +5.43 V  (min =  +5.59 V, max =  +0.03 V)
VBat:        +3.12 V  (min =  +2.05 V, max =  +0.00 V)
fan1:       3096 RPM  (min = 21093 RPM, div = 4)
fan2:          0 RPM  (min = 2636 RPM, div = 4)
temp1:       +40.0°C  (high = +32.0°C, hyst = +16.0°C)  sensor = thermistor
temp2:       +46.0°C  (high = +90.0°C, hyst = +90.0°C)  sensor = diode
beep_enable:enabled
```

Maybe a vist to the developer might be in order, [http://freshmeat.net/projects/xsensors/](http://freshmeat.net/projects/xsensors/)

This is the bugs page in launchpad - but I don't think there is anything there - [https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=xsensors&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=xsensors&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

I don't think I can do much more really, I can't replicate the problems you're getting without a new mobo, as much as I'd like to - which I'd like to get but money is tight here too :(

---

### Post by jerome1232 on 2008-08-22
Yeah I think this isn't reporting correctly (this would be a lm-sensor thing right?)

```
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +36.0°C                                    

w83627ehf-isa-0290
Adapter: ISA adapter
VCore:       +1.12 V  (min =  +0.00 V, max =  +1.74 V)   
in1:         +8.76 V  (min =  +5.02 V, max =  +9.77 V)   
AVCC:        +3.39 V  (min =  +3.02 V, max =  +2.35 V)   ALARM
3VCC:        +3.38 V  (min =  +1.89 V, max =  +0.24 V)   ALARM
in4:         +1.32 V  (min =  +0.89 V, max =  +0.30 V)   ALARM
in5:         +1.51 V  (min =  +1.18 V, max =  +0.38 V)   ALARM
in6:         +5.89 V  (min =  +0.59 V, max =  +4.89 V)   ALARM
VSB:         +3.34 V  (min =  +0.40 V, max =  +2.80 V)   ALARM
VBAT:        +3.30 V  (min =  +0.88 V, max =  +0.58 V)   ALARM
in9:         +1.62 V  (min =  +0.34 V, max =  +0.76 V)   ALARM
Case Fan:      0 RPM  (min =  703 RPM, div = 128)  ALARM
CPU Fan:    1240 RPM  (min =  703 RPM, div = 16)
Aux Fan:    1962 RPM  (min =  703 RPM, div = 16)
fan4:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
fan5:          0 RPM  (min =  703 RPM, div = 128)  ALARM
Sys Temp:    +41.0°C  (high = +111.0°C, hyst = +94.0°C)  sensor = thermistor
CPU Temp:    +30.5°C  (high = +90.0°C, hyst = +85.0°C)  sensor = diode
AUX Temp:    +39.0°C  (high = +90.0°C, hyst = +85.0°C)  sensor = thermistor
cpu0_vid:   +1.550 V

```

in my bios it showed the kind of voltages I would expect to see.
seems like sensors is setting odd min/max's to me, then again it's not naming things very well so I'm not sure what it's measuring.
according to bios. there was more but I didn't bother to write it all down.
```
cpu core: 1.53v
ddr: 2.67v
ddrvtt: 1.32  #not sure what that is
agp: 1.51v
+12v: 12.11v
```

---

### Post by Elfy on 2008-08-22
Yes it would certainly appear not to be quite right, but I wouldn't know how to check it out at the moment.

---

