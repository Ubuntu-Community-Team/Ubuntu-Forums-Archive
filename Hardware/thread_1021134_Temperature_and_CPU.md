---
title: "Temperature and CPU"
date: 2008-12-25
forum: Hardware
---

### Post by Mostly Harmless Eccentric on 2008-12-25
I'm running Intrepid on an HP dv6000. I am always making totally sure to keep the vents unobstructed, and yet both CPUs are always at 100% use, and the temperature hovers around 80 degrees C and even higher. The fan is on, it sounds like full power, all the time. 

Oddly enough, this seems to have no effect on performance, but I'm concerned about my hardware. It has shut down because of this a couple times now, and nothing I do seems to affect it, even when nothing is running. I disable things, no effect. It's even to hot to touch the bottom of the machine sometimes. What can I do about this?

I'm pretty sure this has been a chronic problem, I believe I remember a similar issue with Hardy.

---

### Post by jrusso2 on 2008-12-25
I find it strange that you CPU is maxed.  Run top in your terminal and see what is using all that CPU.

You can paste the output here. if you don't understand

---

### Post by rmausser on 2008-12-25
I have this exact same problem on a Compaq v2000, no ports blocked, cpu super hot, and always running at 100%.

I will post "top", but just wanted to say that while the CPU always says 100%, the applications running only add up to about 10% on idle, yet the total always equals 100%.

This happened after upgrading to 8.10.

Please help, my computer will probably explode after doing this long enough.

---

### Post by rmausser on 2008-12-25
OK heres System Monitor, top and htop results for me



Top

top - 02:05:13 up 7 min,  2 users,  load average: 3.58, 2.84, 1.40
Tasks: 108 total,   3 running, 105 sleeping,   0 stopped,   0 zombie
Cpu(s): 74.4%us, 24.6%sy,  0.0%ni,  0.0%id,  0.0%wa,  1.0%hi,  0.0%si,  0.0%st
Mem:    904304k total,   612028k used,   292276k free,    17244k buffers
Swap:  2441840k total,        0k used,  2441840k free,   371832k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5950 rinnie    20   0  8144 5156 2200 S 27.3  0.6   1:33.85 gconfd-2           
 5314 root      20   0  178m  43m 6752 S 11.3  4.9   0:36.06 Xorg               
 5849 rinnie    20   0 24672 5364 4332 S  2.7  0.6   0:08.37 x-session-manag    
 5942 rinnie    20   0  2904 1136  640 S  2.0  0.1   0:07.28 dbus-daemon        
 6062 rinnie    20   0 22612  13m 7816 S  1.3  1.5   0:05.58 metacity           
 6091 rinnie    20   0 25504  12m 7396 S  1.3  1.4   0:03.02 python             
 9279 rinnie    20   0 54008  17m  10m R  1.3  2.0   0:01.02 gnome-terminal     
 9435 rinnie    20   0  192m  61m  22m S  1.3  7.0   0:14.30 firefox            
 5310 root      20   0 19428 4752 3564 S  0.7  0.5   0:00.36 gdm                
 6013 rinnie    20   0  5560 2172 1832 S  0.7  0.2   0:00.72 gvfsd              
 6093 rinnie    20   0 35244  12m 7548 S  0.7  1.4   0:00.48 cairo-dock         
 6118 rinnie    20   0 45324 9460 7756 S  0.7  1.0   0:01.26 nm-applet          
 6361 rinnie    20   0 17596 8816 2528 S  0.7  1.0   0:03.46 python             
15744 rinnie    20   0 15104 4728 3888 R  0.7  0.5   0:00.02 metacity           
    1 root      20   0  2920 1712  564 S  0.0  0.2   0:01.22 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 kblockd/0          
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  123 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  161 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  162 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  163 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0            
  204 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0              
 1469 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd      
 1472 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd              
 2239 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0              
 2241 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux            
 2478 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 kjournald          
 2688 root      16  -4  2668 1160  400 S  0.0  0.1   0:00.38 udevd              
 2996 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused          
 3002 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 pccardd            
 3188 root      15  -5     0    0    0 S  0.0  0.0   0:03.70 b43                
 4454 root      20   0  1780  536  468 S  0.0  0.1   0:00.00 


screenshots of system monitor and htop are attached.

PLEASE help me, this is a computer I use for work and it gets very hot and stays at 100% all the time, 24/7... something tells me this isnt good for the CPU.

---

### Post by Mostly Harmless Eccentric on 2008-12-25
There we go! I'd checked out top last night before posting and hadn't spotted the culprit because it kept moving around in the list. But coming back to it refreshed, I noticed Boinc was running for no particular reason and occupying a good 95ish % of one of the CPUs. I killed the process, CPU problem solved. The temperature still looks kinda hot, though. It gets up to 70-some odd quite a bit, and I can hear the fan on low. Better, but I'm still not sure. Anyone know what kind of temperature levels I should be looking at?

---

