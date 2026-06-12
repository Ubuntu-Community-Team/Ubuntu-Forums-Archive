---
title: "Loss of Frequency scaling"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by danbert on 2006-10-20
I just upgraded my laptop to the edgy release candidate, and for some reason, the kernel update notifies me that I no longer have support for CPU scaling.  This is quite a problem, as my CPU now runs at full speed all the time, making my laptop quite warm (hotter than hell) all the time.  I tried switch back to my old kernel, but CPU scaling doesn't work on it now either.  Any suggestions would be greatly appreciated.

Error message is as follows:

CpuFreq support not available.  Check sysfs is mounted and your CPU-specific module is loaded or built into the kernel.

I have a Pentium M 2.0 Ghz processor.

---

### Post by Kateikyoushi on 2006-10-21
I have the same CPU and works, which kernels did you try ?
Maybe you can set it up manually.[LINK]("http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling")

---

### Post by benhall on 2006-10-21
Check the version of the kernel you are using. When I upgraded from dapper to edgy I lost scaling, smp etc. I was surprised to learn that there are actually two generic kernels- i386 and generic, and i386 was installed by default. i386 lacks many useful features, and is booted in preference to generic so I found it best to install generic and (after testing) remove i386. I'm not sure why there are two generic x86 kernels.

---

### Post by omschaub on 2006-10-21
I lost scaling as well and I am now using 2.6.17-10-generic -- with absolutely no luck

---

### Post by danbert on 2006-10-21
Yeah, I just installed the generic kernel, and no luck for me either.  I guess my laptop will just continue to burn my manhood :(

---

### Post by lechroom on 2006-10-21
Same here, just upgraded from Dapper to Egdy RC and no more CPU frequency scaling. My CPU is a Pentium M 1.6.

The only available governor is "performance".
The /boot/config-2.6.17.10-386 has this relevant part:
```
#
# CPU Frequency scaling
#
CONFIG_CPU_FREQ=y
CONFIG_CPU_FREQ_TABLE=m
# CONFIG_CPU_FREQ_DEBUG is not set
CONFIG_CPU_FREQ_STAT=m
CONFIG_CPU_FREQ_STAT_DETAILS=y
CONFIG_CPU_FREQ_DEFAULT_GOV_PERFORMANCE=y
# CONFIG_CPU_FREQ_DEFAULT_GOV_USERSPACE is not set
CONFIG_CPU_FREQ_GOV_PERFORMANCE=y
CONFIG_CPU_FREQ_GOV_POWERSAVE=m
CONFIG_CPU_FREQ_GOV_USERSPACE=m
CONFIG_CPU_FREQ_GOV_ONDEMAND=m
CONFIG_CPU_FREQ_GOV_CONSERVATIVE=m

#
# CPUFreq processor drivers
#
CONFIG_X86_ACPI_CPUFREQ=m
CONFIG_X86_POWERNOW_K6=m
CONFIG_X86_POWERNOW_K7=m
CONFIG_X86_POWERNOW_K7_ACPI=y
CONFIG_X86_POWERNOW_K8=m
CONFIG_X86_POWERNOW_K8_ACPI=y
CONFIG_X86_GX_SUSPMOD=m
CONFIG_X86_SPEEDSTEP_CENTRINO=m
CONFIG_X86_SPEEDSTEP_CENTRINO_ACPI=y
CONFIG_X86_SPEEDSTEP_CENTRINO_TABLE=y
CONFIG_X86_SPEEDSTEP_ICH=m
CONFIG_X86_SPEEDSTEP_SMI=m
CONFIG_X86_P4_CLOCKMOD=m
CONFIG_X86_CPUFREQ_NFORCE2=m
CONFIG_X86_LONGRUN=m

#
# shared options
#
# CONFIG_X86_ACPI_CPUFREQ_PROC_INTF is not set
CONFIG_X86_SPEEDSTEP_LIB=m
```

---

### Post by lechroom on 2006-10-21
OK, found a workaround.

For some reason the cpufreq_ondemand module wasn't loaded. I manually added it to /etc/modules and it's now used by default.

---

### Post by danbert on 2006-10-22
I am still not getting frequency scaling to work.  I checked my boot config file and it says that it is enabled, I have powersave installed, I am using the generic kernel, and still no luck.

Any more suggestions would be great.

---

### Post by omschaub on 2006-10-22
lechroom's workaround did not work for me either :(

I am in the same boat as you danbert... powersave, generic kernel, etc... no scaling :(

---

### Post by lechroom on 2006-10-22
The powersave governor seems to have strange behaviours according to some reports here and other forums. Did you try the ondemand one?

---

### Post by omschaub on 2006-10-22
Ah.. you were right.. I uninstalled powersaved and installed powernowd (couldn't find ondemand in my repositories) and 'poof'.. instant results!  Thanks from my end! :cool:

---

### Post by danbert on 2006-10-24
I have tried both powersaved and powernowd.  Neither have worked for me.  However I tried running powernowd and reading the error message, I think the problem is that in my /sys/devices/system/cpu/cpu0 directory only contains an unreadable crash_notes file.  Nothing else is in there, and powernowd looked for frequency options in this folder.  Any ideas why this directory is empty?

EDIT:
I tried creating the directory, and even with sudo, I got the error message that creating a directory here is not permitted.

---

### Post by cparker71 on 2006-10-30
On my dell laptop inspiron 5160,I also lost cpu frequency scaling when I upgraded from dapper to edgy. 

Installing the generic kernel fixed it for me.  With the 386 kernel, the
/sys/devices/system/cpu/cpu0/cpufreq/ didn't exist.  Using the generic kernel, this path does exist.

To install the generic kernel, I just:
sudo apt-get install linux-image-2.6.17-10-generic

FYI, I also had to install the linux-restricted-modules-2.6.17-10-generic package to get nvidia driver to work with the generic kernel.

There might be a dependency missing there.

CP

---

### Post by lassegs on 2006-10-30
I had the same problem, tried some of your tips and tricks here, but it didnt work. Reinstalled powernowd, and read the manual (first time I found an answer in a manual) and started it with 
sudo powernowd -m 1
that enabled aggressive cpu-scaling. Im going to try this mode for a while, then test the other two modes (passive and leaps).

I dunno if this works for anyone, but I hope your solution is as easy as mine.

---

