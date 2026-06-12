---
title: "Laptop CPU scaling not allowing full speed"
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by adamklempner on 2007-06-15
I have an HP laptop with an AMD Athlon-M 1600+ that should have available scaling frequencies of:
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies:
```
1391407 1192635 1060120 927605 662575 
```

But it never goes above 927 MHz, the second scaling step.  I have tried with Gimp and superpi to load the processor up so it runs at full speed, but it just won't.  Here are the stats:

/sys/devices/system/cpu/cpu0/cpufreq/stats/time_in_state
```
1391407 0
1192635 0
1060120 0
927605 46714
662575 220558
```

Any idea on how I can make Kubuntu 7.04 run the CPU full speed?  Edgy did it no problem.  Is there some sort of limitation that has been set somewhere?

Thanks.

---

### Post by adamklempner on 2007-06-15
So I think i have found the problem but I can't seem to fix it.  The file /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq is set to 1050000 or 1.05 GHz (less than one step above the 927MHz that I have).  I think this is why my processor never goes above the 927 MHz step.

The problem is I can't seem to edit this file for some reason.

sudo nano scaling_max_freq 

allows me to change the number, after saving it imediately gets set back to 1050000 (or maybe it just never saves it).

How can I change the value in:
/sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq ?

It should be set to the max frequency the processor is capable of, correct?

Thanks

---

### Post by revertex on 2007-06-18
```
sudo echo "value" >  /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
```

---

### Post by adamklempner on 2007-06-18
How can sudo not have permission?

```
adamk@ark:~$ sudo echo 1391408 >  /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
bash: /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq: **Permission denied**
adamk@ark:~$

```

---

### Post by DagMan on 2007-06-18
try doing 
sudo su
and then doing it again.  It still might not let you and I sort of doubt it,  I think it's actually trying to toss a value into the kernel that the module isn't loaded to handle.  It could be that you need to load the module with an option specified or that you need to use a differant module entirely.  I don't know if that's accurate but it's another approach to look at it from if all else fails.

---

### Post by Austin_KW on 2007-06-18
> **adamklempner said:**
> How can sudo not have permission?

```
adamk@ark:~$ sudo echo 1391408 >  /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
bash: /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq: **Permission denied**
adamk@ark:~$

```

It runs "echo 1391408" as root
then ">" redirects the output from the echo command to the file, but I think this redirection occurs back within you user context, not as root.

You can get around this limitation by running the whole thing as root in a single shell (eg bash) command

sudo  bash -c "echo 1391408 >  /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq"

---

### Post by adamklempner on 2007-06-18
> **Austin_KW said:**
> It runs "echo 1391408" as root
then ">" redirects the output from the echo command to the file, but I think this redirection occurs back within you user context, not as root.

You can get around this limitation by running the whole thing as root in a single shell (eg bash) command

sudo  bash -c "echo 1391408 >  /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq"

Thanks, that got around the permission problem, however it didn't actually change the value in that file.  Immediately after that command I did a "nano /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq" and the file still only had 1050000 in it.

Any idea why?

---

### Post by Austin_KW on 2007-06-18
Not sure about the amd scaling

What is the output of cpufreq-info

Or alternatively, what is the available and actual governor (files in the same directory)

---

### Post by TubaTodd on 2007-06-18
Try using this applet to set your CPU scaling

[http://gfreqlet.sourceforge.net/](http://gfreqlet.sourceforge.net/)

Use the Performance option to use MAX CPU speed. I don't know if this helps, but it may be a start.

---

### Post by adamklempner on 2007-06-18
Setting it to "performance" just maxes it at 928Mhz which can be seen in the cpufreq-info below:

```
adamk@ark:~$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: powernow-k7
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 663 MHz - 1.39 GHz
  available frequency steps: 1.39 GHz, 1.19 GHz, 1.06 GHz, 928 MHz, 663 MHz
  available cpufreq governors: ondemand, powersave, conservative, userspace, performance
  current policy: frequency should be within 663 MHz and 1.05 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 928 MHz.
adamk@ark:~$

```
 
It has got to be that stupid "scaling_max_freq" file which is set to 1.05 GHz that has to be messing it all up...  I don't why that number is in there, and I really wish I could change it...

---

### Post by Christian Helmuth on 2007-06-19
Did you check the file /etc/default/cpufrequtils? Esp. the MAX_SPEED value...

---

### Post by adamklempner on 2007-06-19
/etc/default/cpufrequtils:

```
ENABLE="true"
GOVERNOR="ondemand"
MAX_SPEED=1391439
MIN_SPEED=662590
```

That all seems fine.

---

### Post by adamklempner on 2007-06-20
Anyone have any other ideas as to why I can't change:
/sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq ?

Thanks.

---

### Post by Unicast on 2007-06-20
I had exactly the same issue with a Dell D400 1.7Ghz Intel PentiumM. In the end I had to recompile the whole kernel.

Just found my original thread here: [http://www.ubuntuforums.org/showthread.php?t=283060](http://www.ubuntuforums.org/showthread.php?t=283060)

Hope this helps you more than it helped me. I found that this would work perfectly most of the time, but I'd still get the occasional scaling_max_freq = scaling_min_freq. Very annoying! I never did find a fix that worked 100% of the time. But you never know it might just work for you! ;)

---

### Post by adamklempner on 2007-06-20
> **Unicast said:**
> I had exactly the same issue with a Dell D400 1.7Ghz Intel PentiumM. In the end I had to recompile the whole kernel.

I am reluctantly compiling now.  We'll see how it goes. :-k

---

### Post by Adahn on 2007-07-04
I encountered this issue, but it's related to my overclocked cpu.
I can't edit that 'max-cpu' file either, and it's fixed to the 'rated' speed of the cpu, not what I have it set in bios.

---

### Post by dave-5B on 2008-06-25
i am having the same problem (i think) on a thinkpad r61 with and intel c2d, output of cpufreq-info is:

> 
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.80 GHz
  available frequency steps: 1.80 GHz, 1.80 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: userspace, conservative, powersave, ondemand, performance
  current policy: frequency should be within 800 MHz and 1.20 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1.20 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.80 GHz
  available frequency steps: 1.80 GHz, 1.80 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: userspace, conservative, powersave, ondemand, performance
  current policy: frequency should be within 800 MHz and 1.20 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1.20 GHz.


/sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq is
> 
david@serafina:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq 
1200000

absolutely NOTHING i have tried will change the "current policy" to allow more than 1.2GHz
it was working fine on gutsy, what gives?
i am running on the generic kernel but have the ubuntustudio rt kernel installed, surely i dont have to recompile my kernel?

---

