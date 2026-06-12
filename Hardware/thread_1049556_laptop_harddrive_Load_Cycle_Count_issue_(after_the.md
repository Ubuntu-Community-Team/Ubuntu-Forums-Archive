---
title: "laptop harddrive Load_Cycle_Count issue (after the acpi-support update)"
date: 2009-01-24
forum: Hardware
---

### Post by plamen_todoroff on 2009-01-24
I applied the Suse fix ([http://en.opensuse.org/Disk_Power_Management]("http://en.opensuse.org/Disk_Power_Management")) from the original thread by ubuntu_demon, as it seemed like a more elegant approach to the problem, right after I installed my system (Hardy) back in September 2008.

Now there is an update to the acpi-support package that fixes the laptop harddrive Load_Cycle_Count issue.

I want to ask, what do I do now? Do I just install the acpi-support update? Or first remove the files I created with the Suse fix and then install the update?

---

### Post by plamen_todoroff on 2009-01-27
Anybody? I thought this was a serious issue and a lot of people solved the problem by applying ubuntu_demon's fixes. What do you guys did now? Do you just installed the acpi-support update?

---

### Post by plamen_todoroff on 2009-01-28
Bump

---

### Post by jimv on 2009-01-28
All the Ubuntu update does is change the power saving mode on the HD when you unplug your laptop.  Installing it can only help.

---

### Post by plamen_todoroff on 2009-01-28
I'm completely aware of that, but the fixes that ubuntu_demon proposed back in this thread [http://ubuntuforums.org/showthread.php?t=805570]("http://ubuntuforums.org/showthread.php?t=805570") do the same job.

My question is shall I remove the previously applied Suse fix and then install the acpi-support update? The suse fix mention in ubuntu_demon's thread concerns the pm-utils package, not the acpi-support package, so they both do the same job but through different methods. The pm-utils fix (the Suse fix) also changes the power saving mode whne you plug or unplug the ac cord, so does the acpi-support updated package. I guess the official update is the better choice, but if I leave the pm-utils fix as by ubuntu_demon's instructions, which one will do the job and will both fixes conflict with each other?

---

