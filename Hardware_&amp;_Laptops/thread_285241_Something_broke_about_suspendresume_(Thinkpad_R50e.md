---
title: "Something broke about suspend/resume (Thinkpad R50e) on Edgy"
date: 2006-10-26
forum: Hardware &amp; Laptops
---

### Post by lutzky on 2006-10-26
I've cut the problem down as much as I can, and got stuck.

Suspend/resume worked on Dapper thanks to some of my hackery. It broke on Edgy, so I broke it down to its bare essentials.

I have a script in /usr/local/bin/thinkpad-sleep with contents as follows:

```
OLDCONSOLE=`fgconsole`
/bin/sync
/usr/bin/chvt 10
cat /proc/bus/pci/00/02.0 > /var/cache/video.config
/sbin/hwclock --systohc
echo -n mem > /sys/power/state
/sbin/hwclock --hctosys
cat /var/cache/video.conf > /proc/bus/pci/00/02.0
/usr/bin/chvt $OLDCONSOLE
```

Now, running sudo /usr/local/bin/thinkpad-sleep gets the laptop to sleep, and it wakes up PERFECTLY. No problems whatsoever. Now all that remains is to integrate it with gnome-power-manager.

Now, for dapper, the most simplistic solution that would work would be symlinking /etc/acpi/sleep.sh to /usr/local/bin/thinkpad-sleep. That used to work perfectly - Fn-F4, closing the lid, selecting 'Sleep' from the menu - everything went through thinkpad-sleep.

Now, however, this doesn't work. Again - I checked the symlink, it's still there. Running sudo thinkpad-sleep still works perfectly. But suspending through the menu or through Fn-F4 doesn't set video back at all. (Ctrl-Alt-Del does a clean reboot though).

Now, this obviously wouldn't work: /var/cache/video.config doesn't get created on Fn-F4. So the question is this - how DOES gnome-power-manager call sleep, if not through /etc/acpi/sleep.sh?

---

### Post by iamhimay on 2007-03-01
Hi,
 Did you ever get an answer? After a gnome-power-manager update fn f4 is triggering an acpi event, but it looks like sleepbtn.sh event is doing nothing. But suspending from my gnome power manager battery applet works fine, so i'd like to tie that action to the acpi event from fn f4.
Thanks.

---

