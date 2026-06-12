---
title: "ups detected but no shutdown"
date: 2008-06-08
forum: Hardware
---

### Post by Tim Watson on 2008-06-08
My UPS is recognised, gnome power manager notifications are produced when AC power switched off, low power reached etc. and the correct battery levels are shown but the shutdown set for low level and critical level never happens.

Both use_profile_time and use_time_for_policy were initially set to true but no power history was shown despite two charge/discharge cycles. I set them both to false and altered the thresholds to percentage_low=80, percentage_critical=20 and percentage_action=15 and rebooted, then turned the AC power off and again, all the notifications looked fine but no shutdown at 80%...65%...58%, at which time I turned the power back on.

Ubuntu 8.04, GPM 2.22.1, APC Back-UPS ES 700

I've raised a bug report with gnome:
[http://bugzilla.gnome.org/show_bug.cgi?id=537107](http://bugzilla.gnome.org/show_bug.cgi?id=537107)

Is anyone else having the same problem with their UPS, or is anyone else finding that their UPS is triggering a shutdown properly? Any help would be greatly appreciated.

---

### Post by Tim Watson on 2008-06-09
Is anyone's UPS working with gnome power manager (i.e. is it recognised and does the shutdown at a given battery level or at a specified time actually happen)?

---

### Post by Tim Watson on 2008-06-10
No response yet to the bug report I submitted for g-p-m so I installed apcupsd and followed the configuration instructions. It works perfectly!

---

### Post by cadcrazy on 2008-07-25
How you manage to get apcupsd working. I have installed it from Ubuntu Repo on My 8.04.1 and configured apcupsd.conf properly. When i issue 
 **/etc/init.d/apcupsd start**
i get success
> **Starting UPS power management: apcupsd.**

but when i check the status i get error message
**apcaccess status**

> FATAL ERROR in apcaccess.c at line 41
tcp_open: cannot connect to server localhost on port 3551.
ERR=Connection refused


Anybody help me how to resolve this error.

---

### Post by cadcrazy on 2008-07-25
> **Tim Watson said:**
> I set them both to false and altered the thresholds to percentage_low=80, percentage_critical=20 and percentage_action=15 and rebooted, then turned the AC power off and again, all the notifications looked fine but no shutdown at 80%...65%...58%, at which time I turned the power back on.



Could you plz elaborate how to low value and critical percentage. I mean which .conf file to edit.

And then let me check

---

