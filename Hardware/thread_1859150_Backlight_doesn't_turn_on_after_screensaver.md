---
title: "Backlight doesn't turn on after screensaver"
date: 2011-10-13
forum: Hardware
---

### Post by Sanya_M on 2011-10-13
After screen is turned off by power manager or screensaver, backlight doesn't automatically turn on when I move the mouse or press a key. It is especially annoying when the screen is locked, because I have to type my password blindfold. After the screen is unlocked, I can get the backlight back by pressing increase brightness key. This key doesn't work when screen is locked.

After suspend or hibernate backlight turns on as it should.

I have HP Pavilion dv6-6179er laptop with hybrid graphics (Intel HD 3000 + Radeon HD 6770M), discrete card is turned off on startup using vgaswitcheroo (in rc.local). Radeon module is blacklisted and loaded only before call to vgaswitcheroo, because when it isn't blacklisted splash screen doesn't appear. I'm using ubuntu 11.10. Backlight control started working only with 3.0 kernel and acpi_backlight=vendor boot option.

This problem also appeared in fedora 15, 16, debian (gnome), xubuntu (11.10 beta).

I tried "acpi_osi=Linux" option, but it didn't help.

Maybe there is a way to execute a script when unlock dialog appears?

---

### Post by kahwedyich on 2011-10-15
Hi.

I also own a HP with hybrid graphics, but backlight doesn't work at all in 11.10.
I used switcheroo and blacklisted the radeon driver in 11.04, but that doesn't work since I've upgraded system.

Can you give me a further explanation on that acpi boot option?

---

### Post by Sanya_M on 2011-10-16
in /etc/default/grub:
replace line > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" with > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
then run > sudo update-grub and reboot. For me it disables non-working acpi_backlight0 and acpi_backlight1 in /sys/class/backlight so only intel_backlight remains and everything starts to work (except the problem I've described).

---

### Post by kiriyama9000 on 2011-10-17
I have a HP Mini 110 and just did the "Upgrade" to 11.10 and have this same issue.

The brightness cannot be increased with the function keys for some reason, so I have to flat out restart after this happens.

---

### Post by Antarell on 2011-10-17
> **Sanya_M said:**
> in /etc/default/grub:
replace line  with 
then run  and reboot. For me it disables non-working acpi_backlight0 and acpi_backlight1 in /sys/class/backlight so only intel_backlight remains and everything starts to work (except the problem I've described).

I have found sometimes when my DV6-6023 wakes up the backlight is at the lowest, which for some reason is off. Try bump the brightness up with Fn-F3 and see if that wkes it up.

---

### Post by Sanya_M on 2011-10-18
Fn-F3 doesn't work when screen is locked (unlock dialog shown)

---

### Post by rbslime on 2011-10-19
I'm seeing the same problem on an Asus U31A.

There's a bug report here:
[URL="https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/872652"]https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/872652
[/URL]

There is a patch to gnome-settings-daemon that resolves the issue, but I have not applied it yet.

---

### Post by Antarell on 2011-10-20
> **Sanya_M said:**
> Fn-F3 doesn't work when screen is locked (unlock dialog shown)

This would be true. That's in the list of things I ditch when I install (the lock password). I have also switched to Kubuntu as Gnome/Unity have gone to the dogs!

---

