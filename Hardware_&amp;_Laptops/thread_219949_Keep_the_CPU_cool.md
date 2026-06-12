---
title: "Keep the CPU cool"
date: 2006-07-20
forum: Hardware &amp; Laptops
---

### Post by lzfy on 2006-07-20
Hi, in Windows I used [this ]("http://www.diefer.de/speedswitchxp/") app to make my laptop constantly run @ 800MHz, no matter what I did (games, video converting, etc...) This way my fans almost never run. I would like to do this in Ubuntu too, it runs in idle @800 MHz but when I open an app, like MPlayer, it starts running at 1.8GHz again. So is there a solution for this? I bet there is, I just don't know what it is :rolleyes: 

btw. I'm running the K7 kernel from the repo's. oh and my CPU is a Turion ML34.

thanks...

---

### Post by John.Michael.Kane on 2006-07-20
You can use emifreq-applet it's in the repo's use synaptic to find it.

---

### Post by reacocard on 2006-07-20
there's already an applet in gnome that can do this. just add a "CPU Frequency Scaling Monitor" applet to your panel, then do:

```
sudo chmod +s /usr/bin/cpufreq-selector
```

then just click the applet. it can be set to let you change governers as well as frequencies.

---

### Post by lzfy on 2006-07-21
> **reacocard said:**
> there's already an applet in gnome that can do this. just add a "CPU Frequency Scaling Monitor" applet to your panel, then do:

```
sudo chmod +s /usr/bin/cpufreq-selector
```

then just click the applet. it can be set to let you change governers as well as frequencies.

Amazing thank you :D   Works perfect...

Could you please tell me what the chmod +s command does? I'm still a Linux newbie...

---

### Post by Hellkeepa on 2006-07-21
HELLo!

Shortly explained it allows the binaries to run as their owner, instead of the user calling them. That means that the applet is running as root, and as such has the capability to do changes on a system-level even if your user don't. ;)
Use with cauthion though, as the program's flaws can be used to gain root-access to your box (if it's a networked app).

Happy codin'!

---

### Post by lzfy on 2006-07-21
@Hellkeepa thanks a lot. but it's funny that you can do this in Kubuntu without changing permissions. anyway I'm happy it works :)

---

### Post by susa on 2006-07-21
would the "CPU Frequency Scaling Monitor" work on a Kubuntu & Xubuntu desktop machine ?

system is a thinkpad T43 with Dapper 6.06 and Kubuntu and Xubuntu

---

### Post by John.Michael.Kane on 2006-07-21
> **reacocard said:**
> there's already an applet in gnome that can do this. just add a "CPU Frequency Scaling Monitor" applet to your panel, then do:

```
sudo chmod +s /usr/bin/cpufreq-selector
```

then just click the applet. it can be set to let you change governers as well as frequencies.


emifreq-applet does the same thing as what you posted.

---

### Post by reacocard on 2006-07-21
> emifreq-applet does the same thing as what you posted.
but requires a new package, and applet doesn't fit comfortably on the default (23px) panel.

---

