---
title: "HP dv2000 laptop - short battery life?"
date: 2009-05-11
forum: Hardware
---

### Post by mykrob on 2009-05-11
Got an HP dv2000 series laptop running Ubuntu 9.04. At full charge,the battery life expectancy shows about 1hr 30 min.

Looking for recommendations to increase this battery life. How can I turn off Bluetooth when its not in use? Any other suggestions?

Thanks,
-myk

---

### Post by Forgotten Path on 2009-05-11
I have the same series (dv2000t), and yes, battery life does suck.
No idea how to improve it.  I have read that one of Ubuntu's weaknesses is power management in laptops...

As for the Bluetooth, just flip off the switch on the front of the PC.  Unless, of course, you're using Wi-Fi.  You should be able to disable Bluetooth in System->Preferences->Bluetooth.

Hope that helps at least a little.

---

### Post by mykrob on 2009-05-11
my last laptop, a Gateway M-6881, got about 2 - 2.5 hours. I think this power hungry Turion X2 64 may be the culprit :( 

I use wifi constantly, it would be nice to be able to turn off the bluetooth,it probably consumes a good bit of power.

---

### Post by mykrob on 2009-05-12
here's what i get from powertop:

> 
Wakeups-from-idle per second : 335.9    interval: 5.0s
no ACPI power usage estimate available

Top causes for wakeups:
  42.8% (258.0)       <interrupt> : PS/2 keyboard/mouse/touchpad 
  16.7% (100.8)       <interrupt> : eth0 
  11.4% ( 68.4)          gnome-do : schedule_hrtimeout_range (hrtimer_wakeup) 
  10.1% ( 60.8)       <interrupt> : extra timer interrupt 
   5.1% ( 30.6)       <interrupt> : eth1 
   3.0% ( 18.0)      <kernel IPI> : Rescheduling interrupts 
   2.7% ( 16.0)           firefox : futex_wait (hrtimer_wakeup) 
   2.1% ( 12.6)       <interrupt> : pata_amd 
   1.5% (  9.0)     <kernel core> : hrtimer_start (tick_sched_timer)
   1.0% (  6.0)    wpa_supplicant : wl_add_timer (wl_timer)
   0.6% (  3.8)     <kernel core> : wl_add_timer (wl_timer)
   0.4% (  2.6)    gnome-terminal : schedule_hrtimeout_range (hrtimer_wakeup)
   0.4% (  2.4)              Xorg : schedule_hrtimeout_range (hrtimer_wakeup)
   0.3% (  1.8)       <interrupt> : sata_nv, mmc0
   0.3% (  1.6)       <interrupt> : nvidia
   0.2% (  1.0)    cpufreq-applet : schedule_hrtimeout_range (hrtimer_wakeup)
   0.2% (  1.0)            python : schedule_hrtimeout_range (hrtimer_wakeup)
   0.2% (  1.0)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_timer)
   0.2% (  1.0)              Xorg : nv_start_rc_timer (nv_kern_rc_timer)
   0.2% (  1.0)              Xorg : hrtimer_start (it_real_fn)
   0.1% (  0.8)       <interrupt> : acpi
   0.1% (  0.6)   hald-addon-stor : schedule_hrtimeout_range (hrtimer_wakeup)
   0.1% (  0.6)              Xorg : sk_reset_timer (tcp_delack_timer)
   0.1% (  0.4)     <kernel core> : sk_reset_timer (tcp_delack_timer)

Suggestion: Disable 'hal' from polling your cdrom with:
hal-disable-polling --device /dev/cdrom 'hal' is the component that auto-opens a
window if you plug in a CD but disables SATA power saving from kicking in.


This looks counterproductive based on that last part about SATA power saving.. Any further ideas or suggestions?

Thanks,
-myk

---

### Post by mykrob on 2009-05-12
just a thought.. Has it been proven that running Compiz/Desktop effects significantly decreases battery life?

---

### Post by tuxpenguin on 2009-05-13
In my long quest for better battery life with 8.10, I found that by running the power saving suggestions powertop gave me on startup, [ I think I put them in my init.d...not recommended]I saved about a half hour of battery. I also added a kernel option to my grub boot line...I can't remember which one it was [I'm going to try and find it again...it had something to do with the hard drive access], but it saved me at least another hour.

Also, I haven't seen any significant difference in my battery life when running Compiz.

The more stuff you can disable/streamline, the better battery life you'll have.

---

