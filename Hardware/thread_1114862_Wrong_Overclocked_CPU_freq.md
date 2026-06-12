---
title: "Wrong Overclocked CPU freq"
date: 2009-04-03
forum: Hardware
---

### Post by darkcrawler on 2009-04-03
I overclocked my e4600 from 2.4 to 3.00 GHz in my ubuntu intrepid pc.
I usually use conky to show my cpu freq and in altrenative even cat /proc/cpuinfo.

If i set FSB 250 and molti 12x (250x12 = 3.00 GHz) conky and proc/cpuinfo show cpu freq is 3.00 GHz. Right.

If i set FSB 300 and molti 10x (300x10 = 3.00 GHz) i get from both a cpu freq of 3.60 GHz.. so it seems that the systems can't see that the molti is 10X instead of 12x..

I prefer using the 300x10, but is there something i can do to get the right value of cpu freq? Or is there another way apart cat /proc/cpuinfo to get the right value of my cpu freq?

Thanks to everyone. ;)

---

### Post by darkcrawler on 2009-04-04
no one got the same issue?

---

### Post by cubeist on 2009-04-04
don't mean to be a pessimist, but are you sure you are correctly using the multiplier... cause 12 x 300 is 3.6 ghz.  On my AMD system, /proc/cpuinfo displays correctly whatever combo of multiplier/fsb I use, so this could be a intel bug; you might want to check launchpad to see if anyone else has this.

Also, you should be cautious about such huge swings in FSB OC, 50 MHz is huge.  I mainly use multiplier, and have never exceeded +/- 10MHz on my FSB...but mayber intels are better at that than amds...

---

### Post by darkcrawler on 2009-04-04
Absolutely sure i use 10x molti, because i'm using stock Vcore. To reach 3,60 GHz i have to give more then 1,40 Volts! It wouldn't boot with 300x12 and stock Voltage, but would be great!! :)
I'll try to take a look at launchpad..

In the meantime if someone else has the same issue, tell me more..

---

### Post by HPD2 on 2009-04-04
I have had the same problem on one of my computers. It would seam that the OS can not detect the change in the multiplier and just uses the default multiplier to calculate the GHz. I was over clocking an Allendale 2.0GHz, default multiplier of 10, I changed it to 8 and could not get the correct reading through any OS, only the bios would give the correct GHz.

---

### Post by cubeist on 2009-04-05
definitely an intel issue, not amd, as conky is reporting the correct core and multiplier.  For example, right now I have 3178 MHz from a 15.5x on 205 MHz.

probably a good idea to file a bug report.

---

### Post by darkcrawler on 2009-04-05
Update:

with 'sudo lshw' in the cpu section i get this:

```


 *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E4600  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: LGA775
          **size: 3000MHz**
          capacity: 3800MHz
          width: 64 bits
          clock: 300MHz

```

So seems that the sistem get the right value of cpu freq.. At the moment this is the only way to get this value, but not so nice to put into my conky..

---

### Post by cubeist on 2009-04-06
I seem to recall an app in synaptic called hwinfo that you could use with conky...or since you know what speed your proc is, you could just write it in; I know, not as cool, but still effective!

---

### Post by darkcrawler on 2009-04-06
Thanks cubeist, i installed and tried hwinfo but get 3600 MHz.. :mad:

Seems for now there's nothing else to do except write in conky: 'CPU speed: 3000 MHz'

But there must be something to fix this issue..

If everyone has an idea, i'm here to listen and try ;)

---

### Post by cubeist on 2009-04-06
Try posting in this forum:

[http://ubuntuforums.org/showthread.php?t=281865&page=640](http://ubuntuforums.org/showthread.php?t=281865&page=640)

and you might get a better response!

---

### Post by darkcrawler on 2009-04-07
Thanks for now ;)

---

