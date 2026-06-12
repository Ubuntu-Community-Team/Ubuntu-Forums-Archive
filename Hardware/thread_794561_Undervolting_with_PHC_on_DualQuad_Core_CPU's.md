---
title: "Undervolting with PHC on Dual/Quad Core CPU's"
date: 2008-05-14
forum: Hardware
---

### Post by Daelyn on 2008-05-14
For all of you dual/quad/(*) guys out there with lappies/desktops and undervolting in progress or thoughts.

I have used the Notebook hardware control utility within windows previously (yes, I have once been on the dark side aka. Microsoft) and it worked very well with undervolting for me. Lowered temperatures extensively and eliminated the risk of any 3rd degree burns on my thighs from ever having a chance.

Anyways, I installed gutsy same day it was released and decided I was gonna learn linux and stick with it for good. Went fine (removed machosoft permanently two days later), installed PHC and used it until a kernel update messed it up. Didn't bother much about sorting it due to a potential reinstall later anyways, but, what I remember is that the temperature always where higher than I got in windows on full load whilst max undervolted.

So, I sat and recompiled with PHC undervolt patches tonight and stumbled upon a quite simple "may be" reason. Because we're able to use our cores at independent speeds we gotta be able to run them on independent core voltages too, right? I mean, applications sometimes just run on one core and max it out, so, it would be unreasonable for the voltage to go up to max on both while only one core needs it? So, what is the issue then? The undervolting script only manipulates ONE of the cores voltages (cpu0) as specified in the undervolt script as far as I have been able to make out of it.

I gotta head to bed, but, just wondering if anyone else has thought about it and maybe sorted it permanently in their scripts? or maybe made it independent of how many cores you got? I'll modify my script to account for multi-core system tomorrow and see if it gives a difference or not on my machine. 

Anyways. Shed your thoughts over this. I haven't looked at the phc-forum yet (I suspect I should have before I even thought about this). Sorry in that case. 


Over n' Out
/ Lazy Dae is headin' to bed. 

PS. Another quick reminder to myself. As posted all over the phc forums, it specifically says core 2 duo's (and others) aren't (fully) supported etc, yadda, yadda, yadda. I guess it could be due to the fact that multi-core functions haven't been integrated into the scripts to account for more than one core? 

----------------
*please don't say you have more cores, I would turn sooo jeallus!!
----------------
related to thread:
[http://ubuntuforums.org/showthread.php?p=4908896](http://ubuntuforums.org/showthread.php?p=4908896)

---

### Post by Ares Drake on 2008-05-15
> Because we're able to use our cores at independent speeds we gotta be able to run them on independent core voltages too, right? I mean, applications sometimes just run on one core and max it out, so, it would be unreasonable for the voltage to go up to max on both while only one core needs it? So, what is the issue then? The undervolting script only manipulates ONE of the cores voltages (cpu0) as specified in the undervolt script as far as I have been able to make out of it.

In short: I think you're missing a big point here: hardware.

Your ideas are reasonable and having the cores running at different voltages may be desirable. However your cpu hardware has to support this, i.e. it needs to circuits to deliver power. I only know that AMD's new phenom processors allow for this, but have no clue about intel.

I think this is the reason for the second core to automatically use the voltage of the first one in my howto.

You can check
```
cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
```
and
```
cat /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
```
should give the same results even if you only set your voltage for one core.

Windows still running cooler might have other reasons. For example some windows utilities allow for underclocking as well, so your cpu will run even slower and use less power than designed.
Second, I don't know much about the power states c1 - c6. These are activated to save energy in the unused milliseconds. Maybe windows is yet more tuned there. You can use intel's powertop software on linux to optimize your setup a little.

---

### Post by Daelyn on 2008-05-15
> **Ares Drake said:**
> 
Second, I don't know much about the power states c1 - c6. These are activated to save energy in the unused milliseconds. Maybe windows is yet more tuned there. You can use intel's powertop software on linux to optimize your setup a little.

I have always been using powertop, and the voltages are indeed different according to the vids phc represents.

```

matt@admin-laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
13:35 10:28 8:22 6:19 
matt@admin-laptop:~$ cat /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
13:43 10:33 8:26 6:19 
matt@admin-laptop:~$ 

```

I have been thinking about the hardware already, but, unfortunately I have been out of the business of deep down technology since before they started dual cores, so I don't know.

But, it sounds unreasonable that I have one core running a thread at full speed and power, whilst the other lies dorment at lowest state and enjoys the powertrip. 

It would be great if someone more into it knows if there are different power feeds to them. Or, maybe it's just kernel/module that reports it wrongly?

Also, another thing. Why do I only have four frequency/voltage steps instead of six (could it have been more?) in windows (why does every sentence mention that horrible brand again)?

---

### Post by Daelyn on 2008-05-15
I have reconfigured the undervolt script to account for dual core now and it is possible to apply different voltages. Don't know if there is any use, but, for multiprocessor people it could maybe be an advantage.

I'll report any findings to see if it actually helped down the temperature or not. Hard to find any consistency because I haven't monitored temperatures very closely for the pasts months.

anyways, maybe we get something out of it.

---

### Post by RadiusXE on 2008-07-16
> **Daelyn said:**
> I have reconfigured the undervolt script to account for dual core now and it is possible to apply different voltages. Don't know if there is any use, but, for multiprocessor people it could maybe be an advantage.

I'll report any findings to see if it actually helped down the temperature or not. Hard to find any consistency because I haven't monitored temperatures very closely for the pasts months.

anyways, maybe we get something out of it.

where can I found the script? My cores can run on different voltages...

---

### Post by linkmaster03 on 2008-09-23
OK. I did everything and it was correct, up until I ran the script. It went all the way down to 0 and stopped. 

```
Default VIDs: 40 34 30 25
Current VIDs: 0 34 30 25
Testing VID: 0 (700 mV)
..............................
Default VIDs: 40 34 30 25
Current VIDs: -1 34 30 25
Testing VID: -1 (684 mV)
./linux-phc-optimize.bash: line 161: printf: -1: invalid option
printf: usage: printf [-v var] format [arguments]


The lowest acceptable VID is 0.

Recovering CPU.
./linux-phc-optimize.bash: line 138: 11296 Terminated              burnMMX

Run this script again to continue the optimization.

```

Then when I tried to run the script again...

```
Load VIDs from 'phc_tweaked_vids'
> ERROR: Wrong VID count!
```

And it stops. :( Help?

---

### Post by darthbushi on 2008-11-01
BBBBBBBBump!!

I have the same problem as linkmaster03. I think it must have something to do with either my processor (Core 2 Duo sl 7100 low voltage; probably it can be undervolted even further) or with my kernel (have been using the script designed for kernel 2.6.24-17-generic even though my kernel is 2.6.24-21-generic... Tried to compile for my kernel, with no luck).

Does anyone have any ideas?

Thanks a lot!!

---

### Post by Snakekick on 2009-07-30
i have the same problem. any news ? ;)

---

### Post by Uhuu on 2009-09-25
> **Snakekick said:**
> i have the same problem. any news ? ;)

same here, bump

---

### Post by mihai.ile on 2010-05-08
Hello.
I just created a guide for Ubuntu 10.04 LTS and updated the script for multicore. It uses one voltage for all cores as there is not such a great difference between cores.
Here I placed the guide, and the script is there also. [http://openmindedbrain.info/09/05/2010/undervolting-in-ubuntu-10-04-lucid-lts/](http://openmindedbrain.info/09/05/2010/undervolting-in-ubuntu-10-04-lucid-lts/)
Hope you find it useful

---

