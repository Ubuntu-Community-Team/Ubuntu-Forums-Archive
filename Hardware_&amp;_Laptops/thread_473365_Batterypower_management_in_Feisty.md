---
title: "Battery/power management in Feisty?"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by Mimsy on 2007-06-14
I recently discovered the irritation and anger that is power management in Ubuntu. My brand new laptop battery gets three hours of life in Windows, and one hour in Ubuntu.The laptop goes everywhere with me, so this is unacceptable.... I need effective power management. I am currently using Dapper, and before moving to Feisty I thought I'd ask around and see if I can get some input on how power management works there. Is it much improved over Dapper? Is it improved at all? What are some of the irritations and difficulties in this area?

I want to keep Ubuntu, I have sniffed lightly at other distros and this is my favorite, but this is a problem.

---

### Post by neptho on 2007-06-14
I had to rebuild my ACPI to actually trigger events to happen with Feisty.  It's not difficult, but it [is annoying to track down](http://ubuntuforums.org/showthread.php?t=468396).

---

### Post by trippinnik on 2007-06-14
Well the updated kernel should be quite a bit better, but the two hours difference you're seeing is pretty huge.  Are you sure you have CPU scaling on?  Also there is a lot of work being done on this recently.  There is a new kernel (not available in the repos but you can build it) with Tickless support which should let the CPU stay in lower powerstates longer without waking up.  There's also a utility Powertop you can use to find out what apps are bringing the CPU out of lower powerstates.   I get 1.5 hours but my battery only charges to about 50%.  You probably also want to stop beagled or tracker from loading to save power.  Do you have power management turned on for you GPU?

---

### Post by NeoLithium on 2007-06-14
Check out [http://www.ubuntuguide.org](http://www.ubuntuguide.org)  Using the Powersave option if you follow the CPU scaling section makes a great difference with battery life.

---

### Post by Kobalt on 2007-06-14
You can also save battery life enabling laptop mode : ```
sudo gedit /etc/default/acpi-support
```
Modify the last line to change the laptop mode to "true" : > ENABLE_LAPTOP_MODE=true
Save, quit and reboot to apply changes.

---

