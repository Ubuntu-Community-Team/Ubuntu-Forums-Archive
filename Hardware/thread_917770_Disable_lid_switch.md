---
title: "Disable lid switch?"
date: 2008-09-12
forum: Hardware
---

### Post by chhamilton on 2008-09-12
I've got at Thinkpad T42 with Hardy running on it.  Everything works fine, except the laptop lid switch has gone a little flaky.  Essentially, it doesn't always work, and sometimes it decides to fire off an event at random moments.  (The same behaviour is seen in windows or anywhere else, so I'm pretty sure it's a physical issue with the switch).

Anyhow, I want to disable the lid switch.  Normal behaviour is for it to put the laptop to sleep, which I've disabled in the power management settings.  However, if the laptop *is* suspended and switch decides to interpret an event, then the laptop is woken up.  This has happened on numerous occasions while in my bag, leaving me to find an extremely hot laptop with very little battery power left.

Is there any way to block events from a the lid switch?  I'd like to do it as low down as possible, preferably right at the device level so that no events even get fed to ACPI.

Ideas?

Thanks!

Chris

---

### Post by chhamilton on 2008-09-12
Alright... so I asked the question before having Googled enough.  It turns out that ACPI maintains a list of devices that are able to wake up a suspended laptop, and the lid switch is normally one of them.  Fortunately, they are configurable.  I did this following:

```
sudo apt-get install acpitool
```

Then, I got a list of wakeup devices by running

```
sudo acpitool -w
```

which returns:

```

  Device    S-state   Status   Sysfs node
 ------------------------------------
 1. LID       S3    *enabled
 2. SLPB      S3    *enabled
 ... etc ...

```

(This is effectively the same output as running "cat /proc/acpi/wakeup".)  Then, to make it so that the lid switch is no longer capable of waking up the laptop I ran

```
sudo acpitool -W 1
```

where 1 is the device number corresponding to the lid switch.  Problem solved!

---

### Post by quadra on 2011-08-31
Hi

This solution is certainly fine in special cases like yours.

For more general case:
The lid switch behaviour can be set in System - Preferences - Power Management. 
When I tried to do this in Ubuntu 11.04, I found that the "Do nothing" option had disappeared. However, it can be easily restored using the Gnome Configuration editor (gconf-editor): in gconf-editor, go to apps - Gnome Power Manager - buttons. Then, change the values for "lid_ac" and "lid_battery" to "nothing".

---

