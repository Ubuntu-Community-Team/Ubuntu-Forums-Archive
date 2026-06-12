---
title: "Hot Processors - DELL CS24-SC Server"
date: 2016-02-24
forum: Hardware
---

### Post by scott.bouch on 2016-02-24
Hi,


I have a DELL CS24-SC (1U high) Server conputer running Ubuntu 14.04 with kernel 4.2.0-30-generic.


I've also had this with older kernels.


My Fans run flat out, sounds like it could take-off, and the warning lED is flashing on the front.


Sensors reports these temperatures:


(It has two 4 core processors)




```
$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +69.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +62.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +64.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +63.0°C  (high = +84.0°C, crit = +100.0°C)


coretemp-isa-0001
Adapter: ISA adapter
Core 0:       +86.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +78.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +81.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +81.0°C  (high = +84.0°C, crit = +100.0°C)



```


Only one core is above the "high" value, but they are all pretty close.


Are these sorts of processor temperatures normal?


I just earlier tried running memtest, the air coming out of the server got really really hot, and it switched itself off... I assume one or more cores reached "crit" 100 degrees. Would this be expected behavior?


Just as I'm writing this, the fans dropped in speed, so I quckly ran sensors again:

```
$ sensorscoretemp-isa-0000
Adapter: ISA adapter
Core 0:       +66.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +59.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +60.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +59.0°C  (high = +84.0°C, crit = +100.0°C)


coretemp-isa-0001
Adapter: ISA adapter
Core 0:       +81.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +74.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +78.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +77.0°C  (high = +84.0°C, crit = +100.0°C)



```

This time, all below "high", but the warning led still flashes.

Cheers, Scott.

---

### Post by QIII on 2016-02-24
Is this occurring when the cores are all at idle?

---

### Post by scott.bouch on 2016-02-24
Hi, well, the server has a few applications always running... Zoneminder, Plex, Apache, but it's hardly calculating the London stock exchange..

Cheers, Scott.

---

### Post by QIII on 2016-02-24
Have you run top to see if there is anything unexpected going on?

The things you listed should use only a very tiny bit of your resources.  Effectively close to idle.

(Sorry about the basic questions here.  These are "rule outs" for diagnostic purposes.)

---

### Post by scott.bouch on 2016-02-25
I'm still learning Linux, and am happy to explore the basics!

