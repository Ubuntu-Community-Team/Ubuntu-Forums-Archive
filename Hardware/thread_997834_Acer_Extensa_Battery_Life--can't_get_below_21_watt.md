---
title: "Acer Extensa Battery Life--can't get below 21 watts"
date: 2008-11-30
forum: Hardware
---

### Post by conjunctivitis on 2008-11-30
Hello,

I'm sorry, I realize this is a widely treated topic and I have tried using vor's scripts [http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773), including disabling USB and enabling PCI power saving, but I haven't seen much in the way of results.  With the display on minimum and wireless switched off and no programs open, Powertop gives me around 21-22 watts.  When I look at the Power History, there are brief dips into 17-18 watts at the AC-disconnection event, but it gets right back up to 21 watts right after.

I'm using 8.10 with the .9 kernel and my system is AMD Ahtlon 64 x2 1.9 Ghz with 2 gigs RAM, ATI Radeon video card (using proprietary drivers).

In Powertop, I see that the processors are at 800 Mhz 100% of the time, and this seems to conflict with [http://mjg59.livejournal.com/88608.html](http://mjg59.livejournal.com/88608.html).  Being an AMD processor, I can't get Cstate info.

In Vista, I got around 2.5 hours, with Ubuntu after tweaks around 2 hours.


Thanks in advance

---

### Post by binbash on 2008-11-30
did you read everything here : [http://www.lesswatts.org/](http://www.lesswatts.org/) ?

---

### Post by conjunctivitis on 2008-11-30
Yes.  A lot of it is pretty intimidating for beginners (me).  My foggy understanding of it suggests that many of the tips, such as wireless power saving and C state management are applicable only to Intel processors/chipsets (?), in which case they won't be helpful to me.

I assumed that most of those suggested settings are already incorporated into vos's scripts, but maybe I'm wrong.  

Does anyone else with this notebook have an idea of what kind of battery life is possible

Thanks.

---

### Post by iggykoopa on 2008-11-30
If you don't mind testing it out you could try my gui and see if you get better results. Thread is here [http://ubuntuforums.org/showthread.php?t=988309](http://ubuntuforums.org/showthread.php?t=988309) . It's still in development but it may help.

edit: also you said you tried pcie aspm, did you compile your own kernel? the default ubuntu kernel has that turned off.

---

### Post by conjunctivitis on 2008-11-30
No I didn't.  I'm kind of frightened of the idea, but if it's not that complicated, I would be willing to try compiling a power-saving kernel (is such a thing possible?).  I have been checking out your script but have yet to figure out how to install it.  Do I need to download manually or can I install it through console commands?  Thanks

---

### Post by conjunctivitis on 2008-11-30
figured out the installation.  sorry, i'm really a beginner.  i'll let you know my results...

---

### Post by iggykoopa on 2008-11-30
yeah it doesn't actually have an installer yet since it is still in development, once I get everything ironed out I'm making one. Also look in that thread for the link on kernelcheck, makes it relatively simple to compile your own kernel... theres just a ton of options and you need to learn which ones are safe to turn off and on.

---

### Post by conjunctivitis on 2008-11-30
ok, i ran your script in basic mode and then checked the results with powertop:

dan@dan-laptop:~$ acpi
     Battery 0: Discharging, 92%, 00:02:16 remaining
dan@dan-laptop:~$ sudo powertop -d -t 60
PowerTOP 1.10    (C) 2007, 2008 Intel Corporation 

Collecting data for 60 seconds 


< Detailed C-state information is not available.>
P-states (frequencies)
  1.91 Ghz     0.0%
  1.80 Ghz     0.0%
  1.60 Ghz     0.0%
   800 Mhz   100.0%
Wakeups-from-idle per second : 26.8	interval: 60.0s
Power usage (ACPI estimate): 20.6W (2.3 hours) 
Top causes for wakeups:
  30.9% ( 11.3)           firefox : futex_wait (hrtimer_wakeup) 
  26.3% (  9.6)       <interrupt> : acpi 
  11.3% (  4.1)       <interrupt> : extra timer interrupt 
   8.9% (  3.2)      <kernel IPI> : Rescheduling interrupts 
   4.6% (  1.7)    gnome-terminal : schedule_timeout (process_timeout) 
   3.4% (  1.2)     <kernel core> : wl_add_timer (wl_timer) 
   2.7% (  1.0)        atieventsd : schedule_timeout (process_timeout) 
   1.7% (  0.6)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_timer) 
   1.4% (  0.5)        pulseaudio : schedule_timeout (process_timeout) 
   1.4% (  0.5)   hald-addon-stor : schedule_timeout (process_timeout) 
   0.9% (  0.3)       <interrupt> : ahci 
   0.9% (  0.3)      <kernel IPI> : function call interrupts 
   0.8% (  0.3)   gnome-power-man : schedule_timeout (process_timeout) 
   0.7% (  0.3)       gnome-panel : schedule_timeout (process_timeout) 
   0.7% (  0.2)   <kernel module> : neigh_table_init_no_netlink (neigh_periodic_timer) 
   0.5% (  0.2)            python : schedule_timeout (process_timeout) 
   0.5% (  0.2)   update-notifier : schedule_timeout (process_timeout) 
   0.5% (  0.2)    NetworkManager : schedule_timeout (process_timeout) 
   0.4% (  0.1)              Xorg : schedule_timeout (process_timeout) 
   0.3% (  0.1)              Xorg : do_setitimer (it_real_fn) 
   0.1% (  0.1)     <kernel core> : queue_delayed_work (delayed_work_timer_fn) 
   0.1% (  0.0)      <kernel IPI> : TLB shootdowns 
   0.1% (  0.0)            kacpid : schedule_timeout (process_timeout) 
   0.1% (  0.0)              hald : schedule_timeout (process_timeout) 
   0.1% (  0.0)          gconfd-2 : schedule_timeout (process_timeout) 
   0.1% (  0.0)           syslogd : do_setitimer (it_real_fn) 
   0.0% (  0.0)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   0.0% (  0.0)     <kernel core> : __enqueue_rt_entity (sched_rt_period_timer) 
   0.0% (  0.0)     <kernel core> : laptop_io_completion (laptop_timer_fn) 
   0.0% (  0.0)              cron : do_nanosleep (hrtimer_wakeup) 
   0.0% (  0.0)     <kernel core> : rif_init (rif_check_expire) 
   0.0% (  0.0)     <kernel core> : inet_initpeers (peer_check_expire) 
   0.0% (  0.0)     <kernel core> : addrconf_verify (addrconf_verify) 

Suggestion: Enable SATA ALPM link power management via: 
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
or press the S key.

Suggestion: Disable 'hal' from polling your cdrom with:  
hal-disable-polling --device /dev/cdrom 'hal' is the component that auto-opens a
window if you plug in a CD but disables SATA power saving from kicking in.

Recent USB suspend statistics
Active  Device name
  0.0%	USB device usb5 : OHCI Host Controller (Linux 2.6.27-9-generic ohci_hcd)
  0.0%	USB device usb4 : OHCI Host Controller (Linux 2.6.27-9-generic ohci_hcd)
  0.0%	USB device usb3 : OHCI Host Controller (Linux 2.6.27-9-generic ohci_hcd)
  0.0%	USB device usb2 : OHCI Host Controller (Linux 2.6.27-9-generic ohci_hcd)
  0.0%	USB device usb1 : OHCI Host Controller (Linux 2.6.27-9-generic ohci_hcd)

it hasn't changed much.  i ran this with screen on lowest setting and wireless turned off.

i'll look into the kernel compiling thing.  do you know of any pages that will detail what options i can select to minimize power usage and maximize performance (as far as possible) on my hardware?  thanks

---

### Post by iggykoopa on 2008-11-30
you'll have to try it in advanced mode and enable more settings, the basic mode isn't very aggressive with its settings. Also theyre aren't very many power saving options in the kernel that aren't enabled by default that I know about. I would just recommend turning on pcie aspm, set the kernel to be optimized for your processor (it's in the processor section). Other than that I just remove modules that I'm not going to use so it compiles faster.

---

### Post by sdennie on 2008-12-01
Try seeing if the following helps at all:

```

sudo cpufreq-selector -g ondemand

```

---

### Post by conjunctivitis on 2008-12-01
thanks vor.

i'll try that as soon as i get done compiling my new kernel (right now the processor has its hands full).

does 20 plus watts on battery sound pretty high to you guys?  all the power saving posts i'm reading quote from 12-15 watts...

thanks

thanks

---

### Post by sdennie on 2008-12-01
20 watts does seem high but, I only have experience with Intel hardware so, it may not be out of the ordinary.

---

