---
title: "CPU throttling - unable to achieve max freq"
date: 2007-02-18
forum: Hardware &amp; Laptops
---

### Post by koara on 2007-02-18
I can't seem to be able to get maximum frequency for my system. I have HP nc6320 laptop, core 2 duo @ 2gz, running edgy x86_64 with  2.6.17-11-generic. cpufreq-selector lets me select any frequency from '2000000 1667000 1333000 1000000' as found in  /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies.

However when i select 2ghz, the frequency is set to 1.67Ghz (83%), and the value of 2ghz is actually never achieved. This 1667000 value is displayed both on CPU freq Scaling Monitor and  'cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq'.

Same thing is achieved by selecting the performance governor, which is supposed to set the frequency to maximum. What is going on here?

---

### Post by mr.f on 2007-02-18
I have the same problem on my nx9420 (my max frequency is 1.83 but it never goes above 1.33)

I've found the problem to be the in 
/sys/devices/system/cpu/cpu0/cpufreq/scaling_maxfreq

Even though the availble frequencies include 1.83, this file indicates 1.33 to be the max frequency. I've been able to change this with 

sudo cpufreq-set -u 1833000 (from the cpufrequtils package) 

But this only sets the frequency for cpu0. I don't know how to set cpu1, and also I don't know how to change scaling_maxfreq permanently so that the max frequency is correct after the next reboot.

Anyone knows how to do that?

---

### Post by mr.f on 2007-02-19
Ok, I solved the problem like this:

Install the cpufrequtils package:
[INDENT]sudo apt-get install cpufrequtils[/INDENT]

Edit the config file:
[INDENT]cd /etc/default
sudo gedit cpufrequtils[/INDENT]

Change to:
[INDENT]ENABLE="true"
GOVERNOR="ondemand"
MAX_SPEED=1833000
MIN_SPEED=1000000[/INDENT]

(modify the MIN and MAX values to whatever is the min and max in your /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies)

Reboot.

Well, at least this worked for me. Also you can add one or two processor frequency applets to get some visual feedback that frequency scaling is actually active, and a simple way to change the policy. Hope this can help.

---

### Post by koara on 2007-02-19
Thank you mr. f! You were right, /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq information is inconsistent with /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies!  No idea why, but the cpufreq-set command you mentioned works nicely. I set cpu1 by simply copying the new scaling_max_freq file to ../cpu1/... . Thanks again!

---

### Post by phantez on 2007-02-24
I have exactly the same trouble on a hp nx7400 with a T5500 core2duo 1,66Ghz, and i solved it by creating a file with 1667000 inside and then i copied it into the correct folders.

> 
 echo 1667000 > scaling_max_freq
 sudo cp scaling_max_freq /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
 sudo cp scaling_max_freq /sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq


---

### Post by Pugwash on 2007-03-22
> **phantez said:**
> I have exactly the same trouble on a hp nx7400 with a T5500 core2duo 1,66Ghz, and i solved it by creating a file with 1667000 inside and then i copied it into the correct folders.

How would you go about restoring the original default settings by the way?

---

### Post by phantez on 2007-03-24
i still have the trouble my way to solve this trouble does not manage to do it anymore. I haven't the write to rewrite those files.

---

