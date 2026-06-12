---
title: "Added emifreq and now my system overheats"
date: 2005-08-07
forum: Hardware &amp; Laptops
---

### Post by Magneto on 2005-08-07
Okay I installed emifreqd and its running and it scales but only to powersaving mode which Im thinking is a bug in the 0.17 version that hoary repos carry. My lattitude c640 with p4 M 2ghz has never overheated before today- got so bad the memory started to fail. Sitting and using firefox the default setting which im guessing is the ondemand  - set the cpu at 2ghz and as I watched the applet it climbed its way to 80 degrees celsius so I enabled the powersaving profile and cut the cpu to 1.2ghz and now 5 minutes later it is at 65 degrees 

why is this thing acting up? no background processes using up resources etc so I dont know whats going wrong. I tried the emifreqd author's site but there isnt alot of detail. Im about to just get rid of it and use the default scaling that Ubuntu uses which on my system seems to be always 1.2ghz. The reason I installed emifreqd is that my system would not scale up when needed for compiling an app lets say or some form of multitasking.

any ideas??????????

im about to just uninstall it
I tried cpufreq but there's no control app just the config file and when powernowd was removed cpufreqd didnt load the required modules like speedstep_lib and cpu_powersave

---

### Post by Magneto on 2005-08-08
[QUOTE=Magneto]Okay I installed emifreqd and its running and it scales but only to powersaving mode which Im thinking is a bug in the 0.17 version that hoary repos carry. My lattitude c640 with p4 M 2ghz has never overheated before today- got so bad the memory started to fail. Sitting and using firefox the default setting which im guessing is the ondemand  - set the cpu at 2ghz and as I watched the applet it climbed its way to 80 degrees celsius so I enabled the powersaving profile and cut the cpu to 1.2ghz and now 5 minutes later it is at 65 degrees 

why is this thing acting up? no background processes using up resources etc so I dont know whats going wrong. I tried the emifreqd author's site but there isnt alot of detail. Im about to just get rid of it and use the default scaling that Ubuntu uses which on my system seems to be always 1.2ghz. The reason I installed emifreqd is that my system would not scale up when needed for compiling an app lets say or some form of multitasking.

any ideas??????????

im about to just uninstall it
I tried cpufreq but there's no control app just the config file and when powernowd was removed cpufreqd didnt load the required modules like speedstep_lib and cpu_powersave[/QUOTE]
 well I scrapped emifreq and now powernowd is scaling the processor in userspace mode better so..........................no more heat issues.
On the plus side I ended up rebooting my wireless ap and low and behold 500kbps up from a max of about 300, so a little golden lining, I hadn't noticed any connectivity issues before so I never thought the troughput was off. Surprise.

---

### Post by l.tambiah on 2006-06-24
[quote=Magneto]well I scrapped emifreq and now powernowd is scaling the processor in userspace mode better so..........................no more heat issues.
On the plus side I ended up rebooting my wireless ap and low and behold 500kbps up from a max of about 300, so a little golden lining, I hadn't noticed any connectivity issues before so I never thought the troughput was off. Surprise.[/quote] 

hmm, strange emifreq works with no issues on my machine but im using dapper with 0.18 release installed using apt-get.

---

