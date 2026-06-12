---
title: "CPU Scaling in Karmic on Reboot"
date: 2010-01-11
forum: Hardware
---

### Post by johnnybeem on 2010-01-11
Hi all,
I have an IBM T60 laptop which always overheats in Ubuntu unless I set the CPU scaling to powersave mode. In 9.04, I was able to easily set the scaling by writing "powersave" to these files:

/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

But now in Karmic, this doesn't seem to do anything... Everytime I boot up, it defaults to "ondemand" I have to manually set the scaling for CPU0 and CPU1 using the CPU frequency applet on the panel. It is a huge hassle!! Could somebody out there please help?!

---

### Post by johnnybeem on 2010-01-14
any takers?

---

### Post by luchio on 2010-01-18
I would also like to know how to set cpu frequency permanently...  Always resets to OnDemand on reboot.

---

### Post by mister_playboy on 2010-01-19
Remove /etc/init.d/ondemand so that it doesn't set the cpu frequency to ondemand after a minute or so:

```
sudo mv /etc/init.d/ondemand /etc/init.d/ondemand.bak
```

That will fix it.

---

### Post by luchio on 2010-01-19
actually, I edited that script so that it does 
```

echo -n performance > $CPUFREQ

```
 instead of 
```

echo -n ondemand > $CPUFREQ

```
works like a charm, thanks!

---

### Post by johnnybeem on 2010-01-27
Excellent, thanks guys. I used the same method as luchio and set mine to powersave so my laptop doesn't overheat. It kicks in about 30 seconds after the desktop shows, which is nice cause it stays on performance for a while when the desktop apps are still loading.

---

