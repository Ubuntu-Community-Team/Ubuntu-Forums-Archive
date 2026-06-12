---
title: "Touchpad issue"
date: 2010-11-19
forum: Hardware
---

### Post by andrewgbl on 2010-11-19
I just install Ubuntu 10.10 Maverick yesterday on my Sony Vaio laptop I'm dual booting it with Windows 7 currently untill I get use to it then fully getting rid of Windows to use this I'm trying to figure out a couple of things but seem not to have any luck...I am trying to turn off the tap on my touchpad and I go into [COLOR=Blue]System>Preferences>Mouse[COLOR=Black] no luck with finding that option, also I am trying to bring over my music, etc from Windows to Ubuntu can anyone help me with this situation?[/COLOR][/COLOR]

---

### Post by dino99 on 2010-11-19
Here’s the fix:

1. sudo gedit /etc/default/grub 
to include GRUB_CMDLINE_LINUX=”i8042.nopnp”
2. Run: sudo update-grub
3. Reboot.

*** if no luck:
added i8042.reset i8042.nomux i8042.nopnp i8042.noloop

[https://bugs.launchpad.net/ubuntu/+bug/341094](https://bugs.launchpad.net/ubuntu/+bug/341094)

---

### Post by andrewgbl on 2010-11-19
No dice, did not work...Kinda irritating any other ways?

---

