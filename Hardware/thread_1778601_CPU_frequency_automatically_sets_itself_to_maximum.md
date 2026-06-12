---
title: "CPU frequency automatically sets itself to maximum - after some time."
date: 2011-06-09
forum: Hardware
---

### Post by Matyy on 2011-06-09
Since I tried to set my computer too 800 mhz, where it used to run rather quiet, I observed a quite mysterious behaviour of Ubuntu: It sets itself to maximum frequency, after some time, not always the same. And not always directly to maximum, but in steps.  

My CPU can run at:
 2.00 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
(btw. the first 2Ghz is 100 Khz faster than the second 2GHz)

When I check the frequency, by using cpufreq-info or directly in /sys/devices/system/cpu/cpu1/cpufreq/ I can see, that it sets 

/sys/devices/system/cpu/cpu1/cpufreq/scaling_min_freq

of both CPUs to maximum frequency - 2001000.

When I set it back to 800000 - manually by editing the files or by using cpufreq-selector - it stays there for a while. Than sets itself to 1,6GHz and than to 2,0GHz... Not immidietaly tough - for some times, sometimes longer, sometimes shorter, it runs at 800MHz


Just after boot it is 800 MHz - set to performance governor always running at 2,0 GHz.

I have no idea where too look for, can't find anything in syslog, don't even know where it could come from. I wrote myself a script, that is changing the min_freq every other second,  but well, that's no real solution.

And I can't find anything online, only about people where it sets itself to minimum frequency. Any hints, ideas, suggestions where I should start looking, which other processes could be connected to this are welcome!

Hardware:
ASUS Z53S F3SV Notebook
Intel Core 2 Duo 2GHz

cpufreq-info says "acpi-cpufreq" is the driver

---

### Post by TBABill on 2011-06-09
I am not sure what your ultimate goal is. Are you intending to ONLY run at 800MHz? 
 
By default Ubuntu and other distros set the CPU frequency scaling capability to "ondemand", which does just what you said. As you increase the load on the CPU, the system allows it to automatically scale upward, incrementally, to carry the load up to the max of the CPU. Once demand drops, such as after stopping a video playback using Adobe Flash, then the CPU scales back to whatever frequency it can efficiently run at, or down to the 800MHz level on your machine. The freq changes constantly depending on what you are doing and how much processing power your machine requires for what you are trying to do.
 
Are you looking for a way to never increase CPU freq? I'm not sure how you would lock it in that manner. 
 
If you are trying to just run efficiently, you can check if it is set to ondemand, performance or something else with cpufreq-info, and you can change it for each CPU by using cpufreq-set command in a terminal.

---

### Post by Matyy on 2011-06-09
The problem is, that usually it should change the frequency between 800Mhz and 2 GHz - but it's not, also on (almost) no load, it is running on 2 GHz.

As far as I understand it
/sys/devices/system/cpu/cpu?/cpufreq/scaling_min_freq
/sys/devices/system/cpu/cpu?/cpufreq/scaling_max_freq
define the minimum and maximum a governor can choose from.

the minimum should stay 800MHz - it's not the current frequency, it's just the minimum the governor can choose of.

There are several methods to use a fixed frequency - but in the end they just set the governor to userspace and fix a frequency.

Or did I misunderstand anything there?

Btw the default here isn't ondemand but performance.

---

### Post by tgalati4 on 2011-06-09
More likely is a background process running.

sudo apt-get install htop powertop
htop
sudo powertop

---

### Post by TBABill on 2011-06-09
Performance will keep your CPU at max at all times. If mine were set that way I would ```
sudo cpufreq-set -g ondemand
``` or you can also do it for each CPU individually by ```
sudo cpufreq-set -c 0 -g ondemand
``` and then do the same for each subsequent CPU.

---

### Post by Matyy on 2011-06-09
Thanks for your help, thanks for powertop, I didn't know that one yet. I am using htop, not much of any activity visible, will try powertop more.

But I think there is a fundamental misunderstanding in what I wrote:

It doesn't matter which governor I choose, since the minimum frequency is set to 2,0GHz any governor can choose from nothing but 2,0 Ghz - 2,0 Ghz.

The main problem, and I am quite sure with that, is the minimum frequency - or did I completely misunderstand it and the minimum frequency shouldn't be really the minimum frequency?

