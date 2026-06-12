---
title: "CPU overheating"
date: 2012-07-21
forum: Hardware
---

### Post by DrAlbert on 2012-07-21
Hi
I installed ubuntu 12.04 64 bit and I think cpu is overheating anytime i power on the laptop. my laptop is lenovo y560 core i7 cpu (Graphic: ati radeon 5500).
I used cpufreqd to change the cpu frequency to 933MHz but it is still hot. it is hot even i don't do anything with it even when  splash screen is coming up I can hear fan works hard. I installed KDE XFCE Gnome and tried all of them plus unity 2D and 3D. no change happened. I disabled graphics effects but no changes happened. I don't know what should I do and why my Heavy windows 7 work queit and cool on this laptop but light linux cant?!

---

### Post by QIII on 2012-07-21
Did you install the proprietary AMD/ATI driver?

For some, this has helped with overheating.  Your fan is cooling both the card and the CPU.  The graphics card often runs much cooler in laptops when using the proprietary driver.

Go to the ATI wiki in my signature.  In the table of contents, find 

2.  Installation 

and under that 

2.  Using the Ubuntu repositories (alternate command line method, including hardware acceleration)

Click on that and you'll be taken to that section.

Don't bother with the hardware acceleration part at this point until we see if installing the proprietary driver will help out.

---

### Post by DrAlbert on 2012-07-21
thanks for reply! unfortunately I installed it before, via ubuntu additional driver. but it didn't help. there was two option. I installed that one that is not (post release updates).

---

### Post by QIII on 2012-07-21
When you installed it, did you do

```
sudo aticonfig --initial
```

before rebooting?

Could you also run 

```
top
```

In the terminal and post the results?

---

### Post by QIII on 2012-07-21
D'doh!  Double post.

---

### Post by Kreaninw on 2012-07-21
For me disable suspend fixed heating issue. Even latest AMD CCC 12.6 won't fix a thing when it come to heating issue. If you want to taste latest version instead of 12.4, this should help.

[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

---

### Post by QIII on 2012-07-21
In many cases, using the fglrx driver does, in fact, reduce overheating.

---

### Post by DrAlbert on 2012-07-21
I unistalled the driver today again and installed the latest version from its site and did the command "sudo aticonfig --initial" too. I noticed carefully and understood that ATI driver make my laptop 5 degree cooler than open source driver but its still hot.

top command result:
```
top - 22:10:53 up 37 min,  3 users,  load average: 0.34, 0.53, 0.72
Tasks: 246 total,   1 running, 244 sleeping,   0 stopped,   1 zombie
Cpu(s):  0.2%us,  0.3%sy,  0.0%ni, 99.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3980608k total,  2066904k used,  1913704k free,    95660k buffers
Swap:  9801368k total,        0k used,  9801368k free,   905120k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                            
 6316 root      20   0  293m  77m  55m S    1  2.0   1:53.27 Xorg                                                                                                                               
 6483 rahmani   20   0 1986m  82m  38m S    1  2.1   0:31.30 plasma-desktop                                                                                                                     
11360 root      20   0  425m  43m  31m S    1  1.1   0:02.73 ksysguard                                                                                                                          
11363 root      20   0 10000 1360  868 S    0  0.0   0:00.19 ksysguardd                                                                                                                         
    1 root      20   0 24556 2516 1376 S    0  0.1   0:02.37 init                                                                                                                               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                                           
    3 root      20   0     0    0    0 S    0  0.0   0:00.48 ksoftirqd/0                                                                                                                        
    4 root      20   0     0    0    0 S    0  0.0   0:00.83 kworker/0:0                                                                                                                        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                                        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.04 watchdog/0                                                                                                                         
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                                                        
   10 root      20   0     0    0    0 S    0  0.0   0:00.06 ksoftirqd/1                                                                                                                        
   12 root      RT   0     0    0    0 S    0  0.0   0:00.01 watchdog/1                                                                                                                         
   13 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2                                                                                                                        
   15 root      20   0     0    0    0 S    0  0.0   0:00.07 ksoftirqd/2                                                                                                                        
   16 root      RT   0     0    0    0 S    0  0.0   0:00.01 watchdog/2                                                                                                                         
   17 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3                                                                                                                        
   18 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/3:0                                                                                                                        
   19 root      20   0     0    0    0 S    0  0.0   0:00.08 ksoftirqd/3                                                                                                                        
   20 root      RT   0     0    0    0 S    0  0.0   0:00.01 watchdog/3                                                                                                                         
   21 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/4                                                                                                                        
   23 root      20   0     0    0    0 S    0  0.0   0:00.02 ksoftirqd/4                                                                                                                        
   24 root      RT   0     0    0    0 S    0  0.0   0:00.01 watchdog/4                                                                                                                         
   25 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/5                                                                                                                        
   26 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/5:0                                                                                                                        
   27 root      20   0     0    0    0 S    0  0.0   0:00.02 ksoftirqd/5                                                                                                                        
   28 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/5                                                                                                                         
   29 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/6                                                                                                                        
   30 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/6:0                                                                                                                        
   31 root      20   0     0    0    0 S    0  0.0   0:00.02 ksoftirqd/6                                                                                                                        
   32 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/6                                                                                                                         
   33 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/7                                                                                                                        
   34 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/7:0                                                                                                                        
   35 root      20   0     0    0    0 S    0  0.0   0:00.03 ksoftirqd/7                                                                                                                        
   36 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/7                                                                                                                         
   37 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                                                             
   38 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper    
```

---

### Post by QIII on 2012-07-21
Could you post the results of 

```
aticonfig --od-gettemperature
```

?

---

### Post by DrAlbert on 2012-07-22
this is the result. i added the result of "acpi -t" too. and these result happened just after 10 minute of running "thunderbird,google chrome,dolphin,konsole,system monitor"


```
rahmani@Qw0mlOIn:~$ aticonfig --od-gettemperature

Default Adapter - AMD Radeon HD 6570M/5700 Series
                  Sensor 0: Temperature - 54.50 C
rahmani@Qw0mlOIn:~$ acpi -t
Thermal 0: ok, 64.0 degrees C
```

---

### Post by Kreaninw on 2012-07-22
On Windows 7 64-bit compared to Ubuntu 12.04 LTS 64-bit, it's 5-10 degrees C cooler on Windows.

My GPU is HD5650, this is my result  :

```
Default Adapter - AMD Radeon HD 6500M/5600/5700 Series
Sensor 0: Temperature - 52.50 C
```

*Firefox and Transmision are running, air condition room.*

---

### Post by DrAlbert on 2012-07-23
thanks so there is no solution!

---

