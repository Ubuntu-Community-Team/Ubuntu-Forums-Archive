---
title: "Gnome power manager does not auto suspend or give notifications for critical battery"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by rraheja on 2008-02-06
I am running Ubuntu Gutsy 7.10 which has gnome-power-manager 2.2 on a Sony Vaio VGN-N130G laptop. 

When running on battery, the power manager icon in the panel gives absolutely no notification when it goes low or critical, and it does not auto suspend/hibernate, even though it is mentioned in the settings.  the laptop just continues to drain and shuts down un-gracefully with a loud click....not good.

I searched through the forums and some folks had success with putting acpi_cpufreq in /etc/modules. I did that, but did not help at all. the only balloon style notification I get is if I disconnect the power and I get the "Discharging" notification.

Interestingly, I tried to change the notification and threshold settings in the Configuration Editor and even changed the use_time_for_policy to false, and they had absolutely no effect e.g. even if I change to have no Discharging notification, I still get only that notification, leading me to think that gnome-power-manager is not even using its own configuration settings?

I installed KDE to see if this is a gnome specific issue, and the KDE power manager does honor the thresholds and gives out warning notifications correctly. IT also attempts to hibernate the machine on the given threshold, except that the hibernate itself crashes, but thats another issue. It does seem like this is a gnome specific issue, so for now I will have to use KDE just as I was appreciating the simplicity of gnome.

-raj

---

### Post by dtgolder on 2008-03-21
Anyone have any ideas? Having the same issues....

---

### Post by hihihi on 2008-06-21
Instead of changing to another window/desktop/manager you should look simply for linux solutions regarding laptop issues and for this one we have laptop-mode tools.
laptop-mode tools come by default with your ubuntu installation, but are not started by default! They are very very handy for laptop users, though.

I am having the same problem with my new laptop (sony vaio fz31m).
gpm gives out battery-critical-low warning, so it is working correctly.
hibernation is working correctly, too, but nevertheless it wont hibernate on critical level.
so we need to change the laptop-mode settings.

1.) first of all make sure laptop-mode is enabled on battery (not default)

$ sudo gedit /etc/default/acpi-support

set line &#8220;ENABLE_LAPTOP_MODE&#8221; to &#8220;true&#8221;


from now on this will work automatically after restarting system, once you're on battery, laptop mode is activated.

to activate without restart on the fly:

$ sudo laptop_mode start

2.) now you need to edit laptop-mode-tools:

$ sudo gedit /etc/laptop-mode/laptop-mode.conf

set the
"Disable all data loss sensitive features"-option when the battery level to 1%:

MINIMUM_BATTERY_CHARGE_PERCENT=1

to enable auto-hibernation (hibernate on battery critical-low):

ENABLE_AUTO_HIBERNATION=1

HIBERNATE_COMMAND=/etc/acpi/hibernate.sh (this is my working hibernation script, point it to the script that works for you)

AUTO_HIBERNATION_BATTERY_CHARGE_PERCENT=3 (this value has to be higher than the "MINIMUM_BATTERY_CHARGE_PERCENT"-value and has to give your battery enough time to hibernate)
I hope this helps anybody searching for the answer.
cheers
_________

---

