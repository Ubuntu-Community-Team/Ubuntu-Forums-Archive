---
title: "My concern about fan control"
date: 2007-03-28
forum: Hardware &amp; Laptops
---

### Post by hnfmr on 2007-03-28
I was using Ubuntu Edgy 64 bit on my HP Compaq nx6325, it seems in Linux, the fan runs either at low speed or jumps to high speed (when the laptop gets hotter), so two things worry me a bit: 1. occasional noise 2. temperautre.

While in Windows XP, the fan runs at variable speeds (continuous), so the machine isn't particularly hot....and the noise level isn't always high either...

Anything I missed? Sorry for my English (not native speaker)

---

### Post by wrycatcher on 2007-03-28
I've noticed similar cooling issues since installing Edgy Eft on my Acer Aspire laptop.   It gets more hot, especially toward the front near the touchpad, under Ubuntu than it ever did running Windows XP.  I noticed the fan doesn't run as much as it did in Windows XP either, which is probably a huge contributor to the excessive heat.  I've just installed a few monitoring applets to watch the cpu-scaling, cpu temp, and battery status.

This might help you as well.  So, **here's what I did **(as well as I remember it, anyway):

Go into Synaptic Package Manager and search for "acpi".  I think I selected **acpi**, **acpid**, and **gpowerd**.  Also, consider install other applets available which allow GUI monitoring of your hardware.  Install selections, then log off and then log in (or do CTRL-ALT-BACKSPACE).  Right click on your menu bar/applet bar.  This should allow you to select an application to add.   In the applications listed, you should see something like "Hardware Monitor".  Select that one.  Additionally, you could add the cpu-scaling monitor and battery monitor, too.

You should now see new icons on your applet bar.  You can right click and select "preferences" to configure as you like.  This will give some readings as to what the exact numbers are, especially temperature...you can then determine (via some more online research) if the numbers and behavior are within normal ranges.

---

### Post by hnfmr on 2007-03-29
Thanks for the advice.......

But anyone can provide me with a solution to let the FAN run more frequently please.............it's extremely worrisome...my laptop can be very hot using Ubuntu Edgy

---

### Post by hnfmr on 2007-03-29
I installed the modules you recommended such as acpi, acpid, cpufreq & etc.....now my fan won't stop  -_-

---

### Post by azemute on 2007-03-29
What has happened is that when you installed the acpi modules [and kin] they adjusted your acpi settings. ACPI defines a variety of states about how your machine should behave when it gets hot/battery runs down/etc... in this case, you probably switched from a "pasive" thermal setting to an "active" setting... alot of this information can be found through either the ACPI command, or by viewing the actual data in /proc/acpi/

there's a variety of ways of adjusting the ACPI settings, though I'd be careful... you shouldn't be able to break your machine as thermal cut-offs should kick in before you cause any damage, but you could hurt yourself by having the device run hot in your lap [or such]

thermal information is provided in /proc/acpi/thermal_zone/THRM/

cooling_mode describes the profiles you have available to use for cooling your machine
trip_points describes the points at which the fan will turn on a low setting, turn on a high setting or passivly cool your machine.

You should be able to setup ACPI settings through the acpi modules in gnome. I believe there was a fan-monitoring plugin as well as a temperature plugin. KDE I know has both, and you can dictate power-profiles from the system tray through them.

---

### Post by hnfmr on 2007-03-29
Thank you. Very helpful. I also noticed Feisty Beta doesn't have fan control problems. :)

---

### Post by wrycatcher on 2007-03-30
> I installed the modules you recommended such as acpi, acpid, cpufreq & etc.....now my fan won't stop -_-

Is the 'powernowd' module running?  Seems that if it's running, it can mess up 'ondemand' cooling regulation.  This could cause overcooling (fan on all the time) or overheating (not enough fan).

There are lots of tips in here about what people have tried to do.  You might try some of them.  Sorry I couldn't provide you a practical, short solution.  But 100% fan is better than not enough fan, IMHO...at least you aren't risking frying your hardware for the time being.  I need to take similar interim steps to avert meltdown, as well.

[https://launchpad.net/ubuntu/+bug/22336]("https://launchpad.net/ubuntu/+bug/22336")

UPDATE 4/4/2007

I updated my bios a few days ago.  I haven't had my laptop heat up like before.  Of course, I also turned off hibernate (which never worked correctly anyway, and seemed to result in overheating) in favor of suspend.  It's been running between 25 C and 50 C since these two changes.  Unfortunately, *if* my problem is actually solved now, I'm not sure which one was the culprit...

---

