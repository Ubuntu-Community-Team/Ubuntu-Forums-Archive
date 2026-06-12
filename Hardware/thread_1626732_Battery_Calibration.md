---
title: "Battery Calibration"
date: 2010-11-20
forum: Hardware
---

### Post by notoriousdbp on 2010-11-20
Before Ubuntu 10.04, I was able to set my power management preferences to 'Do Nothing' if the battery reached a 'critical' level.  This meant that, in order to calibrate the the battery I could completely empty the battery before recharging.  The option to 'do nothing' in no longer available in gnome-power-management for a critical battery level.

This is starting to cause a problem as I haven't been able to properly calibrate my battery in ages and it's really starting to suffer as a result.

I've tried adjusting settings in gconf-editor to set the 'critical' level to 0% but this doesn't seem to work.  Can anyone point me in the right direction of how to either re-enable the setting or are there any calibration utilities available for Ubuntu.  I don't have the option to calibrate in my BIOS by the way.  My laptop is an Acer Aspire 5535

---

### Post by Angelo Maldito on 2010-11-21
> **notoriousdbp said:**
> Before Ubuntu 10.04, I was able to set my power management preferences to 'Do Nothing' if the battery reached a 'critical' level.  This meant that, in order to calibrate the the battery I could completely empty the battery before recharging.  The option to 'do nothing' in no longer available in gnome-power-management for a critical battery level.

This is starting to cause a problem as I haven't been able to properly calibrate my battery in ages and it's really starting to suffer as a result.

I've tried adjusting settings in gconf-editor to set the 'critical' level to 0% but this doesn't seem to work.  Can anyone point me in the right direction of how to either re-enable the setting or are there any calibration utilities available for Ubuntu.  I don't have the option to calibrate in my BIOS by the way.  My laptop is an Acer Aspire 5535
Hi, I have the same problem. One possible solution, I'm not sure, is to open the 'system monitor' and to end the process 'power-management', then probably your laptop will be able to consume the very last drop of energy from the battery. However, it might be possible, as the power manager will not be working, that it will not be able to register the actual energy cycle of the battery. Nevertheless, it might work as the chip inside the battery will be working normally and registering the respective data. Any other ideas?

---

### Post by notoriousdbp on 2010-11-21
Thanks for that, I'll give it a try and report back.  I assume there must be a reason for removing the 'do nothing' option in gnome-power-manager but if anyone knows how to re-instate the option I'd like to know

---

### Post by notoriousdbp on 2010-11-21
Reported on Launchpad - [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/678265](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/678265)

---

### Post by fosca on 2011-08-13
On Ubuntu 10.10, you can recover the 'do nothing' option when the battery critical level is reached by running the gconf-editor under sudo:

sudo gconf-editor
apps --> gnome-power-manager --> actions

then you will have the choice for the critical-battery action between:

suspend, hibernate, shutdown and nothing

By default, it seems that a given user login cannot set 'nothing' with the simple 'Preferences' battery menu.

Hope that helps...

---

### Post by Steve Kroon on 2012-08-29
I've also read that just draining your battery on the BIOS screen or operating system selection screen can be used to calibrate your battery.

---

### Post by overdrank on 2012-08-29
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

