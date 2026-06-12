---
title: "Undervolting Core2 Duo Penryn cpu"
date: 2008-04-10
forum: Hardware &amp; Laptops
---

### Post by GordonFreeman on 2008-04-10
Hi,
has someone of you undervolted his penryn processor? I  found a tutorial on the web which explains undervolting for core 2 duos: [https://www.dedigentoo.org/trac/linux-phc/wiki/phc_howto_ubuntu_001](https://www.dedigentoo.org/trac/linux-phc/wiki/phc_howto_ubuntu_001) and I followed every step and phc is running fine, at least it seems so because I have the phc files in the /sys/devices/system/cpu/cpu{0,1} folders.
But echoing the new VIDs (which I got from intels penryn datasheet [http://developer.intel.com/design/mobile/datashts/318914.htm](http://developer.intel.com/design/mobile/datashts/318914.htm)) does not change the values.

Before inserting them:
root@gordon-xps:/sys/devices/system/cpu/cpu0/cpufreq# cat phc_vids
41 34 30 27 23 19 

Then setting the new values:
root@gordon-xps:/sys/devices/system/cpu/cpu0/cpufreq# echo "44 44 44 43 41 41" > phc_vids

And then cat'ing again:
root@gordon-xps:/sys/devices/system/cpu/cpu0/cpufreq# cat phc_vids
41 34 30 27 23 19



Also there is some strange behaviour with the msrinfo tool, the vid/fid table shows that the cpu is running at full speed:
```

        |     CPU 0     |     CPU 1     |
        +-------+-------+-------+-------+
        | FID   | VID   | FID   | VID   |
--------+-------+-------+-------+-------+
Min     | 6     | 23    | 6     | 23    |
Max     | 76    | 34    | 76    | 34    |
--------+-------+-------+-------+-------+
Target  | 136   | 19    | 136   | 19    |
Current | 136   | 19    | 136   | 19    |
--------+-------+-------+-------+-------+

```

But in cpuinfo_cur_freq displays 800MHz:
root@gordon-xps:/sys/devices/system/cpu/cpu0/cpufreq# cat cpuinfo_cur_freq 
800000

Which is confirmed by /proc/cpuinfo.

So I suppose the msrinfo tool does not (yet) support the penryn cpu, I'm wondering only while it's output are some sensible values (136:19), since 136 ist the fid for full speed on my T9300 and VID 19 is 1,2625V.



So has anybody successfully undervolted his penryn cpu? If yes, how?

---

### Post by stefangr1 on 2008-04-10
Why would you want to do this... ?

---

### Post by GordonFreeman on 2008-04-10
> **stefangr1 said:**
> Why would you want to do this... ?

It safes power and it's a laptop, so the battery holds longer.

---

### Post by GordonFreeman on 2008-04-10
I kind of got my mistake, my default values are 41 34 30 27 23 19 and phc doesn't let you raise the voltage values above the default values, or in other words you can't overvolt your cpu. Now I have to recheck my translations from the VID table in the manual from above, but I'm very sure that I've read them correct because I translated the default values to binary numbers and they're matching.

I will check the manual from the 65nm Merom cpus but I suppose that intel has swapped the ranges, so higher VID means now lower voltage.





Edit:


Ok, I just checked and the VID mapping is still the same, so the question arises why PHC does not accept higher VIDs which mean lower voltages.

I just read in an article on the linux-phc website, that the value on the right means the voltage of the highest cpu state and the value on the right of the lowest. Which is quite confusing since then they do not correspond to the VID table in the intel documentation (see page 23 in the manual in my first post).




And in this case the output of msrinfo is correct (at least the current values - the correct min/max values can be read from the phc_default_controls file).






Edit2:

I just realized that the output of phc_vids seems in the reverse order according to the vid table because 19 in the vid table is 1,2625V which is the highes value not the lowest und 41 is 0,9875V which is not the highes but the lowest. So I think that PHC is reading the values in the wrong order. But as you may realize the author of the tutorial says that "39" is for the highest step and "19" is for the lowest. But if that's the case I really don't know how to read the VID table, and I'm pretty sure that the entries are read from right to left (with the values ascending from right to left).

---

