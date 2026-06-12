---
title: "Battery Life and Power Indicator"
date: 2010-05-22
forum: Hardware
---

### Post by Trilby on 2010-05-22
I have an Acer Laptop running Lucid and Windows 7. I've noticed that battery life when using Ubuntu is much shorter than Windows (about 1:15 hrs compared with 2:30 hrs). A friend tells me this is because Linux' battery drivers and less advanced, if there a way around this?

A related problem is that the power use indicator doesn't function correctly. Unless I briefly put my laptop on stand-by mode after booting, the laptop will be convinced it is running of mains power. It will not monitor the remaining battery life when discharging or the charge status when charging the battery, the former having caused surprise losses of power.

Can anyone help?

Thanks,
Trilby

---

### Post by giova.86 on 2010-05-23
Hy Trilby.
If the battery life is too short try to look here: [http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)

---

### Post by exchaoordo on 2010-05-26
It's not the battery but the indicator applet I'm pretty sure.  I wish I knew more because this is a problem lots of Aspire One people are reporting, me included.  Wild fluctuations in the battery indication putting the machine to sleep etc.

---

### Post by lidex on 2010-05-27
This may help.
> Since  Lucid 10.04 laptop-mode-tools is deprecated and conflicts with standard packages.

To manually activate laptop-mode type:

sudo laptop_mode start

however this will only last until next reboot.

Laptop mode is disabled by default in Ubuntu. To enable it open terminal shell and type:

sudo gedit /etc/default/acpi-support

At the bottom of the file, there is ENABLE_LAPTOP_MODE variable, set this to true. A restart is required to enable this setting.

Read through this file to see some of the other options.

Ensure you have laptop-mode-tools installed:

sudo apt-get install laptop-mode-tools laptop-detect

Linux can use different power management profiles called “governors.” By default, Ubuntu does not allow you to change which governor it uses, however you can enable the option with one command:

sudo dpkg-reconfigure gnome-applets

After that, make sure you have the “CPU Frequency Monitor” applet running in your Gnome panel. Right click on the applet and go to the Preferences. Under “Frequency Selector” section, make sure the “Show menu” is selected on “Frequencies and Governors.”

Then you can left click on the applet and from here, choose which governors or frequencies to use.

You can change this via the command line without having to enable anything. Just go to /sys/devices/system/cpu/cpu0/cpufreq/ (if you have multiple processors/cores/hyperthreading change cpu0 to cpu1, cpu2, etc. for each cpu you have listed) and edit the file (use sudo) “scaling_governor”, just change the governor that is listed to whatever governor you want to use. Available governors are listed in “scaling_avail_governors”

man laptop-mode.conf

and edit /etc/laptop-mode/laptop-mode.conf

Consider installing also powertop which could easily help you reducing energy consumption by analyzing actual energy wasts and give you useful tips on how to save.

sudo apt-get install powertop



---

### Post by Trilby on 2010-05-31
> **lidex said:**
> This may help...
Could you clarify that? Are those instructions in the right order?

Thanks

---

