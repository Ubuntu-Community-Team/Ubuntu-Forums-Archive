---
title: "Crashing repeatedly, undiagnosed, possible IRQ conflict?"
date: 2014-09-15
forum: Hardware
---

### Post by pythonjosh on 2014-09-15
Symptom is the computer will do a full freeze/hang/crash.

Hardware:
CPU: Core i7 880
Mobo: EVGA 120-lf-e650
RAM: 8gb (4x2gb) 1333mhz
HDDs: 4x4tb, 2x3tb, 2x2tb, 120gb SSD for Ubuntu 14.04.1LTS all RAID 0
The mobo has 5 sata ports, have a 4 port sata PCIe x1 card for the other 4

I'm pretty new to Ubuntu/Linux. This crashing has been happening since changing over to Ubuntu 12.01LTS like 8 months ago.
Sometimes it can go a week without crashing, sometimes it's a few times a day. This is a Plex Media Server as well.
With googling I have discovered /proc/interrupts (I don't see anything obviously wrong)
I also have HardInfo installed (System Profiler and Benchmark).

I'm not too familiar with the log files, let me know what you want to see.

---

### Post by weatherman2 on 2014-09-15
What do you mean by "crash?"  Does the machine freeze?  Shut down?  Reboot unexpectedly?  Otherwise, describe what happens.

You might have a software/operating system issue, but I suspect a hardware problem.

Here's where I'd start with that:
- check the S.M.A.R.T. status (Attributes) of each hard drive and SSD.  Try installing GSmartControl and use it's analysis of the S.M.A.R.T. Attributes as a starting points. (Not all S.M.A.R.T. Attributes make sense; GSmartControl will highlight suspected Attributes e.g. Pending Sectors > 0.)
- test your RAM.  Run Memtest, which is already installed with Ubuntu, overnight (it loops repeatedly until you stop it).  Reboot the computer and hold down the Shift key to get a Grub boot menu from which you can choose Memtest.
- check the temperature of your CPU.  An overheating CPU can cause "crashes."  You can install lm-sensors.  The temperature of each core will rise as the CPU works harder.  You can even run stress test software to tax the CPU and see if you can make it overheat.  If the CPU is overheating, it could be because of inadequate cooling: CPU fan not working or not working right, heat sink dirty or clogged, not adequate case cooling, etc.  It's also possible the heat sink needs to be removed and cleaned and new thermal paste applied.
- check the power supply.  A failing power supply can cause all kinds of weird issues.  Or if you don't have an adequate power supply, when too much power is required in some cases you could experience freezes.
- failing motherboard.  Check for "blown caps" - capacitors on the motherboard that are "bubbling" or dirty-looking.

For software issues: look at the file /var/log/syslog around the time of a crash and look for information suggesting what might have been happening at the time of the crash.  If the problem is hardware, you may not see any hint of the crash.

---

### Post by pythonjosh on 2014-09-15
Crash = system hang. Have to hard power off.
I have been monitoring SMART status and all drives are good, however the two 3TB's is reporting that the temp has hit 46C (and are currently 46C).
These two are Seagate Constellations.
I have lm-sensors installed and it works with Webmin. Cpu has been spiking under heavy load up to 84C just last night.
A buddy told me anything under 90C is ok, I want to go with water cooling for the CPU and all the hard drives.
These are the last lines of syslog before the last crash:
```
Sep 14 08:32:27 mediadb dbus[832]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)Sep 14 08:32:27 mediadb dbus[832]: [system] Successfully activated service 'org.freedesktop.hostname1'
Sep 14 08:32:27 mediadb kernel: [32229.870615] systemd-hostnamed[17358]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
Sep 14 08:41:11 mediadb kernel: [32753.861856] type=1326 audit(1410709271.385:68): auid=4294967295 uid=65534 gid=65534 ses=4294967295 pid=17866 comm="vsftpd" sig=31 syscall=37 compat=0 ip=0x7ffcf8655757 code=0x0
```
I was not on or remoted into the computer at the time and these lines for org.freedesktop.hostname1 I have not seen before.

---

### Post by Bucky Ball on 2014-09-15
```
Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
```

That gives us a clue ...

Strangely, I don't have it in Synaptics, but I do have libnss-myhostname, and it's not installed.

---

### Post by weatherman2 on 2014-09-15
I don't think the nss-myhostname thing is significant.  I had never seen it before either - until yesterday when I was installing 14.04 on a new system and saw that message when trying to fix another problem (not a crash).  

46C seems reasonable for a modern hard drive.

However, I must disagree with your buddy; 84C seems too hot to me for a modern CPU, unless that is sustained for a while and all four cores are running heavy (in the case of your i7).   The fact that you are observing that randomly now indicates it could be getting much hotter.

I don't have any 1st-gen Core CPUs in use.  I have a couple of 2nd-gen Sandy Bridges that are only dual cores, not quad cores like your i7, and they generally idle under 40C.  60C under load would raise alarm bells for me.  I have an Ivy Bridge system that has an overheating issue (lousy CPU fan) that shuts down at 60C due to the BIOS setting.  You can check around the web and see what temperatures that CPU ought to hit even under load.

You can stress test your system without Ubuntu if you want to rule this out plus make sure any failure isn't due to Ubuntu.  I haven't done this in a while, but the Ultimate Boot CD for one used to have some stress-test stuff you could boot up and run the CPU at high load for hours.  Look for something that will tax all four cores.  If it passes the stress test, then you can start looking for other causes.

---

### Post by pythonjosh on 2014-09-18
I replaced the PCIe x1 sata card with a new one. Load tested moving a couple hundred gb's of files and no crash.
Thanks guys, marking as resolved.

---

