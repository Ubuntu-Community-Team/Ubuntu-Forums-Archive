---
title: "Hardy halves battery life on NC8000"
date: 2008-08-16
forum: Hardware
---

### Post by scotchfx on 2008-08-16
I just installed Hardy on my trusty NC8000 and am having issues with the power management / battery life. In a nutshell, my battery life has been more than halved from what I had in XP (I've gone from ~5hrs+ to less than 2 hrs on a full charge set... I've usually got a pair of primary/secondary batteries plugged into my laptop for longer battery life). 

I've also noticed that my laptop seems to be running much hotter and the CPU fan seems to be running constantly.

I've installed powertop and am trying to follow some of the suggestions it's been giving but all to no avail.

I need to be mobile w/ my laptop and losing 3.5+ hrs of battery life isn't an acceptable sacrifice just to be able to use Ubuntu. I don't want to have to go back to XP however so any advice would be much appreciated...

Thanks!

---

### Post by Sam Lars on 2008-08-16
I have this script in /etc/acpi/ac.d and /etc/acpi/battery.d
Basically it runs these commands each time it enters each state.  Some of those are from powertop suggestions, some are from the forums, some I added myself.
Also, you know if you have CPU throttling working correctly?
```
#!/bin/bash
 
# Go fast.  More or less Ubuntu defaults
if on_ac_power; then
  hdparm -B 255 -S 240 -M 254 /dev/sda
  mount -o remount,commit=5 /
  mount -o remount,commit=5 /home
  echo 0 > /proc/sys/vm/laptop_mode
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo 500 > /proc/sys/vm/dirty_writeback_centisecs
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save
  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
  iwpriv wlan0 power_profile 1
  echo 50 > /proc/sys/vm/swappiness
  echo 3000 > /proc/sys/vm/dirty_expire_centisecs
  hal-disable-polling --device /dev/scd0 --enable-polling
  /etc/init.d/postfix start
  /etc/init.d/anacron start
  /etc/init.d/ntp start
else # Save power
  hdparm -B 1 -S 4 -M 128 /dev/sda
  mount -o remount,commit=600 /
  mount -o remount,commit=600 /home
  echo 5 > /proc/sys/vm/laptop_mode
  echo 40 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 30000 > /proc/sys/vm/dirty_writeback_centisecs
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  iwpriv wlan0 power_profile 5
  echo 10 > /proc/sys/vm/swappiness
  echo 0 > /proc/sys/vm/dirty_expire_centisecs
  hal-disable-polling --device /dev/scd0
  /etc/init.d/postfix stop
  /etc/init.d/anacron stop
  /etc/init.d/ntp stop
  /etc/init.d/rsync stop
  /etc/init.d/smartmontools stop
fi
```

---

### Post by scotchfx on 2008-08-16
Thanks for the script, I'm something of a Linux noob (as a user I'm okay but from an admin perspective I'm pretty much all thumbs)... can I simply add this to /etc/acpi/ac.d and /etc/acpi/battery.d and see if it helps?

*Also, you know if you have CPU throttling working correctly?*

I *believe* it is; in viewing powertop I see that the processor is running the majority of the time @ 600Mhz (as a opposed to full out 2.1Ghz) however just a moment ago (before I decided to shutdown & dock my laptop) when it was on battery I was noticing in powertop that the CPU was not throttling at all (it had been prior, then something seemed to have kicked it into high gear)...

So, short answer, yes the CPU is throttling... but not consistently.

---

### Post by Sam Lars on 2008-08-16
Yes, you can put that in both places and it should work the next time you plug/unplug.
If you're using gnome you can add the CPU scaling plugin to your panel, and if you reconfigure your applets you can control scaling from it.  That seemed to be quite reliable, but I haven't been able to get anything else to work as well... setting it manually works sometimes.

---

### Post by scotchfx on 2008-08-16
I'll give the script a shot... does it matter what I name it or can it just be battery.sh or something similar..?

Thanks!

---

### Post by Sam Lars on 2008-08-16
Everything in those directories will be run whenever it enters its state.
I think it has to start with a number... I've named it 99-savings.sh, I think.  It runs them in order of number.  Thanks for mentioning that.

---

### Post by scotchfx on 2008-08-16
Out of curiousity, what will happen if I plug/unplug my laptop on the fly... do these scripts only get executed on startup?

---

### Post by Sam Lars on 2008-08-16
When you unplug the laptop, it enters battery state, and runs everything in the battery.d folder.  When you plug it back in, it enters AC state, and everything in the ac.d folder is executed.  It has nothing to do with startup and shutdown... there are folders for things to be run at that time somewhere else.
The script has an if statement that decides what part to run based on what state it's in.  You could split the if statements into two separate files in each of those directories if you wanted to.

---

### Post by scotchfx on 2008-08-17
Thanks for all the advice - I've placed the scripts in these respective directories and am currently running unplugged ATM. 

The laptop does seem to be running cooler (although I'm not sure how subjective of an assessment this is) however the battery life (in the battery monitor) is still being estimated at a little under 2 hrs (I would typically get around 5hrs with XP).

I'm going to run the battery down today and see how long I actually get. 

My laptop has integrated bluetooth (and wifi for that matter)... could this be a source of the power drain? I parsed the script you gave me but couldn't specifically discern anything modifying the bluetooth settings (again I might have just missed it).

Does the script handle bluetooth/wifi at all?

If not, can I just add the commands that powertop suggests to the script?

---

### Post by Sam Lars on 2008-08-17
I'm sure you could find some commands for bluetooth management, but since I don't have that, I don't have it in the script.
The line
```
iwpriv wlan0 power_profile 1
```
supposedly handles wifi power management on interface wlan0 (you can change that if yours is different), though I'm not sure if it works on mine or not.
The quote you get for battery life is probably not very accurate until you've drained the battery a good deal at least once.  I think I was getting a 2 hour quote out of the box, but with this script I ended up with a 4 hour one after some real use.  Vista still says 2, though I've never done much battery use with it.

---

### Post by monikersupreme on 2009-06-13
Bump to this old thread... 

Is all of this still relevant in the latest release of Hardy?

I've noticed with powertop that my two powerhogs are:

43.8% (127.4)   USB device  3-1 : Bluetooth by hp (ACTIONTEC) 
36.7% (106.9)       <interrupt> : uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3,

...respectively. However as I am using a Bluetooth mouse I'm not sure if this is necessary. I've noticed that even if I keep the mouse idle the Bluetooth usage remains high... again dunno if this is relevant. I'm puzzled by the second "uhci_hcd:usb*" but I think this may be the wifi unit in my NC8000?

Any advice/suggestions would be much appreciated!

---

