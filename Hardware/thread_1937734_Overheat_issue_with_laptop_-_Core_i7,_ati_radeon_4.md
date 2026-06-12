---
title: "Overheat issue with laptop - Core i7, ati radeon 4670"
date: 2012-03-08
forum: Hardware
---

### Post by kartiksinghal on 2012-03-08
I have a Dell Studio XPS 16 with Core i7 720QM 500GB/4GB with ATi Radeon HD 4670 gfx card. For months now, I have been facing the problem of overheating when I am using linux. I have tried various options in last 2 years - Fedora, Arch, Ubuntu, Mint, etc but to no avail.

The last time it used to be cool enough was with Ubuntu 11.04 or Linux Mint 11. But 11.04 was unusable, and I decided to upgrade mint to 12 when it came out.

Here are some diagnostics on my most recent Ubuntu 11.10 installation:
Under normal usage (browsing etc. or even idle), temp. ranges:
CPU - 65-70 degrees C
GPU - 60-65 degrees C
HDD - 55-60 degrees C

these temperatures are quite close to critical values and reach them soon enough with continuous usage.

This is the same even after installing the proprietary drivers for gfx card (one solution that is quoted to be tried almost anywhere you search).

The reason for this problem is 'probably' a power regression in the linux kernel (somewhere between the lines 2.6.37 to 3.2), but since my system overheats I am unable to compile a new kernel (it shuts down before finishing).

Does anybody have a similar system and know which linux distro works fine with it? Or if you faced similar problem with your system and found any solution for it?

TIA

PS: I have tried Googling a lot, read scores of threads on ubuntuforums and others before finally posting here.

---

### Post by Sonsum on 2012-03-08
AFAIK, the critical value should be much higher for your i7, I have an i5 and its critical value is 105 degrees C.

You aren't going to find a current linux distro that has the problem solved since it is a kernel issue, not an Ubuntu one. Luckily, Intel's patch is being applied to the default kernel in 12.04, so your problems should be solved then. 

I used to have a similar problem, but now I'm down to running at about 34 degrees C. Here's a thread where I've discussed this (with someone else with an i7: [http://ubuntuforums.org/showthread.php?t=1935242]("http://ubuntuforums.org/showthread.php?t=1935242")

---

### Post by kartiksinghal on 2012-03-08
> **Sonsum said:**
> AFAIK, the critical value should be much higher for your i7, I have an i5 and its critical value is 105 degrees C.

Critical value is given as 85 degrees, there is 100 max mentioned too and system shuts down near 95-98 degrees. But even at 60 degrees, it's too hot to touch and I can hear the fan roaring.

> **Sonsum said:**
> You aren't going to find a current linux distro that has the problem solved since it is a kernel issue, not an Ubuntu one. Luckily, Intel's patch is being applied to the default kernel in 12.04, so your problems should be solved then. 

I feel the same, but it will take another 1.5 months at least. Is there any possibility of building a newer kernel package which I can install directly, without me having to build it on my system itself?

> **Sonsum said:**
> I used to have a similar problem, but now I'm down to running at about 34 degrees C. Here's a thread where I've discussed this (with someone else with an i7: [http://ubuntuforums.org/showthread.php?t=1935242]("http://ubuntuforums.org/showthread.php?t=1935242")

Wow, 34 sounds like cool, literally :) I am looking it up.

---

### Post by kartiksinghal on 2012-03-08
> **kartiksinghal said:**
> Is there any possibility of building a newer kernel package which I can install directly, without me having to build it on my system itself?

@sonsum I guess I got my answer already at the thread link you posted. Thanks. :)

---

### Post by Sonsum on 2012-03-08
> **kartiksinghal said:**
> @sonsum I guess I got my answer already at the thread link you posted. Thanks. :)

No problem! I can't wait for Precise so hopefully my temperatures will be even better!

---

### Post by Sergius14 on 2012-03-08
You can upgrade your kernel to 3.2 right now and see what's happens...


Or try 12.04 live cd...

---

### Post by kartiksinghal on 2012-03-08
> **Sergius14 said:**
> You can upgrade your kernel to 3.2 right now and see what's happens...

I just tried Precise kernel 3.3-rc6, it didn't seem to make any difference, but since those are vanilla kernels without any drivers etc. I am going to give a try to 12.04 beta1 next.

---

### Post by kartiksinghal on 2012-03-09
> **kartiksinghal said:**
> I am going to give a try to 12.04 beta1 next.

I installed beta1 today but to no avail. Here is my current sensors output (this when I have set Power Saver as the performance mode in Jupiter):

```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +26.8°C  (crit = +127.0°C)
temp2:        +75.0°C  (crit = +85.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +75.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +75.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +75.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +75.0°C  (high = +84.0°C, crit = +100.0°C)

radeon-pci-0200
Adapter: PCI adapter
temp1:        +83.5°C  
```

