---
title: "Disc activity - what's cuasing it?"
date: 2008-01-27
forum: Hardware &amp; Laptops
---

### Post by stdPikachu on 2008-01-27
I've just finished setting up my first Mythbuntu box, and very nice it is too.

But the hard drive light is flashing about twice a second and I'm not really sure why. On my previous setup (Gentoo) once the OS had finished booting and loading Myth, the HDD would only be active for writing things like log files once in a blue moon, allowing the discs to spin down (it's using a laptop hard drive with the timeout set to 30m). But when I run things like top, powertop and lm-profiler I can't see any obvious contenders:
```
banquo@banquo:~$ sudo lm-profiler
[sudo] password for banquo:
Profiling run started.
Write accesses at 119/600 in lm-profiler run: apt-get
Read accesses at 119/600 in lm-profiler run: apt-get
Write accesses at 120/600 in lm-profiler run: apt-get
Read accesses at 121/600 in lm-profiler run: apt-get dpkg-preconfigu http locale
 sh
Read accesses at 122/600 in lm-profiler run: apt-extracttemp apt-get dpkg dpkg-d
eb dpkg-preconfigu dpkg-split sh stty tar
Read accesses at 123/600 in lm-profiler run: dpkg
Read accesses at 124/600 in lm-profiler run: dpkg
Read accesses at 125/600 in lm-profiler run: dpkg
Read accesses at 126/600 in lm-profiler run: dpkg
Read accesses at 127/600 in lm-profiler run: dpkg
Read accesses at 128/600 in lm-profiler run: dpkg
Read accesses at 129/600 in lm-profiler run: dpkg
Read accesses at 130/600 in lm-profiler run: dpkg
Read accesses at 131/600 in lm-profiler run: dpkg
Write accesses at 132/600 in lm-profiler run: dpkg
Read accesses at 132/600 in lm-profiler run: dpkg
Write accesses at 133/600 in lm-profiler run: dpkg
Read accesses at 133/600 in lm-profiler run: dpkg
Read accesses at 134/600 in lm-profiler run: apt-get
Read accesses at 179/600 in lm-profiler run: eject
Read accesses at 182/600 in lm-profiler run: thunar-volman
Profiling run completed.
```
I installed something and ejected a DVD whilst it was running to see what events were generated and they're the only things visible here. Does lm-profiler only acknowledge writes? Haven't actually enabled laptop mode powersave yet, was going to see if I could get to the bottom of the disc accesses first.

Similarly, powertop doesn't show anything odd either:
```
                                      P-states (frequencies)
                                        2.21 Ghz     0.0%
                                        2.00 Ghz     0.0%
                                        1.80 Ghz     0.0%
                                        1000 Mhz   100.0%
< Detailed C-state information is only available on Mobile CPUs (laptops) >

Wakeups-from-idle per second : 627.8    interval: 10.0s
no ACPI power usage estimate available

Top causes for wakeups:
  20.7% (101.1)       <interrupt> : cx88[0], cx88[0]
  20.6% (100.8)       <interrupt> : ohci_hcd:usb1, eth0
  17.3% ( 84.4)       mythbackend : schedule_timeout (process_timeout)
  15.1% ( 73.6)   mythfrontend.re : schedule_timeout (process_timeout)
  12.5% ( 61.0)       <interrupt> : nvidia
   7.4% ( 36.2)       <interrupt> : sata_nv
```
~600 wakeups per second is pretty good going for a desktop system IME, my laptop gets about ~400 on a good day and it's not running any network-enabled services.

On a related note, when the system goes into hibernate it seems to wake up fine but the TV (connected by DVI) still shows "no signal", making the whole thing a bit pointless. Does anyone know any workarounds for intransigent TV's?

---

