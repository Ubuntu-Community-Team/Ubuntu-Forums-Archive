---
title: "Investigating Intel GMA950 Overclocking"
date: 2011-02-26
forum: Hardware
---

### Post by agrh on 2011-02-26
**Introduction**

I'm posting my experience with overclocking Intel's GMA950 graphics core here to share my findings as well as gather the findings of others in an attempt to create a thread of solid information. Although there are a few programs and howto's which claim they have tested their methods and assure users they work, none of them explain to my satisfaction how they have been tested or where their information comes from.

Having said that, while there are no stupid questions, if you'd like to add to the discussion please supply links to your sources, even if those links contain opinions or information which is unsupported. If you would like share your experience with performance at different clockspeeds then, for example, link to a non-copyrighted Flash video so that other users can test the video at different clockspeeds to confirm the results.

Intel's datasheet for the GMA950 can be found at [http://www.intel.com/Assets/PDF/datasheet/307502.pdf](http://www.intel.com/Assets/PDF/datasheet/307502.pdf)

**My Experience**

There are only three programs I've used in my tests; [FONT=Courier New]setpci[/FONT], [FONT=Courier New]lspci[/FONT] and [FONT=Courier New]intel_gpu_top[/FONT] which can be found in the intel-gpu-tools package. It'll be helpful for you to read the man pages for these.

There is a forum post at [http://forum.eeeuser.com/viewtopic.php?id=67632](http://forum.eeeuser.com/viewtopic.php?id=67632) which includes a script with a list of [FONT=Courier New]setpci[/FONT] commands for changing register values for the GMA950 but doesn't provide any information on what these actually do. The author of the script, marx, states that he discovered this method by disassembling [GMABooster]("http://www.gmabooster.com") but doesn't go into any detail about that. fewt, the author of Jupiter, states that he tested this but also doesn't go into any detail about how it was tested. This was my starting point and here are my findings:

```

**#** setpci -s 00:02.0 f0.b=00,60
**#** setpci -s 00:02.0 f0.w
6000

```The first command writes to the register, the second returns the value of that register. See the man page for info on those commands. After setting the register I ran intel_gpu_top to check the actual clockspeed:

```

**#** intel_gpu_top
render clock: 166 Mhz  display clock: 200 Mhz
                     ring idle:  98%: &#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9611;                     ring space: 0/126976 (0%)
                          task  percent busy

                   Bypass FIFO:   0%:                      
              Color calculator:   0%:                      
                Intermediate Z:   0%:                      
                    Windowizer:   0%:                      
                  Pixel shader:   0%:                      
     Perspective interpolation:   0%:                      
                    Map filter:   0%:                      
                    Dispatcher:   0%:                      
                 Sampler Cache:   0%:                      
                     Filtering:   0%:                      
                        Map L2:   0%:                      
            Projection and LOD:   0%:                      
 Dependent address calculation:   0%:                      
         Texture decompression:   0%:                      
                 Texture fetch:   0%:                      
                  Setup engine:   0%:                      
               Strips and fans:   0%: 

```As you can see the render clock has been set to 166Mhz while the display clock remains at 200MHz, the rest of the output is not really important for us so I'll be trimming it out for the remainder of the commands.

```

**#** setpci -s 00:02.0 f0.b=31,05
**#** setpci -s 00:02.0 f0.w
0501
**#** intel_gpu_top
render clock: 200 Mhz  display clock: 200 Mhz

``````

**#** setpci -s 00:02.0 f0.b=33,05
**#** setpci -s 00:02.0 f0.w
0503
**#** intel_gpu_top
render clock: 250 Mhz  display clock: 200 Mhz

```Here is where I became more suspicious of the validity of the script as you can see that render clockspeed actually remains the same. I tested the register write coming from 00,60 and by that I mean copying how the script sets the clockspeed to 166MHz before setting any other clockspeed. The results were the same and I'm not sure why the script does this as, but again there is no explanation.

```

**#** setpci -s 00:02.0 f0.b=34,05
**#** setpci -s 00:02.0 f0.w
0500
**#** intel_gpu_top
render clock: 250 Mhz  display clock: 200 Mhz

```**Conclusion**

It may be that there is missing functionality in [FONT=Courier New]intel_gpu_top[/FONT] but it seems to me that most information out there is based on GMABooster, an undocumented program, and although the Intel datasheet states the clockspeed can reach 400MHz I haven't found a way to get it there or if I have prove it.

I also don't have any real understanding of PCI registers or the difference between the display clock and the render clock. If someone could share their knowledge of registers I'm sure that would shed a lot of light on this subject and coupled with information on the difference between the render clock and the display clock we might find a way to really solve this.

I eagerly await your input and RTFM links :)

---

### Post by fuduntu on 2011-02-27
> **agrh said:**
> **Introduction**

I'm posting my experience with overclocking Intel's GMA950 graphics core here to share my findings as well as gather the findings of others in an attempt to create a thread of solid information. Although there are a few programs and howto's which claim they have tested their methods and assure users they work, none of them explain to my satisfaction how they have been tested or where their information comes from.

Having said that, while there are no stupid questions, if you'd like to add to the discussion please supply links to your sources, even if those links contain opinions or information which is unsupported. If you would like share your experience with performance at different clockspeeds then, for example, link to a non-copyrighted Flash video so that other users can test the video at different clockspeeds to confirm the results.

