---
title: "CPU scaling - how to set minimum frequency?"
date: 2010-02-05
forum: Hardware
---

### Post by CaptSaltyJack on 2010-02-05
I've got CPU scaling working on my Asus 1001P with Ubuntu Netbook Remix, but it won't go lower than 1GHz. No matter what I've tried to change the scaling_min_freq file (located in /sys/devices/system/cpu/cpu0/cpufreq), the changes won't stick.

How do I set the min/max range for CPU scaling? Windows 7 Starter on this netbook can squeeze apparently 8-11 hours of battery. I'd like to achieve that with Ubuntu.

---

### Post by bilbo1234 on 2010-02-08
I'm also curious about this, so I'll bump it up..

From what powertop reports, it appears 1ghz is the minimum supported CPU freq. This really makes me wonder how to get the claimed 11 hours of battery life. After making the standard adjustments, I'm not able to get more than 7 hours (about 8+ or so with wifi off).

I'm thinking this will be a nice laptop, once screen brightness, battery life, and microphone issues are resolved ;)

---

### Post by a8jr on 2010-02-08
I'm not that deep to ubuntu, but I simply used the cpu scaling widget... (well right click on the panel and then "add to panel", find the cpu frequency scaling widget, you know that).

there is some instance that the cpu will always set to "performance" setting (max frequency) that may cause the battery to be used up quickly. dont know why.

with the widget, simply click on it and change the cpu frequency.

however, everytime i use the widget, i would need to insert password to change cpu level. so i guess the frequency cannot be changed by editing the content of the scaling_min_freq file, but instead should be accessed from terminal and then use "sudo" and then something something (well im not a master in linux command, sorry). i guess that file only determine the smallest cpu frequency of your computer, but do not change the realtime condition at all.

anyway the number of selectable frequency differs from computer to computer (like my notebook has 4 different speed, other has 3,4,5...). i also dont know why this happen.

hope this help.

[EDIT] screenie
[[IMG]http://img109.imageshack.us/img109/5192/smallscreenie.png[/IMG]]("http://img109.imageshack.us/i/smallscreenie.png/")

---

### Post by msrinath80 on 2010-02-08
> **a8jr said:**
> 

however, everytime i use the widget, i would need to insert password to change cpu level. so i guess the frequency cannot be changed by editing the content of the scaling_min_freq file, but instead should be accessed from terminal and then use "sudo" and then something something (well im not a master in linux command, sorry). i guess that file only determine the smallest cpu frequency of your computer, but do not change the realtime condition at all.



Do a sudo dpkg-reconfigure gnome-applets and choose "Yes" when asked whether to install cpufreq-selector with SUID root. Now it won't keep asking for permission every time.

---

### Post by bilbo1234 on 2010-02-15
cpufreq-info says that 1000mhz is a hardware limit on the Asus 1001p. Attempting to set a lower minimum (using cpufreq-set) does nothing. How on earth is one supposed to get 11 hours of battery out of this?

---

### Post by onamattuphere on 2010-02-15
I have just worked my way through these problems in [my recently solved thread]("http://ubuntuforums.org/showthread.php?t=1383190").

---

