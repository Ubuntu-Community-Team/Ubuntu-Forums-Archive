---
title: "Ubuntu 9.04: Laptop gets very hot - Dell XPS M1530"
date: 2009-06-29
forum: Hardware
---

### Post by arpan on 2009-06-29
Hi,

I have a Dell XPS M1530 and everything works well except the laptop gets very hot when run for more than 30 mins. In pre-installed Vista this does not happen. Especially the part where the hard-disk is, gets the hot.

Any solution for this?

---

### Post by jpepin on 2009-07-12
I'm having the same issue.  Laptop came preinstalled with Vista, and never gets hot.  Running Ubuntu 9.04, it gets hot quickly.  The fan seems to take a while to turn on, although I'm not sure if it comes on any quicker in Vista.  Any help?

---

### Post by sonu 1807 on 2009-07-12
In taskbar right click at any blank space and then from add to panel select CPU frequency monitor.To enusre that the laptop runs cool click it and select powersave in place of ondemand.

In terminal you can type sudo apt-get install lm-sensors sensors-applet hddtemp. After installation is complete reboot and then from add to panel select Hardware Sensors Monitor. It will constantly inform you about CPU temperature

---

### Post by jpepin on 2009-07-12
Thanks for the suggestion.  

I noticed that the powernowd application was "checked" in system>admin>services, but was not actually installed in my default Jaunty install (upgraded from Intrepid).  After some research, I decided to install cpudyn in its place (still unsure which is better: powernowd, cpudyn, or cpufreqd).

Once I did that, and followed your suggestion, it seems to have helped with my heat situation.  

I'll let you know if it becomes a problem again, and we can re-address the issue.

---

### Post by DesktopDefender on 2009-07-13
Hi Folks,

I am also the owner of a XPS M1530 I seem to be having a similar issue where my fan is spinning like crazy and all I have open is firefox with 3 tabs & thunderbird.

I installed hddtemp, set the power option to powersave both processors are running at 31% or 800Mhz

installed the sensors app and my cpu is running at 37 and hdd is running at 37 and but the fan is going like mad, just starts spinning for a couple pf minutes at a time.

While I have been writing this post the temp gauge on the CPU and HDD has increased to 51 on each

is this normal behavior for the hardware 
am I doing damage to the inside of the laptop at this temp..?

Any additional information would be greatly appreciated 

Thanks

---

### Post by jpepin on 2009-07-13
DesktopDefender: have you tried anything other than hddtemp?  Through my very unscientific trial and error method, I've found that some apps work better than others.

I just switched to cpufreqd (from powernowd) and tweaked the config file to my taste.  All seems to be working well for now.

---

### Post by DesktopDefender on 2009-07-14
Hi jpepin,

I havent to be honest(very new to linux), as soon as I get an hour of free time, I will try.

I have done some research about the temp readings that I am getting, it seems to be normal enough, however at the rate that the fan rotates, ill be replacing it by the end of the summer :-(

Thanks for the input

D.D.

---

### Post by GoldenSun on 2009-07-14
I have this problem also.  But I do not think it is all ubuntu's fault.  I had a part replaced in it and I was talking to the guy.  He said that they are releasing a service code for overheating for the ones with the m8600 installed in them.  They will take it and replace the mobo with a new one from a different manufacturer.  

And get a nice conky script to see all stats.

---

### Post by jpepin on 2009-07-14
> **DesktopDefender said:**
> Hi jpepin,

I havent to be honest(very new to linux), as soon as I get an hour of free time, I will try.

I have done some research about the temp readings that I am getting, it seems to be normal enough, however at the rate that the fan rotates, ill be replacing it by the end of the summer :-(

Thanks for the input

D.D.

No prob, and welcome to the world of Linux :)  I've found that I learn the most through simply tinkering around, and through the forums.
I'm curious to see what results you get, seeing as we have the same laptop, but are seeing different symptoms (my fan seemed to not be coming on enough).  Keep us up to date on your progress!

---

### Post by DesktopDefender on 2009-07-22
Hey guys,

Figured out why my fan is going so fast so often while I am not really doing very much,

The GPU which is a nvidea 8600GT is hitting a tempeture of approx 61 degress C after about 20 mins of being on, so its switches on to cool the GPU

Is this the temp normal?

Do you guys know what temp your GPUs run at..?

Thanks
DD

---

### Post by DesktopDefender on 2009-07-22
> **GoldenSun said:**
> I have this problem also.  But I do not think it is all ubuntu's fault.  I had a part replaced in it and I was talking to the guy.  He said that they are releasing a service code for overheating for the ones with the m8600 installed in them.  They will take it and replace the mobo with a new one from a different manufacturer.  

And get a nice conky script to see all stats.
Hi GoldenSun,

Based in Ireland and had a look at the Irish Dell website and didn't find any information about the recall of XPS with overheating 8600 GPUs

By any chance have you got any further information

Thanks for you time 
DD

---

