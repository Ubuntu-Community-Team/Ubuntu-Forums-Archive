---
title: "Change default CPU governor (performance to ondemand)"
date: 2009-12-21
forum: Hardware
---

### Post by trx64 on 2009-12-21
Some days ago, after an update, my default CPU governor (I've a notebook, Turion 64 X2) changed from ondemand to performance. The problem is that my CPU stays at maximum frequency, overheating the computer and running out my battery quickly. I always have to change it using the Gnome applet. How can I change the default CPU governor permanently? 

I've tryed:
- Make the changes made by the Gnome applet permanent, giving it the permission to change the governor with "dpkg-reconfigure gnome-applets", nothing appears.
- Add suid bit to /usr/bin/cpufreq-selector, no succes.

---

### Post by trx64 on 2009-12-24
Anyone? No idea?

---

### Post by impact on 2009-12-25
> **trx64 said:**
> Anyone? No idea?

2 ideas. :) The second one is probably better...

[http://ubuntuforums.org/showthread.php?t=860926](http://ubuntuforums.org/showthread.php?t=860926)

[http://ubuntuforums.org/showthread.php?t=541794](http://ubuntuforums.org/showthread.php?t=541794)

---

### Post by MARAUDER2003 on 2009-12-26
I have the same problem, and i've been looking for a solution with no luck yet. When i boot my laptop, it goes into performance mode and it stays there, i have to manually set it to ondemand once everything has loaded. It just annoying to have to set it manually, not to mention to hear the fans and battery go full blast and drained in no time. All the solutions i have come across are for previous ubuntu versions. Does anybody know a solution for 9.10?

---

### Post by trx64 on 2010-01-01
I've found an workaround. The program "cpufreq-selector" can change the governor, but it needs root permissions. But, if you add the suid bit, no password will be required:

$ sudo chmod +s /usr/bin/cpufreq-selector

After that, go to "System > Preferences > Startup Programs" and add a new item. The comand is:

$ cpufreq-selector -g ondemand &     

The frequency will be changed without any password.

---

### Post by MARAUDER2003 on 2010-01-29
I found what the problem was, in my case. I enabled the concurrency feature to "shell" for booting faster, I found out that this was causing the problem. Why? I just don't know. I just reset the feature back to "none" and the problem was solved. My laptop boots fast enough, so I can live without concurrency just fine, I thought I just let everybody know.

---

### Post by Sylslay on 2011-05-14
THX trx64 for post, it help!:popcorn:

1)My cpu: Athlon XP2500+ , OS:updeted fresh install Ubuntu 10.04 
apt-get install cpufrequtils sysfsutils

2)
rc.local

modprobe powrnow-k7
cpufreq-set -c0 -g ondemand
cpufrq-set -d 663000 -u 1860000
exit 0

3) sysfs.conf

devices/system/cpu/cpu0/cpufreq/scaling_governor=ondemand

then: 
$ sudo chmod +s /usr/bin/cpufreq-selector

After that, go to "System > Preferences > Startup Programs" and add a new item. The comand is:

$ cpufreq-selector -g ondemand & 

PS. Probaby before tha was simple way.
It still working, no more overlaod CPU. Full speed of X-server with 625 Mhz on CPU.

thx again

---

### Post by jokernk on 2012-03-18
Hi ,i have a second solution, sort of a hack but , works for me .
My problem on 11.10 , always performance on, always changing to performance.( what cause that? i change processor frequency with cpufreq-selector -f)

Fix 
I changed performance profile settings close to ondemand profile setings in /etc/cpufreqd.conf

[Profile]
name=Performance High
minfreq=20%
maxfreq=100%
policy=performance
#exec_post=echo 8 > /proc/acpi/sony/brightness
[/Profile]

[Profile]
name=Performance Low
minfreq=20%
maxfreq=80%
policy=performance
[/Profile]

[Profile]
name=On Demand High
minfreq=40%
maxfreq=100%
policy=ondemand
[/Profile]

And 
I changed 
/etc/pm/power.d/cpu_frequency
all lines with full_power=     (something)
are changed to full_power="ondemand"
All i care is "ondemand" profile.

Now , strange , is using all profiles, powersave, ondemand, performance, but as should be. (in cpu load -> performance profile ...etc)

I spend 2 days with this, maybe is useful for someone.

Reinstalling ubuntu was not an option.

---

### Post by marcjank on 2012-04-13
Hey everyone,

I've looking into this a bit, seems that for laptops the best option may be to change the settings in /etc/laptop-mode/conf.d/cpufreq.conf
Here you can set the default cpu governor for when you're on battery or ac.

---

### Post by DGINSD on 2012-06-05
> **marcjank said:**
> Hey everyone,

I've looking into this a bit, seems that for laptops the best option may be to change the settings in /etc/laptop-mode/conf.d/cpufreq.conf
Here you can set the default cpu governor for when you're on battery or ac.

I don't have that directory, why would that be?

---

### Post by marcjank on 2012-06-06
That's a good point, this directory exists if you have laptop mode tools installed. They are installed by default if you have a laptop, I don't know how you would do this if you were on a desktop.

---

