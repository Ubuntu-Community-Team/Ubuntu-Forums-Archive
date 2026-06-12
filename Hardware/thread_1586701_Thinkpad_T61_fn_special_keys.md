---
title: "Thinkpad T61 fn special keys"
date: 2010-10-02
forum: Hardware
---

### Post by amgmagician on 2010-10-02
I've installed Ubuntu 10.04 on my T61 thinkpad. The first day, special keys (fn key combinations) worked properly! But now (I don't know why!) they don't work! :(

Please help!

---

### Post by luvshines on 2010-10-02
I have T61P too and they are working fine.
Did you shift from gnome to KDE ?

---

### Post by amgmagician on 2010-10-02
No, I didn't shift to KDE. I guess that the fn keys stop working after upgrading linux-image. I also made changes to /etc/default/grub file and I think the problem arise from GRUB_CMDLINE_LINUX variable which its value is "" now while it should be set to something which loads thinkpad_acpi or something like this. I don't know what the original content of the file /etc/default/grub was.

---

### Post by luvshines on 2010-10-02
This is what the lines look like in my grub file:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash"

Are you able to get the acpi events ?? [can try acpi_listen command to check]

---

### Post by amgmagician on 2010-10-02
hmm, I think I should revise my guesses! :D

I tried acpi_listen and just some event like "fn + F4" works and most of them not working and I don't get any event by pressing for example "fn + F2" to lock screen or "fn + F3" for battery information.

---

### Post by amgmagician on 2010-10-03
luvshines, I found the source of problem! Some days ago, I had installed new version of ALSA using AlsaUpgrade script (see [here]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")). After that thinkpad_acpi kernel module couldn't be loaded. The error message was:
```

$ dmesg | grep thinkpad_acpi
[   22.290844] thinkpad_acpi: disagrees about version of symbol snd_ctl_add
[   22.290846] thinkpad_acpi: Unknown symbol snd_ctl_add
[   22.291016] thinkpad_acpi: disagrees about version of symbol snd_card_register
[   22.291018] thinkpad_acpi: Unknown symbol snd_card_register
[   22.291100] thinkpad_acpi: disagrees about version of symbol snd_card_free
[   22.291102] thinkpad_acpi: Unknown symbol snd_card_free
[   22.291561] thinkpad_acpi: disagrees about version of symbol snd_ctl_new1
[   22.291563] thinkpad_acpi: Unknown symbol snd_ctl_new1
[   22.291991] thinkpad_acpi: disagrees about version of symbol snd_ctl_boolean_mono_info
[   22.291993] thinkpad_acpi: Unknown symbol snd_ctl_boolean_mono_info
[   22.292559] thinkpad_acpi: disagrees about version of symbol snd_ctl_notify
[   22.292561] thinkpad_acpi: Unknown symbol snd_ctl_notify
[   22.293770] thinkpad_acpi: disagrees about version of symbol snd_card_create
[   22.293772] thinkpad_acpi: Unknown symbol snd_card_create
```
Actually I didn't see this error message.

I restored Alsa to which is in Ubuntu Repositories and also upgraded my kernel form 2.6.32-24 to 2.6.32-25 and now thinkpad_acpi works perfectly! and fn keys works well too!

---

### Post by amgmagician on 2010-10-03
Sorry! I forgot to THANK you!

THANKS FOR YOUR HELP, luvshines! :D

---

