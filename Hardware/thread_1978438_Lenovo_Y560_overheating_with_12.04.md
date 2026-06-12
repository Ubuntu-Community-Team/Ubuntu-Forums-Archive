---
title: "Lenovo Y560 overheating with 12.04"
date: 2012-05-11
forum: Hardware
---

### Post by haribrahma on 2012-05-11
Hi,

Recently i installed Ubuntu 12.04 as a dual boot along with Windows7. My laptop is a i7 processor(4cores) with 8gb ram and 1GB ATI Radeon 5400 graphics card. 

After logging in to ubuntu and working for say 20-30 mins my laptop getting super heated. I just do the basic stuffs like browsing, watching video and working on terminal(extensive ssh to remote servers). I have also worked with 10.10 and 11.04 previously but on that i never faced this over heating problem. 

I dont understand what causing this overheating.

---

### Post by krekerov on 2012-06-29
hi.i have same problem. :cry: may be you know how downgrade to 11.10

---

### Post by DrAlbert on 2012-07-20
Hi I have the same problem too. i downloaded cpufreqd to change the cpu frequency to 933MHz but it is still hot. i searched many websites but no answer.

---

### Post by maphilli14 on 2012-08-24
This app is what I've used in the past, but it doesn't work on 12.04 out of the box due to this bug:

[HTML]https://bugs.launchpad.net/tp-fan/+bug/480700[/HTML]

I found that I had to maniuplate some BIOS settings to max performance for both cpu and thermal.  Then the best I could do on my W500 was level 7, which is only ~3000 rpm.  I found that you can use these commands to set the level.

[HTML]http://www.thinkwiki.org/wiki/How_to_control_fan_speed[/HTML]

However, level 7 wasn't enough for dual-monitor using the discrete graphics, ATI in my case with open src drivers.

I was able to use this command to get it to 4900rpm

```
echo level full-speed | superuser tee /proc/acpi/ibm/fan
```

where superuser is sudo of course

This however was temporary and I had to create a loop in bash to run it every 30 seconds or so.

```
#!/bin/bash

while :
do

	echo level full-speed | superuser tee /proc/acpi/ibm/fan
	#echo "Press [CTRL+C] to stop.."
	sleep 30
done
```

HTH,

Mike

---

