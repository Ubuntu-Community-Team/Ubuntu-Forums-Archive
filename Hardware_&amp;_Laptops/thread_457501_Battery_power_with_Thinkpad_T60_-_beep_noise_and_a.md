---
title: "Battery power with Thinkpad T60 - beep noise and applet not there"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by akvik on 2007-05-28
Hi,

when using my Thinkpad T60 on battery (with latest Feisty), I get a tiny beep noise that is very disturbing. This beep is not there when using the laptop on power. When the CPU is working intensely it disappears, only to return when it's not intensive. I suspected it has to do with the graphics card, but the beep is there with both ati restricted drivers and Vesa.

This beep does not occur with XP or Vista on the same computer.

Another thing that might be related to this beep, is that if I go to System > Preferences > Power management, there is no tab for "On Battery" that I am pretty sure used to be there before. If I check the "Always display the icon", the "power chord" applet appears and says "Computer is running on AC power" which it isn't:
```

:~$ acpi
 Battery 1: discharging, 93%, 02:20:11 remaining
```

Does anyone know what might be causing this?

:)

---

### Post by bone43 on 2007-05-28
> **akvik said:**
> Hi,

when using my Thinkpad T60 on battery (with latest Feisty), I get a tiny beep noise that is very disturbing. This beep is not there when using the laptop on power. When the CPU is working intensely it disappears, only to return when it's not intensive. I suspected it has to do with the graphics card, but the beep is there with both ati restricted drivers and Vesa.

This beep does not occur with XP or Vista on the same computer.

Another thing that might be related to this beep, is that if I go to System > Preferences > Power management, there is no tab for "On Battery" that I am pretty sure used to be there before. If I check the "Always display the icon", the "power chord" applet appears and says "Computer is running on AC power" which it isn't:
```

:~$ acpi
 Battery 1: discharging, 93%, 02:20:11 remaining
```

Does anyone know what might be causing this?

:)

 I am also running  a T60 and do have " on battery" in my power managment section did you upgrade today with upgrade manager?

---

### Post by akvik on 2007-05-28
Thanks for the reply :)

Yes, but this has been going on for some time, I don't think there is a particular upgrade that has caused it. I have tried to look around the forums, and I'm experimenting with removing powernowd and running cpufreqd instead, but to no avail.

BTW, does your T60 have this tiny beep when you're running on batteries?

---

### Post by akvik on 2007-05-29
I think I've found the problem, it seems to be with HAL:
[https://launchpad.net/ubuntu/+source/gnome-power-manager/+bug/39413](https://launchpad.net/ubuntu/+source/gnome-power-manager/+bug/39413)

Solution: I reinstalled HAL and Hal-device manager, and now the "On battery" tab is back again! This didn't fix the beep though, but it's nice to have some progress :)

---

### Post by akvik on 2007-05-29
As for the other problem with the beeping sound, it seems I'm not alone... :
[http://www.thinkwiki.org/wiki/Problem_with_high_pitch_noises](http://www.thinkwiki.org/wiki/Problem_with_high_pitch_noises)

[UPDATE]: Hal is back to misbehaving after restart...

Found this in the forums: [http://ubuntuforums.org/showthread.php?t=321221&highlight=power+manager](http://ubuntuforums.org/showthread.php?t=321221&highlight=power+manager)
> I solved the problem: acpid is started after hald (which is started by dbus), so hald cannot know the battery status. That's why if hald is restarted, gnome power manager (which relies on hal for battery polling) works again. To solve the issue, I simply renamed the symlink that makes acpid start in /etc/rcx.d/ to a lesser number. There was only one rc (I think it was 2 but I'm not sure) that was wrong: the symlink was called S50acpid, while in the other rcs it was called S10acpid, so I simply renamed the S50acpid symlink to S10acpid. I hope I wrote this clearly enough

*Yes, that trick actually worked!*
Now Hal behaves as it is supposed to, plus the Emifreq applet gives the right indications. I changed the symlink in /etc/rc2.d/ from S50acpid to S10acpid (so that acpid loads before dbus - check your list before you do something similar).

The Beep keeps beeping though, since I haven't "forbidden" the processor to scale down to the lowest state of power consumption. I am pretty sure that's what's causing it.

---