@sonsum, are you sure you had done just two things - newer kernel and jupiter to reach 34 degree levels?

Also note that currently I am using radeon OSS driver and have not put any special mode in kernel CMDLINE.

---

### Post by Sonsum on 2012-03-10
> **kartiksinghal said:**
> I installed beta1 today but to no avail. Here is my current sensors output (this when I have set Power Saver as the performance mode in Jupiter):

```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +26.8°C  (crit = +127.0°C)
temp2:        +75.0°C  (crit = +85.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +75.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +75.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +75.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +75.0°C  (high = +84.0°C, crit = +100.0°C)

radeon-pci-0200
Adapter: PCI adapter
temp1:        +83.5°C  
```

@sonsum, are you sure you had done just two things - newer kernel and jupiter to reach 34 degree levels?

Also note that currently I am using radeon OSS driver and have not put any special mode in kernel CMDLINE.

When I'm actively using the computer, 40 degrees is more common. But I believe that's all I did.

Have you tried that ```
echo "conservative" | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
``` to change the CPU frequency that the other person had success with on their i7?

(I'd make sure to check out that thread if you haven't, they're using a Dell XPS, which I am sure is quite similar to your laptop.)

---

### Post by kartiksinghal on 2012-03-10
> **Sonsum said:**
> 
Have you tried that ```
echo "conservative" | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
``` to change the CPU frequency that the other person had success with on their i7?

(I'd make sure to check out that thread if you haven't, they're using a Dell XPS, which I am sure is quite similar to your laptop.)

Isn't that command supposed to the same thing that Jupiter applet does? I had set it to Powersave mode which I believe is the lowest possible frequency setting.

Anyhow, I think I have seen that page, and by observing temperature values in Windows (see attachment), I have concluded that main difference is in the gfx card temperatures. So, currently I have switched to Ubuntu 11.10 Gnome Shell Remix and proceeding to install the catalyst 12.2 driver (which was released just 1-2 days back).

Hope I get a stable enough system to carry on my work (after months of frustration.)

---

### Post by kartiksinghal on 2012-03-10
After following my friend pankajthegeek's advice, I installed the latest Catalyst 12.2 (came out 1-2 days back only) with a new installation of Ubuntu 11.10 Gnome Shell Remix. And here are the results:

```
k4rtik@PlatiniumLight:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1: +26.8°C (crit = +127.0°C)
temp2: +66.0°C (crit = +85.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0: +65.0°C (high = +84.0°C, crit = +100.0°C)
Core 1: +65.0°C (high = +84.0°C, crit = +100.0°C)
Core 2: +65.0°C (high = +84.0°C, crit = +100.0°C)
Core 3: +66.0°C (high = +84.0°C, crit = +100.0°C)
```


```
k4rtik@PlatiniumLight:~$ aticonfig --od-gettemperature

Default Adapter - ATI Mobility Radeon HD 4670
                  Sensor 0: Temperature - 68.00 C
```


```
k4rtik@PlatiniumLight:~$ sudo hddtemp /dev/sda
/dev/sda: ST9500420ASG: 49°C
```


Seem pretty good to me. :-)

PS: The screenshot for windows was taken in load conditions with a game in background and an uncompression process in progress, these temperatures on linux are in idle condition.

---

### Post by Sonsum on 2012-03-10
I'm glad you got it fixed!

---

### Post by kartiksinghal on 2012-03-11
Not really, it's just that I have a stable system now. A little heavy work and it starts burning.

For instance I was watching a 720p movie in VLC and within 20 minutes I started noticing lags; there was just linux mainline code being downloaded using git other than that. I noticed temperatures reaching as high as 89.5 degrees for graphics and 84 degrees for cpu cores.

I am not sure for how long I will be happy with this setup. :(

---

### Post by Earsplit on 2012-03-29
Don't mean to bump this thread but have you found a solution? My XPS16 idles at 65 degrees, making my palms sweat when I'm coding. I have latop-mode-tools installed. jupiter broke my wireless card last time I had it installed.

This laptop is literally cooking my hands.

---

### Post by kartiksinghal on 2012-03-29
> **Earsplit said:**
> Don't mean to bump this thread but have you found a solution? My XPS16 idles at 65 degrees, making my palms sweat when I'm coding. I have latop-mode-tools installed. jupiter broke my wireless card last time I had it installed.

This laptop is literally cooking my hands.

No, not yet. It's as unstable as 2 weeks back. Gets heated up with little work.

I have temporarily moved to Ubuntu 10.04.4 under VirtualBox in windows, at least I can manage to finish my college assignments this way.

Just to add how I feel about it - it's really frustrating, till last year I was one to claim I don't use windows at all, but somehow at this stage all linux distros are behaving the same with my laptop, and I have no choice to but to use Windows.

---

