---
title: "Very poor battery life on my laptop"
date: 2007-09-30
forum: Hardware &amp; Laptops
---

### Post by InorganicMatter on 2007-09-30
All right, I'm a Linux n00b - trying to use Ubuntu.

On Vista, I can squeeze seven hours of battery out of my laptop.  On Ubuntu, I'm lucky to get four.  Running the same brightness.

Am I missing something maybe on power management, or something?

---

### Post by peabody on 2007-09-30
More than likely.  Have you tried scaling your cpufreq down?  Try the cpufreq-selector command.

Power consumption's going to get better in the next Ubuntu with the tickless kernel, you may want to try gutsy beta and see if it helps.

---

### Post by benhagerty on 2007-09-30
yeah, I could get like 2 maybe in Windows but now in ubuntu I get 45 tops

---

### Post by lincolnlad on 2007-09-30
install 'powertop' and see what processes it recommends you stop.

You can use Synaptic to get it.  It's aimed at Intel processors but is apparently still useful for other types of processor, too.

More info here: [http://www.linuxpowertop.org/](http://www.linuxpowertop.org/)

---

### Post by Rob500 on 2007-09-30
What about the Wireless LAN?

Mine doesn't have a driver for the button that engages it so I have to disable it using the on screen options, but the light remains on. I don't know if this means the wireless is still on or just that the light won't go out.

---

### Post by InorganicMatter on 2007-09-30
> **peabody said:**
> More than likely.  Have you tried scaling your cpufreq down?  Try the cpufreq-selector command.

Power consumption's going to get better in the next Ubuntu with the tickless kernel, you may want to try gutsy beta and see if it helps.
I have an Intel processor with SpeedStep.  I though scaling was taken care of in the hardware, right?

And I should have said that this is the Gutsy Beta I'm using.

As for WiFi, I'm always running that.  I live on WiFi, so it never goes off.

---

### Post by peabody on 2007-09-30
> **InorganicMatter said:**
> I have an Intel processor with SpeedStep.  I though scaling was taken care of in the hardware, right?

And I should have said that this is the Gutsy Beta I'm using.

As for WiFi, I'm always running that.  I live on WiFi, so it never goes off.

Default scaling is set to ondemand.  This means that the cpu is clocked down when it's not needed and it's dynamically clocked up when it is.  However, you can be even more conservative than this.  Using the conservative policy, the cpu is clocked down to it's lowest setting (usually around 600-800 Mhz) and kept there.  You take a performance hit, but if you aren't doing anything intensive, it can make sense to use this mode while not plugged in.

Other people have mentioned powertop.  It's worth a look and you can truly reap its benefits since you're running the tickless kernel.

---

### Post by David A Knight on 2007-09-30
> **peabody said:**
> Default scaling is set to ondemand.  This means that the cpu is clocked down when it's not needed and it's dynamically clocked up when it is.  However, you can be even more conservative than this.  Using the conservative policy, the cpu is clocked down to it's lowest setting (usually around 600-800 Mhz) and kept there.  You take a performance hit, but if you aren't doing anything intensive, it can make sense to use this mode while not plugged in.

Other people have mentioned powertop.  It's worth a look and you can truly reap its benefits since you're running the tickless kernel.

I may be wrong but doesn't conservative still scale? It just keeps it at the values longer, so a slight spike won't switch up to the faster speed.  Additionally I think the powertop site recommends ondemand over conservative as it will switch back down faster.  Selecting powersave keeps it at the lowest.

---

### Post by TheCanuck on 2007-09-30
The tickless kernel does help quite a bit but there are other factors that will kill battery life:

1) USB devices will prevent you from entering C3/C4 sleep
2) WIFI can limit the amount of time spent in C3/C4 (intel seems to work well, if you use mad wifi/ndiswrapper then you may see less time spent in C3)
3) Most graphics drivers for linux (ATI, NVIDA and intel)  create interrupts that can prevent the processor from entering C3/C4 as well.  There are some patches floating around though.
4) HPET needs to be enabled in the kernel to maximize the time spent in C3/C4.
 --- to find out if it's enabled use :   grep hpet /proc/timer_list

