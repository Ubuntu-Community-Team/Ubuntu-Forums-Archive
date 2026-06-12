---
title: "ATI Mobility Radeon 5470m overheating issue."
date: 2014-01-04
forum: Hardware
---

### Post by gymfreak7855-e on 2014-01-04
Hi, 

I'm currently running Ubuntu 13.10 and have just installed the latest fglrx drivers successfully and after a day of use I'm finding my Dell Inspiron 15R N5010 is becoming very hot beneath the keyboard. I went to investigate and by using amdconfig in the terminal I was able to find out that my graphics card is running at it's maximum clock speed all the time (750mhz). I believe it should vary or at least clock down when not under load (which at the time was 0%). Does anyone in the community know of a solution to this problem? I believe it will not only reduce the overheating issue but improve battery life exponentially. The card currently is idling at around 90 degrees Celsius which is ridiculous for an idling card. Under Windows it used to only get up to 70 degrees on maximum load. I have tried replacing thermal paste etc and this has not solved the issue. 

My system is of the following specifications: 
Dell Inspiron 15R N5010
Intel i3 350m @ 2.26ghz*2
6gb DDR3 @ 1333mhz
ATI Mobility Radeon 5470 w/ 1gb DDR3 dedicated running on the latest 13.12 catalyst fglrx drivers. 
500gb HDD @ 5400rpm

---

### Post by QIII on 2014-01-04
Hello!

Could you please post the results of 

```
amdconfig --pplib-cmd "get activity"
```

Also, I think the i3 350m has on board graphics.  Is that correct?

---

### Post by gymfreak7855-e on 2014-01-05
here is the output of [COLOR=#000000][FONT=Ubuntu Mono]amdconfig --pplib-cmd "get activity":

[/FONT][/COLOR]Current Activity is Core Clock: 300MHZ
Memory Clock: 300MHZ
VDDC: 900
Activity: 0 percent
Performance Level: 2
Bus Speed: 2500
Bus Lanes: 16
Maximum Bus Lanes: 16

The 350m is meant to... but my laptop for some reason does not. I have tried to install intel onboard drivers in window when I was running windows and it didn't detect onboard graphics.

---

### Post by Yellow Pasque on 2014-01-05
Try uninstalling proprietary drivers and using the radeon.dpm trick:
[https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later](https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later)

---

### Post by gymfreak7855-e on 2014-01-06
I would rather not do that as I use my laptop for playing games (dota 2). The open source drivers aren't the greatest when it comes to opengl...

---

### Post by QIII on 2014-01-06
Notice that the activity reported by amdconfig is 0 on your ATI GPU.

I think what you are running into is the basic Intel/ATI hybrid graphics problem.  It has been a horrible mess for a couple of years because the OEMs have not supported these configurations well in Linux.

There may be hope since you are using 13.10, which has a newer graphics stack and a brand new addition.  I have not been able to test this personally because I don't personally have a laptop with Intel/ATI hybrid graphics.  But of the four cases I have seen so far on the forums, the following suggestion worked for two and failed for two.  It's worth a try.

pxpress is new and it doesn't seem all the kinks are worked out yet, but have a look [here]("https://wiki.ubuntu.com/X/Config/HybridGraphics") after uninstalling the fglrx driver and renaming /etc/X11/xorg.conf.

---

