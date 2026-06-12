---
title: "Overheats causing random-ish shutdowns."
date: 2009-08-20
forum: Hardware
---

### Post by Mike_IronFist on 2009-08-20
I'm running 9.04 Jaunty with the latest stable NVIDIA drivers, 185 to be more specific.

My laptop tends to get pretty hot. On Windows (Vista) I play games like Team Fortress 2, Portal, etc. These things make my laptop heat up.

However, on Ubuntu, when I play non-intensive games like TeeWorlds or I leave a screensaver on, or sometimes during a web-browsing session, Ubuntu will suddenly shut me down without warning. It just zaps off. As a note, I do keep compiz fusion effects on all the time, but TeeWorlds has caused my laptop to get hot and shut off even without compiz on.

Can anyone tell me how to stop Ubuntu from reacting to overheating like this? This kind of thing only happens to me with Linux.

Thanks in advance.

---

### Post by snotplop on 2009-08-20
Many laptops shut down instantly like that when they reach a threshold temperature to protect the inner components.

Take a look at the bottom of your laptop. Do you see fans? If so, you don't have a laptop but a *table*top as putting it on your lap will only suffocate it.
Put it on a hard, flat surface and see if there's any improvement. If there is, it would be worth your time to invest in one of those laptop cooling platform devices.

---

### Post by Mike_IronFist on 2009-08-20
> **snotplop said:**
> Many laptops shut down instantly like that when they reach a threshold temperature to protect the inner components.

Take a look at the bottom of your laptop. Do you see fans? If so, you don't have a laptop but a *table*top as putting it on your lap will only suffocate it.
Put it on a hard, flat surface and see if there's any improvement. If there is, it would be worth your time to invest in one of those laptop cooling platform devices.

My laptop already rests on a cooling platform.

Again, this issue NEVER HAPPENS ON WINDOWS, no matter how hot my machine gets. It ONLY HAPPENS WHEN USING SOME KIND OF LINUX.

---

### Post by Mike_IronFist on 2009-08-21
Bump.

Help?

---

### Post by chessnerd on 2009-08-21
I had this happen on a computer running Windows (a desktop) and the reason turned out to be that the fan cooling the power supply was dead. When running Linux check to see if the fan in the laptop is on, if it isn't you'll have to talk with someone who knows how to work with fan issues on laptops (I've only ever dealt with them on desktops).

---

### Post by Mike_IronFist on 2009-08-21
> **chessnerd said:**
> I had this happen on a computer running Windows (a desktop) and the reason turned out to be that the fan cooling the power supply was dead. When running Linux check to see if the fan in the laptop is on, if it isn't you'll have to talk with someone who knows how to work with fan issues on laptops (I've only ever dealt with them on desktops).

Thank you, but the fan is working.

I think I said this, but it NEVER HAPPENS ON WINDOWS, despite the fact that I run far more graphically-intensive stuff on Windows. It ONLY happens on Ubuntu, and it happened once using Pendrive Linux, so it's a Linux-only problem.

---

### Post by sergiom99 on 2009-08-21
I can tell you 2 things I would do>
1. Monitor temperature with lm-sensors to check if its reaching warning levels.
```
sudo apt-get install lm-sensors
sudo sensors-detect
sensors

```
2. Compile my own DSDT file to make ACPI, thermal and power control smoother. Its very easy: [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

Also, posting more info about your hardware and laptop would be helpful.

Good luck!

---

