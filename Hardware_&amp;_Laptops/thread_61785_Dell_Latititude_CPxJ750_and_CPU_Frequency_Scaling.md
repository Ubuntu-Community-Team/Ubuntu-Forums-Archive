---
title: "Dell Latititude CPxJ750 and CPU Frequency Scaling"
date: 2005-09-02
forum: Hardware &amp; Laptops
---

### Post by xx404 on 2005-09-02
I've just installed Ubuntu 5.04 and have chosen to run 2.6.10 kernel and am pretty impressed with it. I was having problems with the mouse cursor "pausing" intermittently and managed to track it down to the CPU Frequency Scaling being performed by powernowd. I've uninstalled it and the annoying mouse problem has gone away (I wan't using an external mouse but the internal ALPS stick/touchpad).

Unfortunately I now don't have any form of CPU scaling so that when I'm running on battery power the CPU is still running at full speed (750MHz). The Dell BIOS claims that the CPU will still throttle itself when the system is relatively idle but I haven't seen this working (I'm using the Gnome CPU monitor applet).

Does anyone know how I can get the laptop to automatically slow the CPU down when running on battery power?

---

### Post by nic2 on 2005-09-02
Try this link:

[http://cpuspeedy.sourceforge.net/](http://cpuspeedy.sourceforge.net/)

---

### Post by xx404 on 2005-09-03
Thanks. That looks like the program that I'm looking for and I've downloaded the .dev file and installed it. Only problem is that when I run it it says the following.

cpuspeedy: error: ERROR_NO_INTERFACE

If you are running a v2.5/2.6 kernel, please make sure that:
  - That you have the core cpufreq and cpufreq-userspace modules
    compiled or loaded into the kernel.
  - The you have sysfs mounted /sys
  - That you have the cpufreq driver for your cpu loaded.


If I "modprobe cpufreq" it says "FATAL: Module cpufreq not found." but "modprobe cpufreq-userspace" works. I've obviously got the correct kernel modules and support since powernowd had no trouble changing the speed of my CPU. When I uninstalled powernowd the </sys/devices/system/cpu/cpu0/...> directories for controlling and checking the CPU governor disappeared with it. How do I get them back? </proc/cpufreq> has also disappeared.

---

### Post by xx404 on 2005-09-05
I've managed to get the /sys directories back by editing my /etc/modules file and adding the speedstep_smi, proc_intf and cpufreq_userspace modules to it. I've also edited /etc/acpi/power.sh so that it now invokes cpuspeedy min when the power cable is unplugged and calls cpuspeedy max when the cable is plugged in again.

It's all a bit painful and has taken far too much research. Hopefully future versions of Linux/Ubuntu will have more user friendly tools for setting these kinds of things up. Spending hours searching and reading on the Internet for stuff that should just work in a modern OS is pretty crazy. Lucky I'm in the mood for it :)

---

### Post by tombeharrell on 2005-09-20
This problem (loading the wrong speedstep driver) is fixed in a new powernowd package available at:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=15788](http://bugzilla.ubuntu.com/show_bug.cgi?id=15788)

- edit - 
this is a fix for the Breezy Badger version, I just noticed this message is in Hoary.

---

