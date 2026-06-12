---
title: "CPU Scaling problems on Celeron M 440"
date: 2009-12-22
forum: Hardware
---

### Post by nicholas on 2009-12-22
I've got a fresh install of Karmic on an HP530 laptop which has is giving me problems with CPU frequency scaling.

I added p4_clockmod to /etc/modules as the gnome cpu frequency scaling applet said my cpu didn't support scaling.

This had the desired effect of allowing the applet to work, or almost work that is.

I couldn't change the scaling governor using the applet or manually via the command line.

I installed powernowd and when running on battery power the applet shows the cpu speed scaling up and down depending on the load, between 233MHz and 1.87GHz. Great so far!

However, if I suspend the laptop to ram or disk, or connect AC power and then  go back to battery, the applet shows that the scaling is no longer working correctly and just sits at 1.87GHz unless I restart the powernowd daemon from the command line.

> sudo echo ondemand>/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

bash: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: Permission denied

dmesg output gives:
> 
[ 3103.980776] ondemand governor failed, too long transition latency of HW, fallback to performance governor

So, to try and automate the powernowd daemon restarting on power/sleep events I created a script named 99-powernow and ran:

```
chmod +755 99-powernow
sudo install 99-powernow /etc/pm/sleep.d
sudo install 99-powernow /etc/pm/power.d

```

The script contains the commands:

```
#!/bin/sh

if on_ac_power; then

  /usr/sbin/service powernowd restart
  echo power>>/home/nicholas/itworks.txt

else

  /usr/sbin/service powernowd restart
  echo battery>>/home/nicholas/itworks.txt

fi

```

The 99-powernow script definitely executes when the power is changed to battery-only as the text file successfully shows the word 'battery' in the itwork.txt file and it definitely executes when returning to ac power as it successfully echoes the word 'power' to the same file. 

What doesn't happen is cpu scaling re-starting on connection of ac power or on removal of ac power.

Yet manually issuing 'sudo /sbin/service powernowd restart' works a treat, and so does 'sudo /etc/init.d/powernowd restart'.


When running on battery power, resuming from an 's2ram --force'* suspend makes the script echo 'battery' to the text file 4 times for some reason but the cpu scaling seems to stay intact and functional.

When running on ac power, resuming from an 's2ram --force'* suspend makes the script echo 'power' to the text file 4 times, but the cpu stays stuck at the full 1.87GHz, but i'm not to bothered about scaling working when on ac power for now.

Can anyone see what I am doing wrong here?

Thanks in advance! :)


* I use 's2ram --force' from a modified '/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux' so that the buttons in gnome etc work correctly.

---

### Post by 00b00nt00 on 2009-12-23
Sorry, but the processor just doesn't support frequency scaling:

[http://ark.intel.com/Product.aspx?id=27151](http://ark.intel.com/Product.aspx?id=27151)

---

### Post by nicholas on 2009-12-23
> **00b00nt00 said:**
> Sorry, but the processor just doesn't support frequency scaling:

[http://ark.intel.com/Product.aspx?id=27151](http://ark.intel.com/Product.aspx?id=27151)

It does when the p4_clockmod module is loaded and also works perfectly with Windows XP and Vista on the same machine.

Thanks for the link, it seems that it is EIST that the CPU doesn't support.

```
sudo powertop -d
```

> 
Cn              Avg residency
C0 (cpu running)        ( 7.4%)
C0                  0.0ms ( 0.0%)
C1 halt            0.0ms ( 0.0%)
C2                  0.0ms ( 0.0%)
C3                  7.7ms (92.6%)

P-states (frequencies)
  1.87 Ghz     3.6%
  1400 Mhz     2.3%
   700 Mhz     2.3%
   467 Mhz     2.2%
   233 Mhz    83.1%

Powertop clearly shows the 4 p-states that the cpu can be throttled to when powernowd is active.  Without powernowd loaded, powertop doesn't display any P-states whatsoever.

```
cat /proc/cpuinfo
```
> processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 14
model name    : Intel(R) Celeron(R) M CPU        440  @ 1.86GHz
stepping    : 12
cpu MHz        : 1866.662
cache size    : 1024 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx constant_tsc up arch_perfmon bts pni monitor tm2 xtpr pdcm
bogomips    : 3724.37
clflush size    : 64
power management:

The powermanagement field is empty which (along with the clear lack of C-state support shown in powertop) confirms that EIST isn't available.

What is strange however is that upon installing the KDE4 Guidance Powermanager tray-applet, the CPU switches between 'Performance' and 'Dynamic' mode when swapping between ac power and battery.

This only seems to work however if the GNOME Power Manager tray-applet is also running at the same time as Guidance Power Manager.  Neither works correctly on its own but when both are running together, then Guidance successfully manages to let powernowd change the CPU speed dynamically dependent upon load.

I have no idea why this combination works the way it does though.

Any ideas?

---

### Post by mahela007 on 2009-12-29
I have a similar problem... 
I've installed ubuntu 9.10 on a IBM laptop using a Celeron M processor. When I start the computer, and boot into Ubuntu for the first time, CPU scaling seems to work. However, after a few seconds, I get a 'kernel error' report from the applet in the gnome-panel and CPU scaling seems to break down. After the error occurs, the CPU frequency is just stuck at the maximum (1.5 GHz for my processor).
After all this, if I click on the frequency selecting applet and select a frequency, it asks me for my password and then CPU scaling SEEMS to work again. However, it doesn't change frequency as frequently as before the error occured.... Most of the time, it's running at full throttle. Any suggestions or theories about what's wrong?

---

