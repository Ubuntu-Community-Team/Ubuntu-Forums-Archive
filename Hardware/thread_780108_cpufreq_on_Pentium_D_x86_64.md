---
title: "cpufreq on Pentium D x86_64?"
date: 2008-05-03
forum: Hardware
---

### Post by aseering on 2008-05-03
Hi,
    I have a Pentium D-based desktop that runs a bit hot; I'm trying to cut fan speeds by enabling power-management features.

    Does anyone know what cpufreq driver (.ko), if any, will enable frequency scaling support for a Pentium D 820 processor?  I know I've adjusted the frequency manually before (though I never bothered to set up powernowd or the like), with some previous Linux distro/install that I've tried on this machine.

    It looks like Ubuntu installs very few cpufreq drivers by default for x86_64 (only acpi-cpufreq and powernow-k8, both of which complain "No such device" when modprobe'd); is there some package that contains more of them, or do I have to compile a custom kernel to get them?

Adam

---

