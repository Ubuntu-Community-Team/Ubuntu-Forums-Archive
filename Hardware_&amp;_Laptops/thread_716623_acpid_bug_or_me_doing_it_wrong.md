---
title: "acpid bug or me doing it wrong?"
date: 2008-03-06
forum: Hardware &amp; Laptops
---

### Post by larsemil on 2008-03-06
I just made a debootstrap install of ubuntu on my eeepc and everything works perfectly. I am so satisfied. Allthough i have a little problem:

i want to install acpid. it installs just fine but it does not get started.

```

larsemil@ubuntu:~$ sudo apt-get install -f
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
0 uppgraderade, 0 nyinstallerade, 0 att ta bort och 0 ej uppgraderade.
3 ej helt installerade eller borttagna.
Behöver hämta 0B arkiv.
Efter uppackning kommer ytterligare 0B utrymme användas på disken.
Ställer in acpid (1.0.4-5ubuntu8) ...
 * Loading ACPI modules...                                                                [ OK ] 
 * Starting ACPI services...                                                                     invoke-rc.d: initscript acpid, action "start" failed.
dpkg: fel vid hantering av acpid (--configure):
 underprocess post-installation script gav felkod 1
dpkg: beroendeproblem förhindrar konfigurering av acpi-support:
 acpi-support beror på acpid (>= 1.0.4-1ubuntu4), men:
  Paketet acpid har inte konfigurerats ännu.
dpkg: fel vid hantering av acpi-support (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av powermanagement-interface:
 powermanagement-interface beror på acpi-support (>= 0.17), men:
  Paketet acpi-support har inte konfigurerats ännu.
dpkg: fel vid hantering av powermanagement-interface (--configure):
 beroendeproblem - lämnar okonfigurerad
Fel uppstod vid hantering:
 acpid
 acpi-support
 powermanagement-interface
E: Directory '/var/log/apt/' missing
E: Sub-process /usr/bin/dpkg returned an error code (1)
larsemil@ubuntu:~$ 


```


and when trying to start acpid manually i get another error:
```

larsemil@ubuntu:~$ sudo invoke-rc.d acpid start
 * Loading ACPI modules...                                                                [ OK ] 
 * Starting ACPI services...                                                                     invoke-rc.d: initscript acpid, action "start" failed.


```

i dont know what to do with this. any ideas?

---

### Post by larsemil on 2008-03-06
oh and modprobe acpi gives
> 
larsemil@ubuntu:~$ sudo modprobe acpi
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.22-14-generic/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device


should i use the linux-image-2.6.22-14-386 instead of the generic one?

---

### Post by larsemil on 2008-03-06
on the other hand i seem to have this on my desktop as well so maybe the packages are not necassary?

what i do want is the settings in gnome-power-manager about "set screen to 75% brightness when on battery power" and this i dont have now...

---

