---
title: "close and open the monitor of the laptop not showing xscreensaver lock screen anymore"
date: 2005-01-17
forum: Hardware &amp; Laptops
---

### Post by merinda on 2005-01-17
I remember the first time I installed ubuntu, it is nice. When I close the monitor of the laptop, then I open it, it show xscreensaver lock screen...... it ask username and password.... 

But after following this guide:
```

If you have a new laptop, or want to take full advantage of power management, or want software suspend , you should use ACPI if your system supports it. ACPI power management should be enabled by default on systems that support it, but suspend needs some extra work. First, download the ACPI scripts at  https://www.ubuntulinux.org/wiki/acpi.tar.gz/download . Then, at a shell, do the following:

   cd /etc
   sudo rm acpi -rf

Then, extract the ACPI scripts located here by doing a

   sudo tar zxvf ~/acpi.tar.gz

(assuming that you downloaded the scripts to your home directory).
Suspend-to-RAM (ACPI)

You have to do a few things to do in order to get suspend-to-RAM working. After following the above steps, do a cd /etc/acpi/buttons and remove the symlinks for lid.sh and sleep.sh, pointed to null. Re-create these pointing to ../actions/suspend.sh

   sudo ln -s ../actions/suspend.sh lid.sh
   sudo ln -s ../actions/suspend.sh sleep.sh

This changes what the lid and sleep actions do (as they are pointed to the symlinks for lid.sh and sleep.sh) to suspend-to-RAM. You may need to edit the suspend.sh file if you have drivers other than USB that need to be unloaded before and reloaded after suspend. Other than that, you are set and lid close/sleep button should initiate a suspend-to-RAM.

```
when I close the laptop's monitor, it shut down my machine..... then I set lid.sh and sleep.sh to point to null.
Then when I close the laptop's monitor, and open again..... the xscreensaver lock screen not showing anymore, instead showing my desktop.
I have reinstall the acpi related package by synaptic but does not work anymore.


anyone know how do I revert back????

---

### Post by tux61 on 2005-01-18
Same problem here  :sad:

---

### Post by jerome bettis on 2005-01-20
my acpi setup works absolutely perfectly, so i'll post up what i have.  i'm not sure if it will work for you, but it might be worth a try to just copy my setup and see what happens.

put this in etc/acpi and extract it:

---

