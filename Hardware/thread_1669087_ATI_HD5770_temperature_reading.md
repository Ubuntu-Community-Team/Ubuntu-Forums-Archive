---
title: "ATI HD5770 temperature reading"
date: 2011-01-17
forum: Hardware
---

### Post by josepaul on 2011-01-17
hey guys, was wondering, how do you get the temperature reading of such a card? The sensor is definitely there (can be used in windows) but when I tried lm-sensors it doesn't come up. anyone who has HD5770 temperature reading working?

---

### Post by josepaul on 2011-01-17
bump

---

### Post by Call_M on 2011-03-09
Sorry to break into your topic but since there was never an answer... 

I have the same card and installed the ati drivers. 

With 
```
aticonfig --adapter=0 --od-gettemperature
```You should get a temperature read but for me it does not seem to work. I get the following message:

> No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configurationfile manually and run aticonfig again.
aticonfig: parsing the command-line failed.Then I ran:
```
sudo aticonfig --initial

```This gives the following message:
> Found fglrx primary device section
 Unable to find any supported Screen sectionDo you get the same messages??

Does anybody have a solution for this?

BTW
my xorg.conf file looks as follows:


[HTML]Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection[/HTML]

---

### Post by Yellow Pasque on 2011-03-09
Generate a new xorg.conf:
```
sudo aticonfig --initial -f
```

---

### Post by Call_M on 2011-03-09
I solved the problem by running:

```
sudo aticonfig --initial -f

```
and a restart.

[COLOR=Silver][COLOR=Black]```
aticonfig --adapter=0 --od-gettemperature
```[/COLOR]
[/COLOR]Gives now a temperature read.

and 

[COLOR=Black]```
aticonfig --pplib-cmd "get fanspeed 0"[/COLOR]
```
Gives the fan speed.

Did this also helped you @TS?

---

### Post by Call_M on 2011-03-09
> **Temüjin said:**
> Generate a new xorg.conf:
```
sudo aticonfig --initial -f
```

You where first! :popcorn:

---

