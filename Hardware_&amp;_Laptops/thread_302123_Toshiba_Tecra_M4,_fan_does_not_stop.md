---
title: "Toshiba Tecra M4, fan does not stop"
date: 2006-11-18
forum: Hardware &amp; Laptops
---

### Post by mahmed on 2006-11-18
Hi all, 
  I'm having serious noise pollution from the cpu fan of the tecra m4.  Basically it doesn't stop. 

stats: I'm running ubuntu edgy (kubuntu 6.06)
```

> uname -a
Linux  2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

```

# the following acpi related modules are currently loaded 
```

> lsmod | grep acpi
toshiba_acpi           12224  0
pcc_acpi               14080  0
dev_acpi               12292  0

> lsmod | grep cpu
cpufreq_userspace       5408  0
cpufreq_stats           7744  0
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  0
cpufreq_ondemand        8876  1
cpufreq_conservative     8712  0

# as well as:
container               5632  0
button                  7952  0
battery                11652  0
ac                      6788  0
video                  17540  0
fan                     6020  0
processor              31560  2 speedstep_centrino,thermal

```

# checking the thermal zone we have
```

>cat /proc/acpi/thermal_zone/THRM/polling_frequency
<polling disabled>

```

and looking inito /proc/acpi 
"ls /proc/acpi/fan"  show that it is empty  and looking into the /proc/acpi/fan we have 

```

> cat /proc/acpi/toshiba/fan
running:                 1
force_on:                0

```

I've tried the toshset utility and it seems to make no difference 

```

> toshset -fan help
HCI error setting fan
valid settings are:
        (0) off
        (1) 1/4
        (2) 2/4
        (3) 3/4
        (4) high
        (5) on
        (6) low
fan: low

```

# the following 3 calls make absolutely no difference to to state of the fan, but i'm curious to find out what "HciFeature::query: received an unexpected response for feature fan: 192" means 
```

> toshset -fan 3
fan: low

> toshset -fan 2
HciFeature::query: received an unexpected response for feature fan: 192

> toshset -fan 4
fan: high

```

Anyhow, I'm inclined to to think there is a kernel bug somewhere but i cant identify it.  This machine used to be silent when in a previous incarnation it ran breezy. Currently i'm going deaf and slowly loosing my marbles with the acpi on the tecra m4.

From what i've googled there are acpi problems on toshiba, but i haven't found any fixes.   So if you have a "silent" and i'll settle for "it doesn't sound like you locked in a server room" or have come across this problem before,  please help.  

thanks, much appreciated
 mo

---

### Post by zgornel on 2006-11-18
I think you're running Dapper (Edgy=6.10). I have a Toshiba Sattelite Pro and no toshiba acpi related module and the fans behave normally (the processor is always at max frequency, no speedstep involved). Try removing toshiba_acpi module. I am only guessing here. ](*,)

---

### Post by 23meg on 2006-11-18
I have an M4 and it's an inherently noisy machine; noise is my only complaint about it.

In my use, when CPU temperature drops in idle operation due to ambient temperature and lack of CPU load, the fan stops. This means the fan is controlled as it should be by the kernel, but the machine, due to its construction, runs hot. Is that the case for you?

---

### Post by mahmed on 2006-11-18
Hi **zgornel**, my mistake, yes it is (Edgy=6.10).  I have tried dropping the module but till no change...

I had also assumed that the cause was the cpu maxing out. I used the cpufreq governor to change the mode to "powersave" earlier, as below 
```

> cpufreq-set -g powersave

```
 
and currently "cpufreq-info" returns:

```

> cpufreq-info

cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: centrino
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.06 GHz, 800 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 800 MHz and 1.73 GHz.
                  The governor "powersave" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).

```

and according to the output its running at 800MHZ, its lowest frq. but it doesn't seem to make a difference.

Hi, **23meg**, yes, it seems that they are inherently noisy, however, from previously running breezy, i'm inclined to think this is more that the machines temperament. 

Somehow it doesnt appear that my machine knows "idle" mode.... That fan starts bursting as the kde desktop loads, and doesn't stop -- i've tried ubuntu and xubuntu, thinking that kde was using more resources, but it made no difference. 

I left my machine running idle yesterday, and the fan noise when i came back 6 hours later was as loud as when i left.  

wrt running, it just unusable when i run processor intensive work. Watching a dvd led to a cpu temp of +90 deg c. and required the use of headphones it hear the speach.  The keyboard area around the escape key (directly above the fan) which i assume is where the cpu is located was simply untouchable.

Btw.  which version of ubuntu/kernel are you running and what is your "lsmod | grep acpi"  return. 

thanks again to both you 
 mo

---

### Post by mahmed on 2006-11-18
btw. 
 currently as well the kde desktop i'm running firefox and emacs and the acpi output is:

```

> acpi -V
     Battery 1: charged, 100%
     Thermal 1: ok, 66.0 degrees C
  AC Adapter 1: on-line

```

---

### Post by 23meg on 2006-11-18
I'm using Edgy with the generic kernel.```
$ lsmod | grep acpi
toshiba_acpi           12224  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
dev_acpi               12292  0 
asus_acpi              17688  0
```

---

### Post by mahmed on 2006-11-18
thanks 23meg, 
 looks like i'll have to deal with it.  If i find anything intersting or that works, i'll post it 
 -

---

### Post by 23meg on 2006-11-24
I'm more or less convinced everything is acting as it should and this is just how the machine operates. Mine has never gone up to a temperature like 90 Celcius though; the highest I've seen is 78, at which the fan spins at its fastest. You may want to check whether your fan is clogged with dust or there's something else going wrong with the cooling system of your laptop.

---

### Post by mahmed on 2006-12-05
hey 23.  I dont understand it either, no dust or blockage currently we have .. 

```

 > acpi -V
     Battery 1: charged, 100%
     Thermal 1: ok, 89.0 degrees C
  AC Adapter 1: on-line

```

making the area around the 'esc' key too hot to literally touch for more than a few seconds

---

### Post by 23meg on 2006-12-07
89 is really over the top; sure, the M4 runs hotter than most similar machines, but in my fifteen months of use I've never even seen 80 and I've done long CPU-heavy renders on it. I suggest you take it to service.

---

### Post by mahmed on 2006-12-10
Hi 23,  
  Just an update, as  a last ditch attempt, i knew that the breezy-badger distribution was silent and hot pipping hot. Anyhow to test, i downloaded a copy and dist-upgraded to dapper[drake(6.06)]. 

 Anyhow the dist-upgrade has left me with a running machine that is not scolding my hand or making me deaf !!! -- 

Tried a new live-cd again to double check - and had the same old problems... it seems that on my machine at least breezy->dapper[drake] dist-upgrade works but dapper-[edgy(6.10)] from the live cd doesnt 

-- 
thanks

---

