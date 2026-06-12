---
title: "How to read this path? &quot;cooling_device -&gt; ../../&quot; etc. Need for script to cool CPUs"
date: 2016-05-22
forum: Hardware
---

### Post by watchpocket on 2016-05-22
I'm getting *"**Core temperature above threshold, cpu clock throttled**"* warnings like crazy in *dmesg* & other logs, and sometimes at boot.  (I'm getting this from *cpu0* and *CPUs 2 & 3* but, strangely, not from *cpu1*).

I *think* the source of the overheating is my[COLOR=#0000ff] 1 GB PNY nVidia GeForce GTS 450[/COLOR] graphics card, which powers two Nixeus Vue 30" IPS 2560x1600 WQXGA monitors running at the 2560x1600 resolution via two dual-link DVI ports. 

I get shutdown if I watch videos long enough (for maybe over a half-hour straight).

I found this *"[Cool your CPU temperature with frequency throttling]("http://seperohacker.blogspot.com/2012/10/linux-keep-your-cpu-cool-with-frequency.html")"* blog post and downloaded his script for doing this, but need to replace in the script his "list of possible locations to read the current system temperature" with my own actual location paths.

When I try to follow the paths to my own locations for this, I get links I can't decipher.

[I]Example:

[/I]One of the locations in the script is:```
# /sys/class/thermal/cooling_device0 
```
But if I enter
```
ls -la /sys/class/thermal
```

at my command-line, I get:```
total 0
0 drwxr-xr-x  2 root root 0 May 22 17:12 ./
0 drwxr-xr-x 55 root root 0 May 22 17:12 ../
0 lrwxrwxrwx  1 root root 0 May 22 17:12 cooling_device0 -> ../../devices/virtual/thermal/cooling_device0/
0 lrwxrwxrwx  1 root root 0 May 22 17:12 cooling_device1 -> ../../devices/virtual/thermal/cooling_device1/
0 lrwxrwxrwx  1 root root 0 May 22 17:12 cooling_device2 -> ../../devices/virtual/thermal/cooling_device2/
0 lrwxrwxrwx  1 root root 0 May 22 17:12 cooling_device3 -> ../../devices/virtual/thermal/cooling_device3/ 
```

***My question is:***

Where is the "../../" part of the path?  What do the dots stand-in for?  What are the actual directories to the left of *"/devices/" ?*

***Also**,* if possible, I'd prefer to cool things down at their hot source, and try to figure out how to do that, rather than run a script to keep CPU temp down.  (I've already blown liquid air through the fans and inside the box).  

If I can't do that, I'll try to get the script working.  

Thanks for reading this.

---

### Post by lisati on 2016-05-22
The dot has special meanings at the start of filenames in Ubuntu.
[LIST]
[*]A single dot at the start of a file name indicates a hidden file
[*]A single dot, on its own refers to the current working directory
[*]A double dot refers to the parent directory of the current working directory
[/LIST]
In other words, **../** means to go up one directory level, and **../../**means to go up two directory levels.

---

### Post by watchpocket on 2016-05-22
> **lisati said:**
> The dot has special meanings at the start of filenames in Ubuntu.

[LIST]
[*]A single dot at the start of a file name indicates a hidden file. 
[*] A single dot, on its own refers to the current working directory. 
[*]A double dot refers to the parent directory of the current working directory. 
[*]In other words, **../** means to go up one directory level, 
[/LIST]
 All that I knew, but:
> **lisati said:**
>  and **../../**means to go up two directory levels.

That's what I haven't seen long enough to have forgotten.  Thank you.

---

