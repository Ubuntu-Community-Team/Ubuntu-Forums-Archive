---
title: "laptop feels hot"
date: 2012-08-25
forum: Hardware
---

### Post by stompinround on 2012-08-25
my laptop feels hot

way hotter than normal. fan is running but not very strong.. laptop shuts down if trying to do anything intensive.   

what can i do to help fan control be better

---

### Post by coldraven on 2012-08-25
Try opening a terminal and type ```
top
```
See if anything is hogging your processor (%CPU) and then post back.

Also, if the laptop is more than three years old the fan might need cleaning. I just did mine and it was half choked with fluff. It was fairly easy to do, just three screws to remove the keyboard and two more for the fan.

---

### Post by stompinround on 2012-08-25
k i did that

yet ubuntu will not allow me to copy it to post it back


i will keep trying

top - 04:22:44 up  1:13,  2 users,  load average: 0.48, 0.49, 0.70
Tasks: 161 total,   1 running, 160 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.7%us,  2.9%sy,  0.0%ni, 93.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4120460k total,  1362240k used,  2758220k free,   185716k buffers
Swap:  4191228k total,        0k used,  4191228k free,   574736k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1407 root      20   0  103m  85m  11m S    8  2.1  12:16.68 Xorg               
 2167 john      20   0  571m 134m  31m S    2  3.3  13:24.90 firefox            
 3887 john      20   0 97476  15m  11m S    2  0.4   0:01.55 gnome-terminal     
 1884 john      20   0  301m 122m  33m S    2  3.0   7:23.82 compiz             
 2947 john      20   0  470m  85m  23m S    1  2.1   7:23.05 plugin-containe    
 2040 john      20   0 42776  10m 8776 S    0  0.3   0:00.94 gtk-window-deco    
 3790 john      20   0  187m  19m  12m S    0  0.5   0:00.39 gnome-screensho    
 3951 john      20   0  2836 1164  880 R    0  0.0   0:00.59 top                
    1 root      20   0  3636 2040 1348 S    0  0.0   0:00.70 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.23 ksoftirqd/0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.09 watchdog/0         
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
   10 root      20   0     0    0    0 S    0  0.0   0:00.20 ksoftirqd/1        
   12 root      RT   0     0    0    0 S    0  0.0   0:00.05 watchdog/1         
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset

finally caught it but it did not like my coppying this


really thinking i should give up on comercial ubuntu and go back to something a bit more open source

my lappy is 4 years old, it is a sony laptop, the fan is rattling constantly sounds like a ford v6 running on 2 cylindars... in windows, it ranped up and sounded like it was killing aliens or something,... it does not ramp up at all in ubuntu... it always makes the same klik klik, 

it is a sony sz640e

---

### Post by whatthefunk on 2012-08-25
> **stompinround said:**
> finally caught it but it did not like my coppying this


really thinking i should give up on comercial ubuntu and go back to something a bit more open source

Has nothing to do with "commercial" Ubuntu....I can copy my top readout just fine.

Anyway, your top readout seems just fine.  Nothing hogging resources.

If your fan is making all sorts of noise, theres a high probability that your problems originates there.  Have a look at it to see if its clogged up or if there is something interfering with its motion.

---

### Post by stompinround on 2012-08-25
my fan make no noises at all running ubuntu


in vista (sorry i hate it, and my cd is scratched too much to restore) it goes from this klik klik everyday bs to like, a helocopter is decending on the house and darkness is here,chop chop....
it does not do this at all in linux, and if i try to launch anything intensive, the laptop shuts off and that is it... i have to reboot

\i do not dual boot


its linux or nothing, i just need it to work

---

