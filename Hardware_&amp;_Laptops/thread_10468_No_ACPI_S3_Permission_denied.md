---
title: "No ACPI S3: Permission denied"
date: 2005-01-08
forum: Hardware &amp; Laptops
---

### Post by mrdc76 on 2005-01-08
Hey,

If I do the the "sudo echo 3 > /proc/acpi/sleep" I get "bash: /proc/acpi/sleep: Permission denied". What could be the problem? My user account is in the following groups: "mrdc adm dialout cdrom floppy audio video plugdev lpadmin scanner".
Everything should be ok, right?

---

### Post by crane on 2005-01-08
I ran into the same problem trying to enter :
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

The only way I was able to enter the command was as root, not sudo.
I had to enable root access with --> sudo passwd root.

entered old password, then entered new password. This enabled me to either completely switch to root or even log in as root if I so wished.

then I typed su, entered password switched to root, entered command and it worked fine.

---

### Post by Arjunanda on 2006-05-04
How do I permanently change the write permission for all for this /proc/acpi/sleep file, as it in the proc file system and the permission will fall back to default after each bootup? Which is the right startup script where to enter chmod o+w /proc/acpi/sleep to make the suspend to work?

---

### Post by Arjunanda on 2006-05-04
More testing,

running the following command, that should suspend to RAM given as root works perfectly:
echo mem > /sys/power/state
The system goes down (to hibernate?) and can be awaken with hitting space.

But the following, that should (suspend to disk) - does not:
echo mem > /sys/power/state
The system goes down and all seems to go fine, but it is impossible to awake the system. I had to hit the power key, and this caused just normal bootup.

How could I enable the suspend command in some practical way gnome?

---

### Post by Arjunanda on 2006-05-19
Lots of frustration, seeking and searching behind. Now today, almost 2 months after installing Ubuntu on my Acer Aspire laptop I finally got the suspend working. The key was here:
```
sudo apt-get install gnome-power-manager
```

This install nice tool, that you can run on the system tray and control the laptop power/battery functions.

---

