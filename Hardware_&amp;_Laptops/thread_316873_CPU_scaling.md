---
title: "CPU scaling"
date: 2006-12-11
forum: Hardware &amp; Laptops
---

### Post by amk221 on 2006-12-11
on windows i had a tray icon that came with my laptop (Acer Aspire 3610), which allowed me to choose the speed of the processor (similar to [emifreq]("http://zzrough.free.fr/emifreq.php#screenshots")), this was very useful when doing something like word pressing for long periods - to prevent overheating.

on ubuntu, i've used synaptic to try different software for cpu scaling, none have worked, apparently my processor doesn't support it. But it *really* does.

is this because the software hasn't got round to supporting my processor, or is it because my processor doesn't actually support cpu scaling? or is it something else? thanks for any help

---

### Post by wieman01 on 2006-12-11
What process have you got? An M-series Intel? Then you should definitely try "powersave" which comes with a nice little applet for GNOME as well as KDE.

---

### Post by amk221 on 2006-12-12
cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Celeron(R) M processor         1.50GHz
stepping        : 8
cpu MHz         : 1496.682
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up
bogomips        : 2997.73

---

### Post by wieman01 on 2006-12-12
Scaling is definitely possible, either user "powersave" or "powernow". No issues, my Intel PM copes well with it.

---

### Post by amk221 on 2006-12-12
cheers, things are looking up. do you mean kpowersave and powernowd?

---

### Post by wieman01 on 2006-12-12
Yes, "kpowersave" or "powernowd". I prefer "kpowersave" because it comes with a GUI which makes things a bit easier. Not sure about "powernowd"... I use it on my desktop PC without having installed any kind of GUI. "kpowersave" is doing a good job on my laptop.

---

### Post by amk221 on 2006-12-12
Thanks, but when selecting different schemes, the processor speed stays at 100% :(

---

### Post by wieman01 on 2006-12-12
Does it? Have you got ACPI installed already?

---

### Post by amk221 on 2006-12-12
yes. acpi, acpid, and acpi-support

i was looking around, and apparently there should be options for cpu scaling. but they are missing. hmmm

---

### Post by amk221 on 2006-12-12
i did this

> sudo modprobe p4-clockmod

then added the CPU frequency scaling monitor to a panel, see [this post]("http://ubuntuforums.org/showthread.php?t=309403&page=2")

and apparently it's worked. although kpowersave reports the processor is still running at 100% (750hz), or (187Mhz) etc. And I would have thought that Desktop effects would slow down if the processor really was running that slow - but they still run fine. so i am not convinced

*EDIT:* Actually, smooth scrolling lags, this is an indicator for me that it's working.

---

### Post by wieman01 on 2006-12-12
Great! Not sure why the applet does not do its job...

---

### Post by Azriphale on 2006-12-12
I assume you mean the Gnome panel cpu frequency monitor applet, and you want to be able to set the frequency.

Go to a console and type:

```

$ sudo dpkg-reconfigure gnome-applets

```

answer yes to the questions.
LEFT click on the CPU Frequency monitor, and you will be able to select a frequency.

---

### Post by amk221 on 2006-12-12
yea i've got it. each time i restart it says cpu scaling is not supported then i have to re-enter $sudo modprobe p4-clockmod, then it works again

---

### Post by wieman01 on 2006-12-12
The simply do this:
> gksu gedit /etc/modules
Then add:
> p4-clockmod
Save the file & reboot. That's it.

---

### Post by technodigifreak on 2006-12-12
> **amk221 said:**
> Thanks, but when selecting different schemes, the processor speed stays at 100% :(

You have to run powersave as root to get the scaling functions.  I'd tell you more, but it's been long enough that I don't remember the specifics.  I do remember it involves setting the sticky bit to allow normal users to use the functions.

---

### Post by Cerberu2 on 2008-06-07
read this, ;)


[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

---

