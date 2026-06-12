---
title: "customizing acpi events"
date: 2005-07-27
forum: Hardware &amp; Laptops
---

### Post by phen on 2005-07-27
hello all!

i am thinking about a new way to use the time i dont have :)

I am using a HP nc6120 laptop, that works absolutely perfect. But the acpi is configured in a way, that closing the lid brings up the screensaver and (maybe, because i cant see anything) suspends the system to ram. 

but i would like to keep the system awake, without the screensaver. So i would be able to connect a external display and use the laptop closed. I have no idea how to start this. i found some acpi-support scripts and played with them, but i would like to read some documentation or howtos before tinkering more. anyone who can point me to some documentation or howtos: Thank you in advance!!


cheers,

kai

---

### Post by luca_linux on 2005-07-27
Yes, I know it's possible to customize acpi events by editing some conf files after having monitored acpid, but maybe you can just use the Ubuntu Hp version available here: [https://www.ubuntulinux.org/support/custom/hplaptops](https://www.ubuntulinux.org/support/custom/hplaptops)

---

### Post by phen on 2005-07-27
thanks for your answer! but actually i use the hp version at the moment. And everything is working! but not the way i like it in this special case....

i searched for a good acpi howto but weren't able to find one. help here would be appreciated a lot!

thanks

kai

---

### Post by Angel Herranz on 2005-07-27
[QUOTE=phen]
i searched for a good acpi howto but weren't able to find one. help here would be appreciated a lot!
[/QUOTE]

Explore all the stuff in /etc/acpi.  You will find there scripts and configuration files that relates acpi and button events to those scripts.

This is not a howto but I think it will help you to spend your time ;).

--
Angel

---

### Post by elsewhere on 2005-07-27
If you're familiar with scripting, you can experiment, you don't really need a howto.

Basically, an event calls an acpi configuration file in /etc/acpi/events that generally calls an "action" script in /etc/acpi.

In the case of a laptop lid closing, a standard acpi event would trigger /etc/acpi/events/lidbtn, which is configured to activate /etc/acpi/lid.sh to trigger the suspend sequence.  There are similar events for pressing the sleep button, power button etc.

If you want to disable the lid activating suspend, you could just comment out the "action=/etc/acpi/lid.sh" line in /etc/acpi/events/lidbtn.  However, you may want to experiment to create a script that will blank the screen when the lid is closed, otherwise the screen and backlight will still remain active with the lid closed.

Also, any time you alter the acpi scripts, you should restart the acpi daemon (acpid) with a simple *sudo /etc/rc.d/acpid restart* in order to reload the event configurations.

Anyways, hope this helps you get started, experimentation will allow you to tweak it the way you want, without really causing any permanent or irrepairable damage.  Just remember to backup the original files in case you need to restore them.

Cheers,
KV

---