(NOTE: I've omitted from Top results of any commands occupying 0% processor and memory)

Just after powering up, after being off all night and cool, fans running moderate:

```
$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +60.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +53.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +54.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +53.0°C  (high = +84.0°C, crit = +100.0°C)


coretemp-isa-0001
Adapter: ISA adapter
Core 0:       +60.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +57.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +58.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +55.0°C  (high = +84.0°C, crit = +100.0°C)

```


```
top - 13:43:28 up 2 min,  1 user,  load average: 0.33, 0.19, 0.08
Tasks: 191 total,   2 running, 189 sleeping,   0 stopped,   0 zombie
%Cpu(s):  3.4 us,  0.0 sy,  0.0 ni, 96.6 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   6110548 total,  1457720 used,  4652828 free,   419964 buffers
KiB Swap:        0 total,        0 used,        0 free.   515756 cached Mem


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                                                                                                                   
 1852 www-data  20   0  529748 201012 185176 S  15.9  3.3   0:14.28 zma                                                                                                                                                                       
 1706 www-data  20   0 1128352 264832 192232 S  10.6  4.3   0:10.80 zmc                                                                                                                                                                       
 1043 plex      15  -5 1550684  44224  21788 S   0.3  0.7   0:00.34 Plex Media Serv                                                                                                                                                           
 1362 mysql     20   0 1470344 120016  10612 S   0.3  2.0   0:01.02 mysqld                                                                                                                                                                    
 1867 plex      15  -5 1068476  31272  15976 S   0.3  0.5   0:00.62 Plex DLNA Serve                                                                                                                                                           
 1933 scott     20   0   25004   3208   2616 R   0.3  0.1   0:00.10 top                                                                                                                                                                       
    1 root      20   0   33808   4400   2712 S   0.0  0.1   0:03.86 init  
```    

I closed Top, then **the server crashed at this point** (unusual, don't know why), I lost SSH, but also couldn't log in directly either, while I was trying to log back in, the fans went to full speed.. Power off and on again at the mains...

It booted up with fans running at top speed, I assume as the processors were already hot.

```

$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +75.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +68.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +70.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +70.0°C  (high = +84.0°C, crit = +100.0°C)


coretemp-isa-0001
Adapter: ISA adapter
Core 0:       +88.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +80.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +84.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +84.0°C  (high = +84.0°C, crit = +100.0°C)
```


```
top - 13:55:24 up 2 min,  1 user,  load average: 0.36, 0.21, 0.08Tasks: 191 total,   1 running, 190 sleeping,   0 stopped,   0 zombie
%Cpu(s):  3.1 us,  0.0 sy,  0.0 ni, 96.8 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   6110548 total,  1449880 used,  4660668 free,   415856 buffers
KiB Swap:        0 total,        0 used,        0 free.   515708 cached Mem


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                                                                                                                   
 1900 www-data  20   0  529748 201256 185420 S  15.3  3.3   0:12.59 zma                                                                                                                                                                       
 1720 www-data  20   0 1128140 264044 192152 S   9.6  4.3   0:08.79 zmc                                                                                                                                                                       
   53 root      20   0       0      0      0 S   0.3  0.0   0:00.01 rcuos/6                                                                                                                                                                   
  263 root      20   0       0      0      0 S   0.3  0.0   0:00.02 jbd2/dm-0-8                                                                                                                                                               
 1948 scott     20   0   25004   3224   2632 R   0.3  0.1   0:00.10 top                                                                                                                                                                       
    1 root      20   0   33792   4308   2632 S   0.0  0.1   0:03.88 init
```

And a few minutes  later I tried again (no more crashes):

```
$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +70.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +63.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +64.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +63.0°C  (high = +84.0°C, crit = +100.0°C)


coretemp-isa-0001
Adapter: ISA adapter
Core 0:       +85.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +77.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +80.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +80.0°C  (high = +84.0°C, crit = +100.0°C)



```

```
top - 13:58:00 up 5 min,  1 user,  load average: 0.24, 0.21, 0.10
Tasks: 185 total,   2 running, 183 sleeping,   0 stopped,   0 zombie
%Cpu(s):  3.2 us,  0.1 sy,  0.0 ni, 96.6 id,  0.1 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   6110548 total,  1457264 used,  4653284 free,   417344 buffers
KiB Swap:        0 total,        0 used,        0 free.   515776 cached Mem


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                                                                                                                   
 1900 www-data  20   0  529748 201256 185420 S  15.6  3.3   0:36.91 zma                                                                                                                                                                       
 1720 www-data  20   0 1128508 264308 192152 S  10.0  4.3   0:24.84 zmc                                                                                                                                                                       
   78 root      20   0       0      0      0 S   0.3  0.0   0:00.07 kworker/1:1                                                                                                                                                               
   81 root      20   0       0      0      0 R   0.3  0.0   0:00.05 kworker/4:1                                                                                                                                                               
 1211 plex      35  15 1802820  55024  10400 S   0.3  0.9   0:03.76 python                                                                                                                                                                    
 1948 scott     20   0   25004   3224   2632 R   0.3  0.1   0:00.45 top                                                                                                                                                                       
    1 root      20   0   33792   4308   2632 S   0.0  0.1   0:03.88 init
```

The top two are www-data, I don't know what that means, but zma and zmc may relate to ZoneMinder... but they are still low CPU and memory usage

Thanks, Scott

---

### Post by v3.xx on 2016-02-25
Found this

> Dell&#8217;s thermal management system seems to have only 2 settings: off or maximum. The issue is that as long as the server is on it&#8217;s pretty much at the later. The fans never spin down no matter what the internal temperature is.

[http://aramblinggeek.com/on-the-dell-cs24-sc-server](http://aramblinggeek.com/on-the-dell-cs24-sc-server)

---

### Post by scott.bouch on 2016-02-25
Thanks v3.xx... My CS24-SC does seem to operate with variable fan speed while it's cool, but as soon as one of the processors have exceeded the "high" setting of [COLOR=#000000][FONT=arial]+84.0°C, the fans go to maximum speed, which is understandable as they are trying to save the processors from cooking[/FONT][/COLOR][FONT=arial]. The only unfortunate thing is that at least one of my processors spends most of it's time above [/FONT][COLOR=#000000][FONT=arial]+84.0°C , and therefore the fans run flat out most of the time. That blog post seems to have generallised a bit about these servers and missed some detail.[/FONT][/COLOR]

But the fans really aren't the issue, they are just a symptom, I think my main question is though, what temperatures ***should*** a fairly un-stressed processor operate at? I seem to be exceeding most temperatures stated here: [http://www.buildcomputers.net/cpu-temperature.html](http://www.buildcomputers.net/cpu-temperature.html)

The other issue is that the hot air from the processors then passes over the RAM sticks, making them really hot too. The ram gets so hot I can't touch it... can't be good for it.

Before I take it apart to clean out heatsinks, replace fans etc.. It would be nice to know if there's any fixable software reason for the high temperatures.

Some processor info (two quad core processors):

```
$[B] lscpu
[/B]Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                8
On-line CPU(s) list:   0-7
Thread(s) per core:    1
Core(s) per socket:    4
Socket(s):             2
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Stepping:              6
CPU MHz:               2003.000
BogoMIPS:              4666.86
Virtualisation:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              6144K
NUMA node0 CPU(s):     0-7
```

Cheers, Scott.

---

### Post by scott.bouch on 2016-02-25
Well,

I had the processor heatsinks off, found the paste to be very dried up.. So cleaned them up with some IPA, and applied fresh heatsink compound. Great.

Then the plot thickens.. I went to power it back up, only to be met by an almost dead server:


[LIST]
[*]No VGA output
[*]Slow running fans,
[*]Some motherboard led's on or flickering
[*]No LED on main OS SDD, but LED on secondary storage HDD
[/LIST]

I had this exact issue recently.. it was fixed by some man-handling, so I'm now going to have the motherboard out and check for a short to chassis, metal debris etc... Whatever is causing this issue, it seems to come and go with movement.

hmmm.. grumble grumble... When I have it running again, I'll be able to re-visit the processor temperatures, how frustrating.

Cheers, Scott.

---

### Post by scott.bouch on 2016-03-31
Hi all,

Well, I finally found some time to rebuild my CS24-SC server, and seem to have had some success on the face of it. It was a bit dirty, but I've seen dustier / dirtier computers in the past though.

[ATTACH=CONFIG]268099[/ATTACH]

I took every last component out, processors and all, gave everything a good scrub with Isopropyl Alcohol (IPA) and a brush and rebuilt it. Even cleaned out the Power Supply Unit board.

[ATTACH=CONFIG]268100[/ATTACH]

the boards weren't particularly dirty, but did have a LOT of flux on them from manufacturing. The IPA melted this all away.

I scrubbed and washed the main board in the sink with IPA (not water!!)

[ATTACH=CONFIG]268079[/ATTACH]

I did find some poor soldering on the main board on some ferrite ring inductors / chokes, so I re-soldered them just to be on the safe side.

[ATTACH=CONFIG]268081[/ATTACH]

There were also some metal brackets under the processors (on the underneath of the board) that come into contact with the main board with a tongue. They have some plastic insulation fitted to them, but one of the insulator pads was right on the edge, there's a chance the metal could have been shorting to a via hole on the main board, so I relocated the insulators to guarantee no contact.

[ATTACH=CONFIG]268080[/ATTACH]

The screwdriver shows where the edge of this bracket's tongue rested on the board, you can just make out some dust where it was. The orange insulator should have overlapped the end of the tongue, but this one was so close to the edge, the tongue *may *have been shorting to a via hole...

```
$ sensorscoretemp-isa-0000
Adapter: ISA adapter
Core 0:       +66.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +58.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +59.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +59.0°C  (high = +84.0°C, crit = +100.0°C)


coretemp-isa-0001
Adapter: ISA adapter
Core 0:       +68.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +62.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +64.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +64.0°C  (high = +84.0°C, crit = +100.0°C)



```


After 20 mins we're over 84 degrees, and the fans accelerated to full speed.

```
sensorscoretemp-isa-0000
Adapter: ISA adapter
Core 0:       +79.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +72.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +76.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +75.0°C  (high = +84.0°C, crit = +100.0°C)


coretemp-isa-0001
Adapter: ISA adapter
Core 0:       +86.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +80.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +85.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +85.0°C  (high = +84.0°C, crit = +100.0°C)



```

The fans brought the temperatures down again, and they returned to a steady speed, so they are regulating the processor temperatures nicely now!! It sounds much less like it's about to take off. The fans have spent the rest of the day having 10 mins low, few mins high, in an ambient room temperature of 19 to 20 degrees C. The air coming out the back of the server is measured at 35 to 40 degrees C, so is gaining about 15 to 20 degrees through the server depending on fan high / low speed.

So, I guess it's now a matter of leaving it running to see if it fails again.

Can't say 100% what's fixed it, or if it really is fixed yet or not, but giving it a good old clean up has really helped.

Cheers, Scott.

---

