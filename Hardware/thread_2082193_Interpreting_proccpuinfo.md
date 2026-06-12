---
title: "Interpreting /proc/cpuinfo"
date: 2012-11-08
forum: Hardware
---

### Post by RayDeCampo on 2012-11-08
Looking at my output for /proc/cpuinfo I see that two of my cores are running at 3600MHz but the other two are running at 1400MHz.  Is this normal for a quad-core processor?  

I have an AMD FX-4100 3.6GHz quad-core processor ([http://www.newegg.com/Product/Product.aspx?Item=N82E16819103996](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103996)).  Does this mean I am not getting 3.6GHz on all cores?  Again, is this expected or is something screwy here?

OK, when I cat'ed /proc/cpuinfo again to create a file to attach to this post now all the cores are reporting 1400MHz.  Hopefully someone can explain this to me.

---

### Post by ibjsb4 on 2012-11-08
CPU throttling?

[http://en.wikipedia.org/wiki/Dynamic_frequency_scaling](http://en.wikipedia.org/wiki/Dynamic_frequency_scaling)

---

### Post by RayDeCampo on 2012-11-09
> **ibjsb4 said:**
> CPU throttling?

[http://en.wikipedia.org/wiki/Dynamic_frequency_scaling](http://en.wikipedia.org/wiki/Dynamic_frequency_scaling)

I suppose that's a possibility although it is a desktop system.  How can I tell?  Is there a BIOS setting?

---

### Post by Sylos on 2012-11-09
Its my understanding that the cat /proc/cpuinfo command gives you snap shot of the speed at the time the command is run. So when your CPU is throttled down you will get a lower reading. 

Try either disabling throttling (set prefs to Performance) or just start something that uses all cores quite a bit (maybe rendering or a high end game) and then issue the command.

Cheers

---

### Post by RayDeCampo on 2012-11-11
> **Sylos said:**
> 
Try either disabling throttling (set prefs to Performance) or just start something that uses all cores quite a bit (maybe rendering or a high end game) and then issue the command.


Where is this Performance setting?

---

### Post by Yellow Pasque on 2012-11-11
It's normal for newer processors to change core speeds independent of each other (power-saving feature): [http://www.cpu-world.com/Glossary/I/Independent_dynamic_core_technology.html](http://www.cpu-world.com/Glossary/I/Independent_dynamic_core_technology.html)

---

### Post by Sylos on 2012-11-12
> **RayDeCampo said:**
> Where is this Performance setting?

I think I had to install CPU frequency scaling monitor - the options appear under that (my bad - I forgot I had to install that separately). Look for such an app in synaptic or the software centre.

Cheers

---

### Post by efflandt on 2012-11-14
If you want to see what the cores are doing over time (once per second), run this script (Ctrl+C to exit)

```
#!/bin/sh
while [ 1 ]; do
    grep MHz /proc/cpuinfo
    sleep 1
    echo
done
```

If you look at % of each core in **System Monitor** or **htop**, you don't really know if that is a percent of idle speed or top speed.  Although, if any core remains at 100% for a period of time, that core is likely at full speed.

---

