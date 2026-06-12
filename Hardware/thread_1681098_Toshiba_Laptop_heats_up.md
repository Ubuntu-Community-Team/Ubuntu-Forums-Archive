---
title: "Toshiba Laptop heats up"
date: 2011-02-03
forum: Hardware
---

### Post by yogeshp08 on 2011-02-03
Hello,

I recently installed Ubuntu 10.10 on my Toshiba L505-S5971.
I dual boot Ubuntu with Windows 7.

I have been using Ubuntu all the time. And for no reason the systems heats up on Ubuntu. It never did the same on Windows. I cannot figure out why. What might be wrong?

Please help. Thanks

---

### Post by agnibhu on 2011-04-06
Hi,

I also have this problem.
I'm using Dell 1440.
**uname -a**
Linux dell 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux

**less /proc/cpuinfo**
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     T6500  @ 2.10GHz
stepping    : 10
cpu MHz        : 1200.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dts
bogomips    : 4188.93
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     T6500  @ 2.10GHz
stepping    : 10
cpu MHz        : 1200.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dts
bogomips    : 4189.45
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:


I'm not sure what to do .
Is there any generic way we can tackle this issue. I'm ready to invest some time on this. If some one can guide me I can try to figure it out.

---

### Post by scorpio2002 on 2011-04-06
I an unlucky onwer of a Toshiba laptop (U500-10V). I've always had overheating issues since I bought it. I have recently found out that this is due to a buggy Windows-specific BIOS table that they install on their laptops.

I don't know if that is your specific problem, but it is clear to me that Toshiba wants to prevent Linux users from using their laptops.

I'm currently looking for a new laptop because I'm fed up with Toshiba!

---

### Post by agnibhu on 2011-04-17
Hi,

I wonder why nobody seems to be care about these issues. What is the need of releasing new versions of ubuntu without solving these basic needs. I'm myself a software engineer. I can try to solve this issue if some one guides me. 

Actually I like Ubuntu very much, thats why I stick to this even after this heating problem persists. But we solve it right ?

I think we should focus more about these issues than making the ubuntu more fancier or some thing like that.

---

### Post by rvchari on 2011-04-17
> **agnibhu said:**
> Hi,

I wonder why nobody seems to be care about these issues. What is the need of releasing new versions of ubuntu without solving these basic needs. I'm myself a software engineer. I can try to solve this issue if some one guides me. 

Actually I like Ubuntu very much, thats why I stick to this even after this heating problem persists. But we solve it right ?

I think we should focus more about these issues than making the ubuntu more fancier or some thing like that.