There are several powersaving patches that you can apply to the kernell which will allow the processor to sleep longer:  [http://www.tglx.de/projects/hrtimers](http://www.tglx.de/projects/hrtimers)

(note: the hrtimers site is having problems right now so you might not be able to get the kernel patches)

Ideally you want to get more than 90% residency in C3 or C4 for decent powersavings.  From my experience linux battery life from a fresh install usually blows compared to Windows.  But if you're willing to take a little time, recompile the kernel, apply some patches etc then you can probably get much better battery life than even Windows can give you.

---

### Post by peabody on 2007-09-30
> **David A Knight said:**
> I may be wrong but doesn't conservative still scale? It just keeps it at the values longer, so a slight spike won't switch up to the faster speed.  Additionally I think the powertop site recommends ondemand over conservative as it will switch back down faster.  Selecting powersave keeps it at the lowest.

You may be right, I've read web sites that have stated as such.  However, I have anecdotal evidence to suggest that (at least on my laptop) I get better battery life from the conservative setting (I actually timed it and got almost three hours with conservative while I got about two and a half under ondemand).  Also, I have the CPU frequency scale monitor running, and my dual-core never seems to go above 800 under the conservative setting.  However, you're right that powersave is supposed to be the best.

Edit: P.S. I stumbled across this post which says how to set the policy in gnome for when the ac is plugged or unplugged: [http://ubuntuforums.org/showpost.php?p=3189740&postcount=10](http://ubuntuforums.org/showpost.php?p=3189740&postcount=10)

Edit2: I think I got better battery life because I'm not running the tickless kernel, so you're probably right about your circumstance, maybe you should keep on ondemand.

---

### Post by dinub1 on 2007-09-30
> **peabody said:**
> More than likely.  Have you tried scaling your cpufreq down?  Try the cpufreq-selector command.

Power consumption's going to get better in the next Ubuntu with the tickless kernel, you may want to try gutsy beta and see if it helps.

Regrettably and I have a problem with this. I recently upgraded Kubuntu from 7.04 to 7.10 on my laptop. Since the upgrade, my CPU fan runs continuously, CPU temp stabilizes around 65 F and running "System monitor" shows processor load very high. Sometimes 100%, without running anything. This is annoying especially when the new kernel claims to reduce CPU power. Some sort of bug or something. It never happened with previous versions of Ubuntu.Running Windows XP home on the same machine, the CPU runs as usual cooler, fan only works intermittently and on idle, CPU temp is approx 47F. Did  anyone encounter a similar issue? For information, same Kubuntu 7.10 runs on a HP desktop but with very cool CPU temps and CPU load at idle  only shows 3-5% usage. However Kubuntu 7.10 has been installed from scratch on that machine and not upgraded, as in the laptop case.

---

### Post by peabody on 2007-10-01
> **dinub1 said:**
> Regrettably and I have a problem with this. I recently upgraded Kubuntu from 7.04 to 7.10 on my laptop. Since the upgrade, my CPU fan runs continuously, CPU temp stabilizes around 65 F and running "System monitor" shows processor load very high. Sometimes 100%, without running anything. This is annoying especially when the new kernel claims to reduce CPU power. Some sort of bug or something. It never happened with previous versions of Ubuntu.Running Windows XP home on the same machine, the CPU runs as usual cooler, fan only works intermittently and on idle, CPU temp is approx 47F. Did  anyone encounter a similar issue? For information, same Kubuntu 7.10 runs on a HP desktop but with very cool CPU temps and CPU load at idle  only shows 3-5% usage. However Kubuntu 7.10 has been installed from scratch on that machine and not upgraded, as in the laptop case.

Did you check what process was causing the cpu to be used at 100%.  It sounds like killing the offender will solve the problem.

---

