---
title: "Ubuntu 14.04 sensors detect, fan speed problem"
date: 2014-04-27
forum: Hardware
---

### Post by Hossein_Talebi on 2014-04-27
Hi,

I am running ubuntu on a Lenovo Ideacenter PC with Core i7, Nvidia Gforce660 graphics, 32GB RAM, 64GB SSD and 2TB HDD.

With no special configuration, in general, the Fans work at least 1.5 times faster than Windows 8 for no reason (the temperature is below 40). In version 13.1, I installed the fancontrol and after using sensors-detect I could setup my fans speed and everything was working perfect. 

Now, After upgrading to 14.04, when I run the sensors-detect, update the /etc/modules and restart, the Fans (I have 3 fans) of the system work even faster and they change the speed according to my CPU usage. This means when I open some programs they work really fast. When I run the Fancontrol, it cannot control the fan speed. Please help me to return to my ubuntu13.1 config or solve this problem. The system works really loud now :(.

Cheers
H.

---

### Post by Hossein_Talebi on 2014-05-01
ok, I found my answer. I Downloaded the lm-sensors packages from ubuntu 13.1 and ran the sensors-detect with the older version. The file generated had a different Chip driver i.e. the old one was "w83627ehf" and the new (14.04) detected one was nct6775. So, apparently it was the wrong one. I manually replaced the chip drivers and now it works fine like before. :) Of course I have no idea what these drivers mean.

---

### Post by alexander-klein-5 on 2014-07-17
Hi... I´m a newbie... can you please tell me, how you changed the chipset drivers?

---

### Post by anutosho on 2014-08-03
Alexander,
though I don't exactly understand your question I can tell you what I have done to get the fan speeds and voltages shown by "sensors" and in gkrellm (my favored system monitor tool)

**Problem:**
when entering 
```
sensors
```
at the command line only the core temperatures was shown. No fan speeds and no voltages.

**Solution:**
I installed lm-sensors
Next I did a 
```
sudo sensors-detect
```
answering all questions about probing the different sensor types with "yes"
When it comes to "Do you want to add these lines automatically to /etc/modules?" I answered "no"
Next, I looked for already loaded modules between the ----cut here---- lines
```
lsmod | grep <module name>
```
In my case the coretemp module has already been loaded, but a w83627ehf module was not

So I did a
```
sudo vim.tiny /etc/modules
```
opened a new line and simply entered a ```
w83627ehf
``` here.

That will load the w83627ehf module at system startup
a manual 
```
sudo modprobe w83627ehf
```
will load the module immediately and a subsequent 
```
sensors
```
will show all the temperatures, fan speeds and voltages now.

I had no issues with fans running too fast on my system (maybe the BIOS takes care about it??) But now the speeds are shown in gkrellm, too :)

---

