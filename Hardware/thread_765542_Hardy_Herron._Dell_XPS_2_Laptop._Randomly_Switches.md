---
title: "Hardy Herron. Dell XPS 2 Laptop. Randomly Switches off with new 8.04!"
date: 2008-04-24
forum: Hardware
---

### Post by B3Nji on 2008-04-24
Hey Guys and Gals,

Back in the day when 8.04 was in alpha, I gave it a try. But found that when using it my computer would randomly switch its self off. I thought it was still in testing and the problem would be fixed when it comes out. So I went back to Gutsy. Which works flawlessly btw, fast and amazing as Ubuntu is normally for me :). Anyway, I installed the RC version two days ago, the same thing happens! Its as if I have told my laptop to shut down. I can be doing anything from listening to music, browsing the web. Or just watching a movie. It happens quickly if I'm watching a video now I think about it. Which leads me to be thinking overheating? But how could that happen with an upgrade.. something must have changed in the kernel and disagrees with my laptop? I'm probably wrong. Ill leave it to the more experienced people to work that one out.

I have been using Ubuntu since Breezy Badger for my primary OS and never had any problems. 

BTW I have a separate home and / partitions so when I update to any other version its a fresh install except my home one. 

Anybody got any ideas of what's cracking off? I'm thinking I will have to downgrade to gutsy at this rate. :(

Thanks for your help.

---

### Post by BlueColibri on 2008-04-26
Hello I have the same problem on my Dell XPS 2 Laptop and I figured this much out I use two rt kernels and 1 generic kernel

the kernels I use are
2.6.24-16-rt                        shuts down
2.6.24-16-generic                   shuts down
2.6.24-7-rt                         doesn't shuts down

I don't know why exactly but I think That the cpu thinks that it is overheating in the above kernels except for the one below I figured this out by the system monitor beceause the cpu usage was not that high it's a bug in some kernel versions that the ubuntu people patched I also have a other bug that is that I can use only my nvidia new glx driver in the generic kernel and not in the rt kernels when I boot up in de rt kernels the only thing that it shows is the ubuntu usplash screen and afther that a blinking cursor in the right upper corner of my screen maybe we can help euch other out

---

### Post by stupid_user on 2008-04-27
Just another Dell XPS Gen 2 owner here with the same issues.  I have a laptop cooling fan under laptop, and using hddtemp shows that at least the hard drive is not overheating.  

Its kind of annoying when you laptop turns off every few minutes.  I reinstalled hardy, and while installing new software it died.  I really like Hardy when its working.  But this is just making it unusable.  

I do remember having this problem with windows xp as well.  Well I guess its time to try  some of those other distros I keep hearing about.  Either that or go back to Gutsy.

---

### Post by yodenss on 2008-05-01
I also have this issue; it occurs when an application uses 100% CPU for periods of time.

Gutsy had no issues.  If the fans were run at a higher speed, the system would be fine.  Unfortunately, I can't seem to find a way to convince them to do this...

Thing I've tried:
dellfand: runs, but doesn't seem to effect fan velocity.  The fans run faster when THM reaches 100 C just as before.
lm-sensors: doesn't detect fans
ksensors: doesn't really have anything useful anyway

Possible solution:
1) install i8kutils
2) run i8kmon
3) middle click (forces them into 'high speed'

while this doesn't actually force them into the highest speed, it is higher than I was able to force them to go using anything else.  Unfortunately, it seems that the fans slow down slightly.  At least, if I wait a few minutes and click again there is audible speedup...

So, here is my ugly ugly hack:
Run from the command line every 5 seconds:
```
i8kctl fan 2 2
```

Python script to do this:
```

#!/usr/bin/env python

import time
import os

while True:
    os.popen("i8kctl fan 2 2")
    print "sleeping 5"
    time.sleep(5)

```


So far, I've been watching WC3 dota AI play, and CPU temps are under 90.  I'll post again after I play a game or two to let you guys know if this actually prevents the shutdown.

---

### Post by yodenss on 2008-05-01
Here is a fancier script which should allow more reasonable control.  Usage:
```
./XPS poll_rate cpu_low_temp cpu_high_temp gpu_low_temp gpu_high_temp
```

Save this into a file XPS.py, make it executable using chmod +x XPS.py

```
#!/usr/bin/env python

import time
import os
import sys

if len(sys.argv) != 6:
    print "Requires 5 integer arguments, e.g. ./XPS 5 55 75 75 90"
    print "First is refresh interval"
    print "Second is CPU temp to turn on low speed"
    print "Third is CPU temp to turn on high speed"
    print "Fourth is GPU temp to turn on high speed"
    print "Fifth is GPU temp to turn on high speed"
    sys.exit()

sleep,low,high,glow,ghigh = [ int(a) for a in sys.argv[1:6] ]

speed = 2   #default to max speed

try:#catch interrupt; don't quit with fans off!
    while True:
        #first get CPU temp
        #i8k driver uses format:
        #1.0 A05 XXXX 41 2 2 115260 126090 -1 -22
        #? biosrev servicetag cputemp fan1speed fan2speed fan1rpm fan2rpm ? ?
        output = os.popen("cat /proc/i8k").read()
        temp = int(output.split(" ")[3]) #so temp is 4th element

        #now get GPU temp
        #magic regex; entirely dependent on format of nvidia-settings
        output = os.popen("nvidia-settings -q gpucoretemp |"\
            "grep '):' | awk '{print $4}'").read()
        gtemp = int(output[:2])

        if temp < low and gtemp < glow:
            speed = 0
        elif temp < high and gtemp < ghigh:
            speed = 1
        else: speed = 2

        os.popen("i8kctl fan %d %d"%(speed,speed))

        #sleep
        print "Sleeping for %d..."%sleep
        time.sleep(sleep)

except:
    if speed == 0: speed = 1 #don't quit with it off
    os.popen("i8kctl fan %d %d"%(speed,speed))  #otherwise leave it
    print "Quitting, fan speed at %d %d"%(speed,speed)
```

Disclaimer:  Playing with fan settings could damage your laptop.  I am not responsible.  Also, This script requires i8kutils, the i8k kernel module to be running, and nvidia-settings.

---

### Post by slade208 on 2008-05-17
All,

Aside from having this same problem I do like the new release of Ubuntu. Has anyone been able to confirm a workaround for our XPS ge n 2 overheat random shutdown?

---

### Post by BlueColibri on 2008-05-17
Hello slade208 what do you mean, the only thing I did is writing a litlle program in C# for activating my fan's sooner and there is a other thing you could do but it's not safe to do that is adjusting your trip_points file from the standard 99°C shutdown point to a higher point but it's not wise to do so

---

### Post by slade208 on 2008-05-17
oh I was just saying that I do have the same problem but only in hardy heron. My xps shuts off after a period of time and when I boot it backup it says it's because of overheat.

I did a little test last night which helped me pin the problem a little and that was to disable the restricted nvidia drivers ( I have a nvidia go6800). I was able to use hardy without the random temperature shutdown. If can figure it out I think I will try a different nvidia driver since ubuntu without 3dfx is not cool.

---

### Post by BlueColibri on 2008-05-21
Hi everybody I fixed the problem for me what I did is select the package cpufreqd in synaptic package manager and deselecting powerdownd if it doesn't by it self and the problem was gon

---

### Post by BlueColibri on 2008-05-21
Hi everybody with the package cpudyn it works even beter for me please tell me your findings

---

### Post by Shanghai on 2008-06-18
> **BlueColibri said:**
> Hi everybody with the package cpudyn it works even beter for me please tell me your findings

I have overheating problems on 2.24.19 that causes it to shut down. Installing cpudyn brought the computer to a crawl I had to uninstall it.
I have never had this problem before and I have been running Ubuntu since Dapper and a number of other distros on my XPS gen2 Inspiron.
I might have to start distro hopping again before I burn up my computer.

---

### Post by kpkeerthi on 2008-06-18
Sorry about the problem, guys.

Running Hardy on my Dell Inspiron XPS Gen 2 laptop. No problems here. Running hardy since RC1. 

I have temp monitors running. I find nothing unusual. I'm able to watch movies, play audio and do everything just fine.

---

### Post by Shanghai on 2008-06-18
> **kpkeerthi said:**
> Sorry about the problem, guys.

Running Hardy on my Dell Inspiron XPS Gen 2 laptop. No problems here. Running hardy since RC1. 

I have temp monitors running. I find nothing unusual. I'm able to watch movies, play audio and do everything just fine.

I think I actually started in Beta and the problems started after stable?
In the Beta I couldn't run Desktop effects (KDE4) so I have turned them off now to see if it helps.
Its the GPU that gets hot the CPU is just fine. I can't measure the GPU temp in Linux even running Gkrellm but in Windows XP i can using the I8k equivalent for Windows. No problems in XP by the way.

---

### Post by kpkeerthi on 2008-06-18
> **Shanghai said:**
>  I can't measure the GPU temp in Linux

If you have nvidia binary driver, here is the command to get the GPU temp
```
nvidia-settings -q gpucoretemp
```

The output would look like
```

**  Attribute 'GPUCoreTemp' (DELL-XPS-G2:0.0): [COLOR="Blue"]46[/COLOR].**
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.

```

The line highlighted shows my GPU temp (46 degrees)

---

### Post by Shanghai on 2008-06-18
Thanks that's a good tip.

Attribute 'GPUCoreTemp' (Novascape:0.0): 95.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.

It looks like I could fry an egg on my GPU!

The CPU only reads 51.

Something is not right.

---

### Post by BlueColibri on 2008-06-23
Hello Shanghai sorry about the cpudyn thing it was a mistaketo post that  but with cpufreqd I have no problems what so ever what are your findings

---

