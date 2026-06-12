---
title: "MPLAB IDE Works!"
date: 2008-11-04
forum: Hardware
---

### Post by au-steve on 2008-11-04
Hello all, I've just started with Ubuntu (2 months now) and was almost turned away while trying to use MPLABS IDE with the ICD 2 programmer.

After 3 hours and a headache to kick, I finally got the IDE running with Crossover. The programmer successfully works across the serial interface using a prolific USB to serial converter. It would however only work with the PICC PRO compiler, not the lite version, weird. I cannot get the USB to work still, and thats my next mission.

I've noticed a handful of people trying to use MPLAB software with Linux and upon failing have turned to piklabs. Piklabs is fantastic, however it has limited support for some microchips as it is still in development. So hopefully Crossover staff can add support for this product (MPLABS) and keep another handful of people interested in Linux.

Steve


EDIT: I've just realised ive posted in the wrong section. Terribly sorry

---

### Post by hvymtlsteve on 2008-11-04
Welcome! Interesting to hear that MPLAB is working, I think I've tried it on Wine before but didn't have much luck. I think there has been some documentation on it at the microchip forums but I just figured the USB part would be too much of a hassle that way. 

At any rate, I'm quite happy with Piklab, which has been built into the Ubuntu repositories for the last couple of releases (the first time I tried Piklab, on 6.04 or so, I had to alien an rpm and install some dependencies, but it still worked). 

Have you tried it? All you need is 
```
sudo apt-get install piklab
``` 
and you're good to go!
[http://piklab.sourceforge.net](http://piklab.sourceforge.net) has all the info on it, what chips and programmers are supported and all that good stuff.

I've never used the ICD2 but it's supposed to be supported... 
PicKIT2 works with USB, though, for sure.

Cheers,

Steve

---

### Post by au-steve on 2008-11-05
So I had a look at PikLab just then. The IDE looks nice, and I found it easy to get around. However, the 18F65J11 is not supported with the ICD 2 as of yet. Hopefully it will be soon, or I may write to the PikLab crew and try and get them to hurry along  ;)

Some of the other programmers look nice, but for now i'm going to stick with the ICD2 and serial link! It's not too slow, but USB would be nice.

Good to see other micro controller programmers using Ubuntu!

Steve

---

### Post by physeetcosmo on 2009-01-07
Steve,

i am also using Microchip's PIC in Ubuntu (or at least trying anyway ;)). i just navigated to Ubuntu from WinXP about a week ago. i love it!

Anway, back to PIC. i am installing Piklab as i am typing this, however the list in Piklab doesn't show any kind of support for the PIC32 which is what micro i am using. 

One questions: do i still need to install something other than Piklab to interface with my board?

Thanks!:D

---

### Post by promet on 2009-03-15
Hello,

I am also trying to get Piklab working. It loads and seems to work generally, i.e. it functions and detects the MPLAB ICD2 I've got connected via USB.

When I try to flash my target board how ever, Piklab reliably crashes with the error:
```

kbuildsycoca running...Reusing existing ksycoca
KCrash: Application 'piklab' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
```I've tried fishing around Google and Debian Packages in some KDE Packages to find the **"drkonqi"** file, but have so far been unsuccessful, it seems to be tucked away pretty good. Anyone aware of this issue or the package containing **"drkonqi"**?

---

### Post by Mervaka on 2009-04-20
> **promet said:**
> Hello,

I am also trying to get Piklab working. It loads and seems to work generally, i.e. it functions and detects the MPLAB ICD2 I've got connected via USB.

When I try to flash my target board how ever, Piklab reliably crashes with the error:
```

kbuildsycoca running...Reusing existing ksycoca
KCrash: Application 'piklab' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
```I've tried fishing around Google and Debian Packages in some KDE Packages to find the **"drkonqi"** file, but have so far been unsuccessful, it seems to be tucked away pretty good. Anyone aware of this issue or the package containing **"drkonqi"**?

i get exactly the same problem :(

---

### Post by dandaman0061 on 2009-04-26
I get the same "drkonqi executable not found" error crash when I try to program the MCU through piklab.  This may be a clue though...

I tried to 'sudo apt-get install drkonqi' and it told me that 'drkonqi' had been replaced by package 'kdebase-runtime-data' and that I was already at the newest version of 'kdebase-runtime-data'.  Hmmm... does piklab need to know about this?  I'm going to dig some more...

---

### Post by dandaman0061 on 2009-04-26
Well, after a bit of researching... drkonqi is 'KDE crash handler gives the user feedback if a program crashed' ...so the crash is probably happening before it can't find drkonqi

drat.

---

