---
title: "elitebook 8560p resumes from suspend only to suspend again"
date: 2011-09-04
forum: Hardware
---

### Post by ahto111 on 2011-09-04
Hi,

I have been playing with my new laptop and ubuntu 11.04 is almost perfect for it. There's one problem that I would like to fix.

When running on battery power I close the lid and laptop goes into suspend mode like it is supposed to.
Then after a while I open the lid and press power button to restore the machine. 
I enter my password when asked and I can see for a second that battery level indicator is showing alarm that battery level is critical and then it goes back to suspend mode right away. 
When I repeat the process the second time it doesn't do that anymore.

This happens also if I hibernate and return from there.

There's plenty of power left in the battery.

I tried to find some parameters to tune in dconf but I can't find anything relating to power management.
They are not in the old place ( /apps/gnome-power-manager/) or the new place (org.gnome.settings-daemon.plugins.power)

If there was a way I could tell the power manager to take it easy and not throw the machine back to suspend mode, my Ubuntu laptop project would be a success :)

---

### Post by Toz on 2011-09-05
I've read a couple of posts over the last while regarding bugs with gnome-power-manager with respect to properly estimating remaining battery time - especially after suspend/hibernate. The suggested fix might help you:

```
gconftool-2 --type bool --set /apps/gnome-power-manager/general/use_time_for_policy false
```

Just googled around and found this reference:

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/120258]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/120258") (post #61)

Worth a try?

---

