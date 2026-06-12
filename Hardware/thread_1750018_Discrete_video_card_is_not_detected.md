---
title: "Discrete video card is not detected"
date: 2011-05-05
forum: Hardware
---

### Post by anderston on 2011-05-05
I have an hp dv7-6000er laptop with two graphic cards: integrated Radeon HD 4200 and dicrete Radeon HD 6650m card. I tried both opensource and proprietary drivers, but still while the integrated card is working, the discrete is not.

Here is some output 
```
 aticonfig --list-adapters
* 0. 01:05.0 ATI Mobility Radeon HD 4200 Series

* - Default adapter

```

```
lspci
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
```


Both cards worked under windows 7 but not under linux.
It seems that my issue may be somehow related to this one: [http://ubuntuforums.org/showthread.php?p=10686990]("http://ubuntuforums.org/showthread.php?p=10686990")

---

### Post by m3ld4r10n on 2011-06-08
[FONT=Arial]I've been playing myself. I've tried literally everything I could find on google over the past few days. I'm not happy with vga-switcheroo, nor with blacklisting the driver.

I followed the walk through here 
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)

And I learned that  [FONT=monospace]y[/FONT]ou don't need a script to change from Intel->ATI and ATi->Intel. Once the fglrx driver is installed and the links are properly  configured, the switch [/FONT][FONT=Arial]should be done by the Ati Catalyst control panel in the desktop, or by sudo aticonfig --px-igpu or sudo aticonfig --px-dgpu in the command line.

I would imagine the same could be said of us IF WE could get our hardware properly installed.

I too have a integrated ATI HD Radeon and Discrete ATI HD Radeon.

Now although both are detected by

[/FONT]> $lspci
...
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series] (rev ff)
02:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series] (rev ff)
...
[FONT=Arial]

When I install the radeon driver and CCC it only installs drivers for the integrated card and only lists the integrated one in xorg.

Unfortunately this GPU stuff is way out of my comfort zone as i've never dabbled in it.

So if anyone could shed light on how to get our cards properly installed I think we may be able to make use of a switching feater already available. I'm dying for hdmi output for the occasional film on tv
[/FONT]

---

### Post by cyberbrain_12 on 2011-06-08
Take a look here ...
your problem concerns the **hybrid graphic cards** ...! case you want to more search...i gave up ....i had had the same problem ...and i'm now using the intel one :( ...so just check this one : 
[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

---

