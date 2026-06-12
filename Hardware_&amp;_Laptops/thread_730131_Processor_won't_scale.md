---
title: "Processor won't scale"
date: 2008-03-20
forum: Hardware &amp; Laptops
---

### Post by CTenorman on 2008-03-20
Hi Guys,

I've had a fairly reliable Ubuntu 7.10 install for a while now, at least once the initial kinks were worked out. I have a CPU frequency monitor in the top right, and I just noticed today that it's not scaling above the base frequency any more, even when I pump its CPU activity right up to max with several different apps. I'm running a 5450 Core 2 Duo on a Dell 1720. Again, it was working great up until just recently, and I'm pretty sure it's nothing I've done. I also tried 

```
$ sudo dpkg-reconfigure gnome-applets 
```

and I can't force it to change frequencies manually, even though I could at one point. Any ideas? Thanks,

Scott

---

### Post by Yellow Pasque on 2008-03-20
Please post the output of cpufreq-info if the third command does not work or keep the governor set properly.
```
sudo apt-get install cpufrequtils
sudo cpufreq-info
sudo cpufreq-set -g ondemand
```

---

