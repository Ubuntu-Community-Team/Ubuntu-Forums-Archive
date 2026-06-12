---
title: "Ubuntu 8.04 goes into sleep mode after 4 minutes regardless..."
date: 2009-07-14
forum: Hardware
---

### Post by AmbientOcclusion on 2009-07-14
I have an HP Mini 1116MR with 8.04 HP Mi version. No matter what I set the power management settings to, the laptop will go into sleep mode after 4 minutes of inactivity. Even if I set the sliders to never, or 2 hours or something similar it will still shut down exactly at 4 minutes.

Any ideas why this is occurring or how to fix it?

If I open power management the sliders only allow for me to select 2 hours 1 minute or Never for both battery and non battery power. If I were to set the selection to never and rebooted, or even reopened power management the sliders would indicate 2 hours 1 minute. Even at this setting it will enter sleep mode at 4 minutes.

---

### Post by nietzschez on 2009-07-14
Um, consider using 9.04.

---

### Post by AmbientOcclusion on 2009-07-14
This is the HP version of 8.04, for the netbook. I didn't know there is a 9.04. I tried the netbook remix and some of the device workarounds didn't work.

I still feel like I should be able to control the power manager and would like to know how to fix this issue. It seems as if I am unable to control it.

---

### Post by AmbientOcclusion on 2009-07-14
Regardless of what version I should have, is there some reason why power management will not work? I would like to fix it, or at least gain control over the settings.

---

### Post by AmbientOcclusion on 2009-07-16
Should I just remove the Gnome Power Management and reinstall? Or what steps can I take to trouble shoot the problem?

---

### Post by AmbientOcclusion on 2009-07-17
[SIZE="5"]SOLVED[/SIZE]

Thanks to the Fedora Users for their help supporting the Ubuntu 8.04 LTS policy, lol.


Settings> Click Advanced Tab> Configuration Editor

Twirl Down APPS

Twirl Down GNOME POWER MANAGER

Then click on each of the folders and adjust settings.

The GnomeConfigurationEditor is similar to the Registry Editor in Windows, so click on each of the settings under each folder (ie Actions) and type in a new value.

For example I clicked on the actions folder, then clicked on sleep_type_ac.

Next I typed in a value of **nothing**.

I went through each setting and turned off hibernation etc. This should solve the issues if others are having them. The settings survive reboot, so problem solved.

As a test I had no sleep/hibernation issues with ntbook remix, so maybe this is just something with the HP Ubuntu Iteration.

---

