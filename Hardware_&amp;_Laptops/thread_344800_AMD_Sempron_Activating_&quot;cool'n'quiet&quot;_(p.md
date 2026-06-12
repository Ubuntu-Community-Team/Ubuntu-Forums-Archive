---
title: "AMD Sempron: Activating &quot;cool'n'quiet&quot; (powersave)"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by ranarion on 2007-01-23
Hello everyone,

I've got an AMD Sempron on a PCChips M863G mainboard. I tried following several Howtos (e.g. [http://ubuntuforums.org/showthread.php?t=248867]("http://ubuntuforums.org/showthread.php?t=248867") ) in order to get its power management working, but did not succeed.

I am using a "server" installation off Dapper's alternate CD, but got the exact same results with the standard desktop install.

I can't insert any of the modules mentioned in the Howto I linked above. I get the following error:

```
FATAL: Error inserting powernow_k7 (/lib/modules/2.6.15-27-386/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k7.ko): No such device
```

The path is, however, correct; and there's an appropriately named module there. In another posting, I read that this was a result of using older versions of the k7 kernel. So, as you see in the error message, I switched to the most current 386 kernel, but this didn't help solve the issue.

Any ideas?

---

### Post by OffHand on 2007-01-23
Did you enable it in the bios?

---

### Post by ranarion on 2007-01-23
There is no option to explicitly enable/disable it in the BIOS (just a general "Power Management/APM" option, which is enabled), but the manual states that cool'n'quiet is supported, so I assume it is. Is there any way to check this (somewhere in /proc, perhaps)?

---

### Post by OffHand on 2007-01-23
I can control frequency scaling on my desktop (amd 3500+) with the following command:
```
sudo /etc/init.d/powernowd start
```
```
sudo /etc/init.d/powernowd stop
```
```
sudo /etc/init.d/powernowd restart
```

---

### Post by ranarion on 2007-01-23
Sure, your cpufreq setup works, so you can of course do that :-) My problem is one step below the point powernowd, cpufreqd or cpudyn would act: the kernel support for CPU scaling is not working. Hence, when I give those commands, I get
```

admin@stockert01:~$ sudo /etc/init.d/powernowd start
 * Starting powernowd...                                                         
 * CPU frequency scaling not supported
                                                                         [ ok ]

```

---

### Post by ranarion on 2007-01-25
Hmm, I forgot one thing: does anyone know of a possible bug in the -386 kernel that is similar to that in the -k7 kernel? I could not find anything in the bugtracker, but I don't know what else to check...

---

### Post by huygens on 2007-05-15
Ranarion, did you find a solution to your problem?
I have also the same issue. I have a Sempron 64 ( K8 ) which AMD says to be Cool'n'Quiet compatible. The motherboard is also compatible and has the feature enabled in the BIOS.

When I load the module powernow-k8 I get the same error as you and dmesg reports:
```
powernow-k8: Power state transitions not supported
```

---

### Post by ranarion on 2007-05-21
No, unfortunately not. I would still be interested in hearing from anyone who solved this. (Meanwhile, I simply switched to a different board for that machine, but anyway...)

---

### Post by huygens on 2007-05-30
I have found out that my Sempron does not support the Cool'n'Quiet technology, even though AMD states otherwise on its web site...
sigh
:(

---

