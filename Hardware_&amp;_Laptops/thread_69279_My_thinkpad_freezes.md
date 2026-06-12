---
title: "My thinkpad freezes"
date: 2005-09-26
forum: Hardware &amp; Laptops
---

### Post by Midget on 2005-09-26
I have an IBM Thinkpad x31 with a fresh installation of Ubuntu Hoary. Everything went smoothly during the install, but later on I've found a rather big problem: My laptop freezes when I pull out the powercord. 

If I want to run on batteries, I pull the power out, the laptop freezes, I reboot and everything works fine.

Has anyone else had this problem / knows how to fix it?

---

### Post by JELaVallee on 2005-09-28
I've had this problem with my thinkpad T43p early on in Hoary.  It's related to ACPI not playing nice when reconfiguring the system settings in power-save mode.

This solution worked for me: [http://ubuntuforums.org/showthread.php?p=293282&highlight=acpi#post293282](http://ubuntuforums.org/showthread.php?p=293282&highlight=acpi#post293282)

But I've recently upgraded the kernel to the latest 2.6.10 686 kernel and this problem has gone away with ACPI turned on.

cheers,
Etienne

---

### Post by Midget on 2005-10-07
[QUOTE=JELaVallee]But I've recently upgraded the kernel to the latest 2.6.10 686 kernel and this problem has gone away with ACPI turned on.[/QUOTE]

I don't want to turn off acpi, because I want the power-saving-features (cpufreq, battery and so on). I upgraded to breezy last night (kernel 2.6.12), but it still freezes. Hopefully someone will find a fix to this problem soon :)

---

### Post by akseli on 2005-10-08
[QUOTE=Midget]I don't want to turn off acpi, because I want the power-saving-features (cpufreq, battery and so on). I upgraded to breezy last night (kernel 2.6.12), but it still freezes. Hopefully someone will find a fix to this problem soon :)[/QUOTE]

I'm running a somewhat older T23 version thinkpad. I had to disable APM because with ACPI I was unable to successfully suspend and resume. 
After adding the APM module to boot and adding ACPI=off APM=on to grub's menu.lst file I have been running everything perfectly. that is: when I am not using all of my processing power my Pentium III-m processor slows down, when I'm not plugged into the power-cord the screen becomes somewhat dimmer, and when I close the cover my laptop suspends perfectly just as it would with windows. Only problem that I have run across is that I am forced to run /etc/init.d/alsa-utils restart in order to get sound after resuming from suspend.

To conclude, I think that you're perfectly well of running APM instead of ACPI. I still haven't figured out what the advantage to ACPI is...
Good luck!

---