Intel's datasheet for the GMA950 can be found at [http://www.intel.com/Assets/PDF/datasheet/307502.pdf](http://www.intel.com/Assets/PDF/datasheet/307502.pdf)

**My Experience**

There are only three programs I've used in my tests; [FONT=Courier New]setpci[/FONT], [FONT=Courier New]lspci[/FONT] and [FONT=Courier New]intel_gpu_top[/FONT] which can be found in the intel-gpu-tools package. It'll be helpful for you to read the man pages for these.

There is a forum post at [http://forum.eeeuser.com/viewtopic.php?id=67632](http://forum.eeeuser.com/viewtopic.php?id=67632) which includes a script with a list of [FONT=Courier New]setpci[/FONT] commands for changing register values for the GMA950 but doesn't provide any information on what these actually do. The author of the script, marx, states that he discovered this method by disassembling [GMABooster]("http://www.gmabooster.com") but doesn't go into any detail about that. fewt, the author of Jupiter, states that he tested this but also doesn't go into any detail about how it was tested. This was my starting point and here are my findings:

```

**#** setpci -s 00:02.0 f0.b=00,60
**#** setpci -s 00:02.0 f0.w
6000

```The first command writes to the register, the second returns the value of that register. See the man page for info on those commands. After setting the register I ran intel_gpu_top to check the actual clockspeed:

```

**#** intel_gpu_top
render clock: 166 Mhz  display clock: 200 Mhz
                     ring idle:  98%: &#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9611;                     ring space: 0/126976 (0%)
                          task  percent busy

                   Bypass FIFO:   0%:                      
              Color calculator:   0%:                      
                Intermediate Z:   0%:                      
                    Windowizer:   0%:                      
                  Pixel shader:   0%:                      
     Perspective interpolation:   0%:                      
                    Map filter:   0%:                      
                    Dispatcher:   0%:                      
                 Sampler Cache:   0%:                      
                     Filtering:   0%:                      
                        Map L2:   0%:                      
            Projection and LOD:   0%:                      
 Dependent address calculation:   0%:                      
         Texture decompression:   0%:                      
                 Texture fetch:   0%:                      
                  Setup engine:   0%:                      
               Strips and fans:   0%: 

```As you can see the render clock has been set to 166Mhz while the display clock remains at 200MHz, the rest of the output is not really important for us so I'll be trimming it out for the remainder of the commands.

```

**#** setpci -s 00:02.0 f0.b=31,05
**#** setpci -s 00:02.0 f0.w
0501
**#** intel_gpu_top
render clock: 200 Mhz  display clock: 200 Mhz

``````

**#** setpci -s 00:02.0 f0.b=33,05
**#** setpci -s 00:02.0 f0.w
0503
**#** intel_gpu_top
render clock: 250 Mhz  display clock: 200 Mhz

```Here is where I became more suspicious of the validity of the script as you can see that render clockspeed actually remains the same. I tested the register write coming from 00,60 and by that I mean copying how the script sets the clockspeed to 166MHz before setting any other clockspeed. The results were the same and I'm not sure why the script does this as, but again there is no explanation.

```

**#** setpci -s 00:02.0 f0.b=34,05
**#** setpci -s 00:02.0 f0.w
0500
**#** intel_gpu_top
render clock: 250 Mhz  display clock: 200 Mhz

```**Conclusion**

It may be that there is missing functionality in [FONT=Courier New]intel_gpu_top[/FONT] but it seems to me that most information out there is based on GMABooster, an undocumented program, and although the Intel datasheet states the clockspeed can reach 400MHz I haven't found a way to get it there or if I have prove it.

I also don't have any real understanding of PCI registers or the difference between the display clock and the render clock. If someone could share their knowledge of registers I'm sure that would shed a lot of light on this subject and coupled with information on the difference between the render clock and the display clock we might find a way to really solve this.

I eagerly await your input and RTFM links :)

It was tested by playing back a variety of videos, and using 3D applications like tuxracer and watching frames per second / cpu time.  It was a long time ago though, so I no longer have the details of the tests I ran.

The render clock slows down or speeds up graphics processing based on the clock setting.  It's underclocked to save power, if you increase the clock you will normally see an increase in 3D rendering in terms of frames per second (though it's not an enormous increase).

I tested it on an Asus Eee PC 1000HE for a few days before adding the capability to Jupiter.

---

### Post by agrh on 2011-03-01
Thanks for your input (fewt I assume), I know there's not really a logical place to publish tests like those and most users don't care.

Can you confirm that the render clock actually reaches 400MHz by writing to the register and if so how? The only tool I've found to check this is intel_gpu_top because I assume that most GPU driver programmers are familiar with reading datasheets and interpreting the results.

---

### Post by fuduntu on 2011-03-02
> **agrh said:**
> Thanks for your input (fewt I assume), I know there's not really a logical place to publish tests like those and most users don't care.

Can you confirm that the render clock actually reaches 400MHz by writing to the register and if so how? The only tool I've found to check this is intel_gpu_top because I assume that most GPU driver programmers are familiar with reading datasheets and interpreting the results.

I have only seen 166Mhz, 200MHz, and 250MHz. 166MHz is the default clock rate if I remember correctly.

I can play around with it later, and see what happens though.

---