some processes in ubuntu seem to be behaving like a runnaway processes... my laptop heats up whenever i run some specific process.
one of them is as simple as gnome appearance that has to be always tracked by pid using top or conky (i use conky exclusively for this !) and then kill the runnaway pid (one pid is used by gnome appearance and another is paralelly created with pid number as (pid)+1. i have to kill the +1 process to bring the laptop temp back to normal.

another one is when i use clamtk to scan my pendrive or something like that...

does ubuntu forum staff notice these things ? or is it a bug only i am facing ?

i am using t500 lenovo laptop and i havent had these issues since i started using it exhaustively... but such bugs started since past few months.... which i keep track and kill the process to control the temp in normal.

abnormality is so high that a laptop running at 40 to 45 deg C shoots up beyond 80 in just a few seconds !!! i have to be really fast to kill the process to protect my laptop !
the instant i do my bit, temp is brought in control in another few seconds !

---

### Post by agnibhu on 2011-04-17
thanks rvchari for a quick response.
But I couldn't understand the 'top technique'. I've pasted the output of the top command on my machine. Can you figure out anything reasonable ?

Thanks and Regards......


top - 20:39:21 up 12 min,  2 users,  load average: 0.05, 0.18, 0.16
Tasks: 175 total,   1 running, 174 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.6%us,  1.6%sy,  0.0%ni, 96.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3060500k total,   896568k used,  2163932k free,    75348k buffers
Swap:  2047996k total,        0k used,  2047996k free,   398120k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                       
 1381 root      20   0 73992  30m  12m S    2  1.0   0:21.91 Xorg                          
 2167 deepud    20   0  341m  78m  31m S    1  2.6   0:35.34 firefox-bin                   
 2287 deepud    20   0 93948  13m  10m S    1  0.5   0:01.80 gnome-terminal                
 2311 deepud    20   0  176m  62m  35m S    1  2.1   0:14.44 software-center               
   57 root      20   0     0    0    0 S    0  0.0   0:00.40 kondemand/0                   
 1802 deepud    20   0 99740  11m 8592 S    0  0.4   0:00.55 gnome-settings-               
 1822 deepud    20   0 73456  26m 9732 S    0  0.9   0:05.23 compiz                        
 1889 deepud    20   0  3908  916  732 S    0  0.0   0:00.33 syndaemon                     
 1935 deepud    20   0 76692  12m 9.8m S    0  0.4   0:02.43 sensors-applet                
 2395 deepud    20   0  2620 1144  840 R    0  0.0   0:00.06 top                           
    1 root      20   0  2888 1708 1244 S    0  0.1   0:00.74 init                          
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                      
    3 root      20   0     0    0    0 S    0  0.0   0:00.08 ksoftirqd/0                   
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                   
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0                    
    6 root      RT   0     0    0    0 S    0  0.0   0:00.70 migration/1                   
    7 root      20   0     0    0    0 S    0  0.0   0:00.03 ksoftirqd/1                   
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1                    
    9 root      20   0     0    0    0 S    0  0.0   0:00.07 events/0                      
   10 root      20   0     0    0    0 S    0  0.0   0:00.01 events/1                      
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset                        
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper                       
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 netns                         
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr                     
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 pm                            
   17 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers                   
   18 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default

---

### Post by rvchari on 2011-04-17
> **agnibhu said:**
> thanks rvchari for a quick response.
But I couldn't understand the 'top technique'. I've pasted the output of the top command on my machine. Can you figure out anything reasonable ?

Thanks and Regards......


top - 20:39:21 up 12 min,  2 users,  load average: 0.05, 0.18, 0.16
Tasks: 175 total,   1 running, 174 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.6%us,  1.6%sy,  0.0%ni, 96.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3060500k total,   896568k used,  2163932k free,    75348k buffers
Swap:  2047996k total,        0k used,  2047996k free,   398120k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                       
 1381 root      20   0 73992  30m  12m S    2  1.0   0:21.91 Xorg                          
 2167 deepud    20   0  341m  78m  31m S    1  2.6   0:35.34 firefox-bin                   
 2287 deepud    20   0 93948  13m  10m S    1  0.5   0:01.80 gnome-terminal                
 2311 deepud    20   0  176m  62m  35m S    1  2.1   0:14.44 software-center               
   57 root      20   0     0    0    0 S    0  0.0   0:00.40 kondemand/0                   
 1802 deepud    20   0 99740  11m 8592 S    0  0.4   0:00.55 gnome-settings-               
 1822 deepud    20   0 73456  26m 9732 S    0  0.9   0:05.23 compiz                        
 1889 deepud    20   0  3908  916  732 S    0  0.0   0:00.33 syndaemon                     
 1935 deepud    20   0 76692  12m 9.8m S    0  0.4   0:02.43 sensors-applet                
 2395 deepud    20   0  2620 1144  840 R    0  0.0   0:00.06 top                           
    1 root      20   0  2888 1708 1244 S    0  0.1   0:00.74 init                          
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                      
    3 root      20   0     0    0    0 S    0  0.0   0:00.08 ksoftirqd/0                   
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                   
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0                    
    6 root      RT   0     0    0    0 S    0  0.0   0:00.70 migration/1                   
    7 root      20   0     0    0    0 S    0  0.0   0:00.03 ksoftirqd/1                   
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1                    
    9 root      20   0     0    0    0 S    0  0.0   0:00.07 events/0                      
   10 root      20   0     0    0    0 S    0  0.0   0:00.01 events/1                      
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset                        
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper                       
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 netns                         
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr                     
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 pm                            
   17 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers                   
   18 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default


in a nut shell, (eventhough i am not a linux guru or for that matter an ubuntu geek) i observed that the top command lists the processes in decending order (highest mem / cpu % usage is listed topmost. i note down the pid and spent some time to read on. notice the sequence. in ur case its Xorg on top listed as of time you copied / pasted.

PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                        
 1381 root      20   0 73992  30m  12m S    2  1.0   0:21.91 Xorg                           

i cant decipher whats PR, NI, VIRT, RES, SHR, S
i notice the pid which is 1381, %CPU2, %MEM is 1.0 and name (command) thats Xorg.
you cant do anything to this as this is essential process to run X

in my case whenever the runaway processes occur, it shoots upwards to top place (but natural, user will be me and not root) and % MEM shoots up which inturn burns up the laptop by increasing the temp.

i issue the command "kill PID" without quotes in the terminal where PID is the number (1381 in the above example). once i issue this command... fan comes to normal speed, temp is restored to normalcy and i can work....

the latest bug i found is this.... apt-get command starts whenever it thinks to screw my temp and shoots up... i have to issue "sudo kill PID" in terminal as apt-get isnt controled by user.... why this ? when i never touch that command unless and until i wish to remove or install a package ? or update or upgrade ? funny but this is happening....

still i am happy that ubuntu helps me identify the black sheep and bring things back to normal... (i had been using windows and windows at times used to hang... was this case occuring there too ? i dont know coz i dont have any idea on how to identify ! so i quit using windows and am a happy ubuntuer... since jaunty !)

---

### Post by rvchari on 2011-04-17
i forgot to add that in my case, gnome-appearanc and apt-get are the two black sheep that shoots up the temp beyond 70 and 80 ( in gnome-appearanc case, i dont let it go beyond 50 as i keep the kill command ready  ) in apt-get case, i notice only if i track the temp (which is displayed b conky)

---

### Post by timesarehard4dreamers on 2011-04-17
For those with Toshiba laptops, try using toshset commands to enable fan use in Ubuntu.

---

### Post by Yellow Pasque on 2011-04-17
> **agnibhu said:**
> I wonder why nobody seems to be care about these issues.

Ubuntu can't fix mobo/system manufacturers' buggy BIOS implementations.  You're better off voicing your need for Linux support to them than Canonical. Or better yet, support Linux vendors like System76.

Side note: I kind of feel guilty about getting an HP laptop, even though they're one of the better manufacturers when it comes to stuff working in Linux. I did get a great deal on it though, and I needed a laptop in a pinch while I was living in my car (LOL @ my priorities).

---

### Post by agnibhu on 2011-04-18
hmm..So the BIOS might be the culprit here ?...
I think we don't have control over the BIOS right ?

---

### Post by rvchari on 2011-04-18
> **agnibhu said:**
> hmm..So the BIOS might be the culprit here ?...
I think we don't have control over the BIOS right ?

may be... cant conclude...
coz i havent updated or changed my bios... but i did face problems over a period of time and am still facing it. thanks to top and conky, i can keep track of whats going on so i can do my "kill" at will !!!

wonder whats bugging, may be some updates ? cant say coz i didnt keep exact track of when i started facing this heating due to some runaway processes...

but yes, i have read in some thread that toshiba users did face this heatup problem and that the fan speed control has to be done or something like that. try searching with similar keywords in forum, you may come across that thread..

---

