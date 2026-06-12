---
title: "Disable ethernet port"
date: 2009-07-07
forum: Hardware
---

### Post by skintythe1andonly on 2009-07-07
Hi, I am currently troubleshooting a warmer laptop since the upgrade to jaunty. I posted about this in [http://ubuntuforums.org/showthread.php?p=7577819#post7577819]("http://ubuntuforums.org/showthread.php?p=7577819#post7577819") but thought i might need its own thread as I think its a separate issue to everyone else there.

I used powertop to see what was using all my power as I have seen reduction in battery life since the upgrade. I get the following
```
Wakeups-from-idle per second : 175.2    interval: 10.0s
no ACPI power usage estimate available

Top causes for wakeups:
  38.2% (100.6)       <interrupt> : eth0 
  16.4% ( 43.2)      <kernel IPI> : Rescheduling interrupts 
  15.9% ( 41.9)       firefox-3.5 : futex_wait (hrtimer_wakeup) 
  10.9% ( 28.6)       <interrupt> : extra timer interrupt 
   4.0% ( 10.5)       <interrupt> : pata_amd 
   3.2% (  8.4)       <interrupt> : PS/2 keyboard/mouse/touchpad
   2.4% (  6.4)       <interrupt> : eth1
   2.3% (  6.0)    wpa_supplicant : wl_add_timer (wl_timer)
   2.2% (  5.8)     <kernel core> : hrtimer_start (tick_sched_timer)
   1.0% (  2.7)       compiz.real : schedule_hrtimeout_range (hrtimer_wakeup)
   0.7% (  1.8)       <interrupt> : sata_nv, mmc0
```

As you can see eth0 is the main cause of the wake ups. This is my ethernet port and my wireless is eth1. I want to disable eth0 to see if this reduces the extra heating.

I tried 
```
chris@skint-laptop:~$ sudo ifdown eth0
[sudo] password for chris: 
ifdown: interface eth0 not configured

```

yet it works if i plug in a cable. I have tried the package ifplugd but this does not have an effect either. Looking around on google brought me to [http://www.linuxquestions.org/questions/linux-newbie-8/howto-disable-eth0-at-boot-time-65768/]("http://www.linuxquestions.org/questions/linux-newbie-8/howto-disable-eth0-at-boot-time-65768/") but ubuntu does not seem to have a /etc/sysconfig folder so I am lost. Any ideas how to cut the power to eth0 or at least reduce the wake-ups

---

### Post by skintythe1andonly on 2009-07-07
Btw my current /etc/network/interfaces looks like this

```
auto lo
iface lo inet loopback

```

if i could manually disable it from here that would be great

---

