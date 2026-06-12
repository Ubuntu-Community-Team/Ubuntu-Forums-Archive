---
title: "Toshiba L775D-S7305 (AMD A6-3400M) Shut down while plugged in restarts automatically"
date: 2011-11-03
forum: Hardware
---

### Post by bbrg548 on 2011-11-03
As noted in the title, I have a Toshiba L775D-S7305 (AMD A6-3400M processor) running Oneiric (32-bit). If I select "shut down" from the menu and in the dialog box, the system shuts down, but then it immediately restarts. This only happens while it's plugged in - on just the battery, it shuts down normally.

I swear I saw this same problem posted in another thread, but I haven't been able to find it, and I don't remember if there was a solution or not.

---

### Post by bbrg548 on 2011-11-12
Bump?

---

### Post by bbrg548 on 2011-11-22
Update and bump: [Known bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/889660"), now being followed in Launchpad.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/889660](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/889660)

---

### Post by bbrg548 on 2012-04-05
Possible solution [here]("https://wiki.archlinux.org/index.php/Toshiba_Satellite_L775D_S7340"). The keyboard/touchpad fix at that site also seems to fix this issue as well.

Just add ```
i8042.nomux=1 i8042.reset
``` to the *GRUB_CMDLINE_LINUX* line in your /boot/grub/grub.cfg file (this appends the command to the end of the 'linux' command line (GRUB legacy's "kernel" line) for both normal and recovery modes.

I haven't had the issue here happen since I did that a couple of days ago.

---

