---
title: "Ubuntu 16.04 with kernel 4.10.x hangs when switching to battery on Dell XPS 9560"
date: 2017-03-28
forum: Hardware
---

### Post by dhaneshr on 2017-03-28
Hi,

I recently install Ubuntu 16.04 and upgraded to the 4.10.x mainline kernel on my Dell XPS 9560 (Kaby Lake with NVIDIA 1050) . I also have configured NVIDIA with proprietary drivers ([FONT=Courier New]nvidia-375[/FONT]) but without [FONT=Courier New]bumblebee[/FONT]. I normally only use the built-in Intel graphics and occasionally switch to NVIDIA using [FONT=Courier New]prime-select nvidia[/FONT]. I've installed[FONT=Courier New] tlp[/FONT] for better power management. I have also installed the latest Kaby-lake drivers from Intel. 

I'm happy with the install however, if I unplug the AC power and switch to battery - the system hangs - and nothing works (no keyboard, touchpad) and I have to revert to hard-reset . I've tested with kernel 4.8.x-HWE as well as kernel 4.9.x and all results in the same behaviour. 


What could results in such freezes ? Anyone else with the same problem ? 


D

---

### Post by Doug S on 2017-03-29
Does the problem still occur if you try[ the mainline 4.11-rc4 kernel]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11-rc4/")?
Does the problem persist if you plug in the power cord again.
Does the problem occur using the acpi-cpufreq CPU frequency scaling driver instead of the intel_pstate driver?

To disable the intel_pstate driver and use the acpi-cpufreq driver instead, do this in your /etc/default/grub file:
```
GRUB_CMDLINE_LINUX_DEFAULT="intel_pstate=disable"
```If you do not use grub, then I don't know.

EDIT: Also is there any insight gained by looking at the log files? /var/log/kern.log and /var/log/syslog are two to look at in particular.

---

### Post by ackowa2 on 2017-04-01
Have a 9560 as well and running 16.04 + 4.8 kernel from hwe package (+ some company customization (i.e. ldap login ))
Installed intel propriatary micro code driver from additional drivers menu.
Have not installed nvidia driver, tried with 375 and prime-select intel and got black screen only at boot.
have not installed tlp.
Running with WD15 docking station as power supply (usb-c) (problems with dock before upgrading to latest laptop bios)

No problem disconnecting from dock and running on battery.

---

