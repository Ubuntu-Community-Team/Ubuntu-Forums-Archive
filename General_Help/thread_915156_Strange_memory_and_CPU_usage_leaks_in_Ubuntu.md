---
title: "Strange memory and CPU usage leaks in Ubuntu"
date: 2008-09-09
forum: General Help
---

### Post by descentspb on 2008-09-09
The ubuntu version is 8.04 x64, 2 GB of memory is available, no swap partition enabled.

Sometimes, when in Ubuntu the system begins to run out of memory, and both htop and sysmonitor show that the amount of used memory is i.e. 1800 MB out of 2000 MB. However, there are **no applications**, which can be shown either in htop, or sysmonitor, **that eat all this memory**! 

Strange is also, that even if i **turn off every single desktop application**, the memory usage is still high! Restarting the X server helps, and the memory usage gets back to normal.

When the memory usage is close to maximum, the CPU usage jumps really high, but again there are **no apps, that use the CPU**, according to htop or sysmon. What can that be? Is there any other way to check?

---

### Post by descentspb on 2008-09-10
Here's a screenshot, though it's not exactly what I am talking about, but it's similar. Where did over 200 MB of memory go?

[IMG]http://img116.imageshack.us/img116/8958/htoplp9.png[/IMG]

---

### Post by treepolitik on 2008-12-22
From my standpoint, it appears that you have three other users besides root using your computer: haldaemo, descent, and klog.  Are they all you?

---

### Post by descentspb on 2008-12-22
> **treepolitik said:**
> From my standpoint, it appears that you have three other users besides root using your computer: haldaemo, descent, and klog.  Are they all you?

well, these are the system users. One runs the hal daemon, and the other the klog daemon.

---

### Post by treepolitik on 2008-12-22
[http://ubuntuforums.org/showthread.php?p=3600578](http://ubuntuforums.org/showthread.php?p=3600578)

I found something on it in the archives.  Just double-checking, do you have the latest version?

---

### Post by descentspb on 2008-12-22
> **treepolitik said:**
> [http://ubuntuforums.org/showthread.php?p=3600578](http://ubuntuforums.org/showthread.php?p=3600578)

I found something on it in the archives.  Just double-checking, do you have the latest version?

As you can see, the post is a pretty old one. This was obviously not console-kit-dameon's fault, it is just the way htop shows processes. I tried killing all that, and it didn't help.

Nevertheless, I am not having this issue now. This was happening to one of the many Ubuntu installations I made, and I don't have any access to this problematic one.

---

### Post by treepolitik on 2008-12-23
> **descentspb said:**
> As you can see, the post is a pretty old one. This was obviously not console-kit-dameon's fault, it is just the way htop shows processes. I tried killing all that, and it didn't help.

Nevertheless, I am not having this issue now. This was happening to one of the many Ubuntu installations I made, and I don't have any access to this problematic one.

Sorry I couldn't be of any help.

---

