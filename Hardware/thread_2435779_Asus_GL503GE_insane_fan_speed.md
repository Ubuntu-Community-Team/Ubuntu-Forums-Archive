---
title: "Asus GL503GE insane fan speed"
date: 2020-01-25
forum: Hardware
---

### Post by user1254 on 2020-01-25
Hello to everyone,
i recently bought the gaming laptop Asus GL503GE with i5-8300h and Nvidia GTX 1050Ti 4GB.
With some problems, i managed to install Ubuntu 16.04 on this laptop but after a few days, I started to notice that the fans speed were too much loud. I decided to substitute the old thermal paste but things didn't go better.
These days, as soon as I open a program, say even the browser, the fans go crazy for a little while, I'd say at full speed or almost there, and then they calm down. If I close the browser, they come back to run fast and then, after a few seconds or so, they settle down. 
I tried to watch the frequency of CPU and it could easily go over 3.5Ghz for every little task and then settle down to 900Mhz more or less.
I installed **cpufrequtils** to set a range of frequencies for the CPU: min 900Mhz max 2.3Ghz but fans are still loud as before and Unity freezes when I press the play button (at first they reach the max. frequency and when Unity freezes they go back go the minimum frequency. I can't therefore use programs as before)
I also checked the GPU and modified the **xorg.config **file to set the performance level to 2 and even 1 (levels go from 0 to 3) but problem still occurs.
I tried to disable intel turbo boost still no results.
I guess the CPU is the main problem, but I don't know how to fix that.
Is there something I can do about it? It also seems that fan speed cannot be set manually..

Thank you

---

### Post by mörgæs on 2020-01-26
Hi, welcome to the fora.

Though Ubuntu 16.04 is still supported it's outdated and should not be used, especially for new hardware. I recommend that you begin with a fresh install of 19.10.

---

### Post by user1254 on 2020-01-26
Yes, I know 16.04 it's kinda old but I'm forced to use it for a few months at least..
The problem is that even with Windows 10 i face the same problems.
I updated nvidia drivers, set nvidia GPU as default for 3D Applications, still hella loud.
The next step i was thinking about was undervoltage but I was wondering if there's something I could do about it before that

---

### Post by mörgæs on 2020-01-26
You could try updating the UEFI firmware.

---

### Post by user1254 on 2020-01-26
I checked BIOS and says it is the latest version already, checked the asus download center and it indeed is the latest version
I noticed one thing.. I have Unity running right now and using this command **watch -n1 "cat /proc/cpuinfo | grep \"^[c]pu MHz\"" **to check CPU frequency  it shows that the frequency flactuate a lot ranging from 900Mhz or so to even 4Ghz with no apparent fan speed increase (I'd say it's a tollerable fan noise).
Besides Unity, i also have some other programs running and using the **top** command I can see that the **load average** is 1,55 -- 1,50 -- 1,32 (flactuating just a little bit from that) and that the % usage of each core is no more than 20% (usually raning from 9% to 18% or so for each core).
As soon as I launch another script though, say a python script that interacts with Unity and the other stuff running now, the command **watch -n1 "cat /proc/cpuinfo | grep \"^[c]pu MHz\"" **constantly outputs 4Ghz for every core but the **top **command shows that load average is 1,23 -- 1,24 -- 1,25 and that the % usage of each core now ranges from 13% to a 23% max or so. Fan speed here goes crazy, I'd say full speed ( I guess because of the constantly 4Ghz ) and **psensor **shows temperatures ranging from 68C degress to 81C degress (but sometimes I saw even 90C degress..) for CPU and less than 50C degress for the GPU nvidia 
Is there something I can do about this?
The only things I can think of are the undervolt and the **cpulimit  **command to limit all python scripts but.. yeah, I'd like to know if I could do something else

EDIT1: top now shows load average of 1,83 -- 1,73 -- 1,45 after 5 min or so of the python script running, with the % usage of each core still no more than 25%.
As soon as I close the python script, the fan speed comes back to a tollerable level and the CPU frequency goes back to flactuate from 900Mhz to 4Ghz

EDIT2: if laptop is not charging, even when launching the script, frequency still flactuate therefore the fan noise is tollerable, If instead I plug in the AC, when launching the script, CPU freq goes to 4Ghz constantly. I guess when laptop is not charging, it is using some battery save mode but when the AC is plugged, it goes under some performance mode, which, if needed, uses all cores at max speed without flactuating.
[B]Is there a way to find out which options is the SO using while the AC is not plugged and use those even when the AC is plugged?


[/B]EDIT3: turns out that using the command **echo 2800000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq** as superuser really locks the cpu (0 in this case) to 2.8Ghz. Set that value for all cpus and system seems ok. Fan noise tolerable, CPU temperature under 70C degrees, GPU under 52C degress and max usage of CPU (according to psensor) is 39%.
I guess this can be a quick solution. Another thing i noticed is the **energy performance preferences **file under **/sys/devices/system/cpu/cpu0/cpufreq/ **directory which could be helpful in some cases..

---