When I look at cpufreq-info it says something like (it's in German so I will just translate it):

driver: acpi-cpufreq
...
hardware limits: 800MHz - 2,00 GHz
possible frequencies:  2.00 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
possible governors: conservative, ondemand, userspace, powersave, performance
current behaviour: the frequency should be between 2,0 GHz and 2,0 GHz, the governor (insert any, whichever I chose before), which frequency between those two it chooses.
now running at: 2,0 GHz, verified through hardware check
Statistics... if I don't do anything always >90% 2,0 GHz

so now what I am doing is, changing the minimum frequency, and accordingly, the current behaviour changes:
the frequency should be between 800 MHz and 2,0 GHz,  [...]
now running at: 800 MHz, verified through hardware ...

But within sometimes second, sometimes minutes, without changing anything myself it is set to 2,0GHz - 2,0GHz  again.

Something is changing the minimum frequency to 2,0 GHz without my input.

---

### Post by Seq on 2011-06-09
> **Matyy said:**
> But I think there is a fundamental misunderstanding in what I wrote

I agree with you there.

The behavior you described definitely sounds like a bug. You should file a bug on launchpad.

---

### Post by TBABill on 2011-06-09
> **Matyy said:**
>  
so now what I am doing is, changing the minimum frequency, and accordingly, the current behaviour changes:
the frequency should be between 800 MHz and 2,0 GHz, [...]
now running at: 800 MHz, verified through hardware ...
 
**But within sometimes second, sometimes minutes, without changing anything myself it is set to 2,0GHz - 2,0GHz again.**
 
**Something is changing the minimum frequency to 2,0 GHz without my input**.
 
Just a guess, but you mentioned your machine CPUFREQ setting is set to performance. If you adjust it to ondemand it should automatically care for your needs to go to 800MHz by default and scale upward when necessary. Even if you want to do it manually by setting min and max freqs, the performance setting may override your manual settings and revert back to max at all times. 
 
Have you tried to scale to ondemand and then see if your performance changes or are you sticking to performance and making all changes to settings manually without changing the governor setting?
 
Edit: just to be clear, my point is that it appears maybe the governor setting overrules the manual settings and forces you back to max. I'm just not sure if the governor setting *should *perform like that or not by design.

---

### Post by belltown on 2011-06-09
Ubuntu has a service, "ondemand", that messes with the CPU frequency settings, so if you try to set stuff manually it may get overwritten. To disable this service type:

```

[FONT=Liberation Serif, serif][SIZE=3]sudo update-rc.d -f ondemand remove[/SIZE][/FONT]
[FONT=Liberation Serif, serif][SIZE=3]sudo update-rc.d ondemand stop 80 0 1 2 3 4 5 6 .       (Don't forget the period at the end)[/SIZE][/FONT] 

```Now you can put CPU freq settings in /etc/rc.local, for example, and they should not get overwritten.

---

### Post by Matyy on 2011-06-10
thank you belltown, when I am home I will have a look at that, sounds promising, yesterday I changed the access rights to read only also for root - it works now, just have to do that every time I launch:

```
echo 800000 > /sys/devices/system/cpu/cpu1/cpufreq/scaling_min_freq
echo 800000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq
chmod 444 /sys/devices/system/cpu/cpu1/cpufreq/scaling_min_freq
chmod 444 /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq

```

---

### Post by belltown on 2011-06-10
> **Matyy said:**
> thank you belltown, when I am home I will have a look at that, sounds promising, yesterday I changed the access rights to read only also for root - it works now, just have to do that every time I launch:

```
echo 800000 > /sys/devices/system/cpu/cpu1/cpufreq/scaling_min_freq
echo 800000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq
chmod 444 /sys/devices/system/cpu/cpu1/cpufreq/scaling_min_freq
chmod 444 /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq

```

If you set the CPU freqs in /etc/rc.local then you won't need to change the access rights as everything in rc.local is run as root.

---

### Post by leandrw on 2011-12-27
The same here. 
I changed my configurations to conservative governor, setting max e min frequency rate and this work for a while. After some minutes or a reboot, every configuration is override by something-that-i-dont-know e set the min and max to the hardware max freq rate and the governor to performance. Is a notebook HP pavilion Dv5 serie with a AMD processor, is very hot! Sometimes I think I can toast something here. Sorry for my bad English, but this can be very useful for me and the other who having the same problem.

****INFO: the performance governor was set as default after the cpufreq-utils installation.***

:-k There are some daemon changing everything?

[RIGHT][SIZE="1"]*(Sorry for my very bad English :oops: )*[/SIZE][/RIGHT]

---

