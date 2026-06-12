---
title: "Power status reported incorrectly"
date: 2007-05-24
forum: Hardware &amp; Laptops
---

### Post by AusIV4 on 2007-05-24
I have a System76 Gazelle with an edgy install and a feisty install. In feisty, after resuming from hibernate or suspend, the power manager for both KDE and Gnome seem unable to determine what the state of the power system is.

When it resumes, the power manager arbitrarily chooses a power state - often no battery or a battery at 0%, and reports that no matter what is actually the state of the machine. I can unplug it and it keeps running, reporting that there is no battery and it is running on AC power. It doesn't notice if I remove the battery, put it back in, unplug it from AC, plug it back in.

This lack of information about the power systems means that it doesn't go in to power saving mode when the laptop is unplugged. It also means that I have no idea how much battery life my system has remaining.

There has been some discussion about this on the System76 forum, and I've filed a bug report with them, but I thought I'd see if any other systems had experienced this problem.

I've tried looking at the battery information in the /proc directory (I'm at work, so I don't have my system available to be specific), but I haven't figured out how to read the information. I might be able to debug this if anyone can tell me where this information is kept and how it is read.

Any help is appreciated.

---

### Post by whayong on 2007-05-24
Unfortunately, I have yet to see or read about a fix for this.  I am encountering the same problem in Feisty.  Maybe Ubuntu will release a laptop version for Gusty?  Don't hold your breath though.......

---

### Post by AusIV4 on 2007-05-24
Most laptops seem to handle feisty fine - at least the ones I've seen. My Gazelle works fine until I resume from hibernate or suspend. But since I use hibernate and suspend all the time, I'm sticking to my edgy partition until this gets resolved. I haven't seen anything particularly compelling about upgrading to feisty anyway.

---

### Post by corney91 on 2007-05-24
I'm having the same problem as you -my battery is apparently always on 0% and discharging. I had the same problem on Vista as well so I assumed it was because it was an old battery. Could this be the problem? It might be completely unrelated though because yours is from hibernate or suspend.

---

### Post by AusIV4 on 2007-05-25
> **corney91 said:**
> I'm having the same problem as you -my battery is apparently always on 0% and discharging. I had the same problem on Vista as well so I assumed it was because it was an old battery. Could this be the problem? It might be completely unrelated though because yours is from hibernate or suspend.

And mine works fine on edgy, regardless of hibernate and suspend.

---

### Post by AusIV4 on 2007-05-26
I'll post here what I've posted on the System76 forums and the System76 bug report:

> 
I decided to see how battery information is managed. I assume both Gnome power manager and KDE's Guidance power manager collect their data from /proc/acpi.

I ran the following commands

cat /proc/acpi/ac_adapter/AC0/state
cat /proc/acpi/battery/BAT0/alarm
cat /proc/acpi/battery/BAT0/info
cat /proc/acpi/battery/BAT0/state

Prior to suspend, they gave outputs that matched the state of the system and what the power manager reported. After resuming from suspend, those commands gave outputs that resembled what was being reported by the power manager, but not the actual state of the system.

I assume there is some kernel module that is not being reloaded properly after suspend and hibernate. Is there any way to reload modules individually to help determine which one is not being reloaded? If this can be determined, perhaps there will be one line to add to the /etc/default/acpi-support in order to get things working properly.

Additionally, I've found that removing the modules 'battery' and 'ac' makes the folders /proc/acpi/ac_adapter/AC0 and /proc/acpi/battery/BAT0 (and all subsequent files) disappear. When I reload those modules, the folders return, but the data reported by them continues to be incorrect.

---

### Post by msemtd on 2007-05-27
On Kubuntu Edgy, after spending ages trying to stop the shoddy default power thingy from starting up (had to specifically exclude guidance-power-manager from the session in kcontrol), I was using KDE's power thingy and that worked great. When I installed Feisty, the default power thingy came back and I thought I'd go with that and see if it had improved -- well, at the moment it's randomly popping up a window saying that the AC has been plugged in when I've been running on batteries for an hour and a half! :roll:
I shall have a go with the proper KDE power manager thingy again and see what it thinks.
EDIT: after killing the shoddy default power manager icon and using kcontrol to enable the power monitor that comes with KDE, I find that it correctly reports that I had better quickly plug in to recharge!

---

### Post by bvanaerde on 2007-05-31
Since I updated Feisty from 2.6.20-15 to 2.6.20-16, the Gnome Power Manager isn't working anymore.
It's always showing "Computer is running on AC power", regardless of the power cable being plugged in or not.

In 2.6.20-15, this was working perfectly (and it still does!).

edit: It is also showing a different icon (see attachment)
edit2: it seems my battery status cannot be retrieved all of a sudden... *acpi -b* gives back nothing

---

### Post by richtea on 2007-05-31
I'm a total newb so can't give you anything technical, but have just experienced this myself on my Benq s53 laptop.

Have Feisty running, power manager was working fine until the other day when update manager updated a load of stuff. Now stuck on AC : (

Tried this:

[http://lists.debian.org/debian-user/2007/03/msg02899.html](http://lists.debian.org/debian-user/2007/03/msg02899.html)

But didn't work!

edit: Seems I have the same problem as bvanaerde, running 2.6.20-15 it works fine, running 2.6.20-16 it doesn't

---

### Post by bvanaerde on 2007-06-01
> **richtea said:**
> I'm a total newb so can't give you anything technical, but have just experienced this myself on my Benq s53 laptop.

Have Feisty running, power manager was working fine until the other day when update manager updated a load of stuff. Now stuck on AC : (

Tried this:

[http://lists.debian.org/debian-user/2007/03/msg02899.html](http://lists.debian.org/debian-user/2007/03/msg02899.html)

But didn't work!

Thanks for the suggestion... but it didn't work here either.
That bug was posted somewhere in March this year, so it's probably a different one (but maybe related).

edit: here's the correct bug report:
[https://bugs.launchpad.net/ubuntu/+bug/117504](https://bugs.launchpad.net/ubuntu/+bug/117504)

---

### Post by joncheyne on 2007-06-01
Same issue as you all - and yes a different icon - which just stays on AC power regardless of the actual state of the battery.

I have a dell so the battery has a an inbuilt meter so I can tell the actual status. 

/proc/acpi all shows the correct info - if I unplug, then AC correctly reports this - but not on the desktop.

So I wonder if it is gnome-power-manager which is at fault?

[update]
If you add "Battery Charge Monitor" to the panel it shows the status fine (further along the panel, the P-M app is still showing AC:-)

  - a poor mans workaround - at least you know the status of your battery :-)

---

