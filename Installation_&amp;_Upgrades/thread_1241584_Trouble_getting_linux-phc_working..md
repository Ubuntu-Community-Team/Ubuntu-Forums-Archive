---
title: "Trouble getting linux-phc working."
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by elldirash on 2009-08-16
I am trying to undervolt my T8100 Core2 Duo laptop and have tried to follow the Howto given on the Linux-PHC forum:

[http://www.linux-phc.org/forum/viewtopic.php?f=13&t=67](http://www.linux-phc.org/forum/viewtopic.php?f=13&t=67)

I am aware that a lot of threads about this topic already exists in this forum. However all of the Howto's seem to assume that the acpi_cpufreq or the speedstep_centrino modules will be running after the kernel recompile.

After thoroughly following the guide 4 times (trying to figure out what i am doing wrong) for a total of about 12 hours of compiling i thought it would be about time to check if someone else is having the same problems.

After recompiling and installing the modified kernel it seems that phc is not recompiled as a module:

lsmod | grep acpi_cpufreq                  gives no output.
lsmod | grep speedstep_centrino         gives no output.

The command:

sudo modprobe phc-intel                  can be run without errors, but afterwards

lsmod | grep phc-intel                     no output.

Any help would be appreciated!

---

### Post by JesVestervang on 2010-03-30
I know I'm replying to an old post, but well...

The reason you don't see the modules probably is that they are compiled into the kernel. You can check if it's the case by looking at the compilation configuration which resides in /boot:

```

$ grep -i acpi_cpufreq /boot/config*
/boot/config-2.6.32-16-generic:CONFIG_X86_ACPI_CPUFREQ=y
/boot/config-2.6.32-17-generic:CONFIG_X86_ACPI_CPUFREQ=y
```

The 'y' should have been an 'm' if it should have been compiled as a module.

---

