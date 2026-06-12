---
title: "Feisty-&gt;Gutsy breaks old laptop"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by Jekyll on 2007-11-04
I recently upgraded an old Asus M2400 to Gutsy from Feisty about a week ago, since then it has been running incredibly slowly.

It's very unresponsive, taking upwards of a minute to load programs that started in seconds, and the compilation of tex files is much slower.

It now keeps the fan running on full all the time, even when the processor isn't hot, and our USB WiFi and pen drives are no longer working with it.

Does any one have any smart ideas about what might be going wrong or should I reinstall Feisty?

Thanks,

---

### Post by ajgreeny on 2007-11-04
If desktop effects are enables try stopping them and see if it makes everything run faster.  If so then that will be the problem.  Compiz-fusion (ie, desktop effects) may run but just slow things up if your old laptop is not really good enough for them.

Go to System> Preferences> Appearance, and the Visual Effects tab will let you turn them off to try this out.  If that makes no difference, then it may be that a clean install is needed, as you suggested, but wait and see what other people have to say first.

---

### Post by Jekyll on 2007-11-04
> **ajgreeny said:**
> If desktop effects are enables try stopping them and see if it makes everything run faster.  If so then that will be the problem.  Compiz-fusion (ie, desktop effects) may run but just slow things up if your old laptop is not really good enough for them.

Go to System> Preferences> Appearance, and the Visual Effects tab will let you turn them off to try this out.  If that makes no difference, then it may be that a clean install is needed, as you suggested, but wait and see what other people have to say first.

Thanks, but I've already tried that.

---

### Post by Jekyll on 2007-11-05
Bump.
There is a message that flashes by on startup.

Something like:
"Can't  start hardware abstraction layer please ensure dbus is running."

dbus is running by the time I get into gnome.

Any ideas?

---

### Post by Jekyll on 2007-11-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Fixed.
The dbus priority in /etc/rc2.d/ was set to S50 making it start after HAL.

Setting it back down to S12  i.e.
sudo mv /etc/rc2.d/S50dbus /etc/rc2.d/S12dbus

fixed all the issues with HAL and everything is now fine.
See:
 
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931)

for similar problems/resolution.

---

