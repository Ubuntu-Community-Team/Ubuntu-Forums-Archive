---
title: "Sound on Fujitsu Siemens M3438G"
date: 2005-07-16
forum: Hardware &amp; Laptops
---

### Post by hpw on 2005-07-16
Hi,

since Tuesday this week i'm proud owner of a Fujitsu Siemens M3438G.
After some troubles with acpi i'm now able to run Hoary 5.04 (without acpi support)

The only trouble i have is getting the soundcard to work. According to lspci
it is a "Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio 
Controller (rev 04)"

After performing the alsa upgrades as described in 
[https://wiki.ubuntu.com/HdaIntelSoundHowto](https://wiki.ubuntu.com/HdaIntelSoundHowto)
i managed to have the card detected using the snd-azx driver.

Unfortunately up to this moment i did not manage to get sound out of my notebook.

Playing around with kernel parameters (acpi,apic,pci) did not fix the problem.

When i got the notebook ther was WinXP installed (the sond worked there) - so the hardware seems to be fine.

Any help greatly apreciated.

br

hans-peter

---

### Post by hpw on 2005-07-16
OK. One new thing i found out at the suse WIKI.

The kernel seems to have troubles handling ACPI-Requests.
if you add "acpi_cpufreq" to /etc/modules the troubles with
acpi (hang on boot, hang when starting powernowd) vanish.

But still no sound....

---

### Post by varunus on 2005-07-16
You said you had set up the drivers for ALSA...are they getting loaded every boot?  Check for the "snd-" modules in the output of lsmod.

Also, try entering "alsamixer" and make sure you're not muted.  Some cards I've seen seem to start out muted...

---

### Post by hpw on 2005-07-18
Got it.

I managed to get the thing running taking the follwing steps

Add a line
acpi_cpufreq
to /etc/modules

uninstall the alsa-1.0.8-driver modules (i previously installed)

install the alsa 1.0.9_rc4a driver (i got it from the realtek homepage - drivers for ALC880)
after a reboot, sound was working and all the acpi error messages vanished.

br

Hans-Peter

---

### Post by hpw on 2006-02-17
Upgrading to Dapper Drake fixed that problem for good ...\\:D/

---

### Post by tso on 2006-11-03
I had the problem of not having sound on my Amilo M3438G, too. I solved it by starting the alsamixer. The sound for the internal speaker was disabled, so all I had to do was to enable it.

---

