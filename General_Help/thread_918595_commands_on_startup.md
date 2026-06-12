---
title: "commands on startup"
date: 2008-09-13
forum: General Help
---

### Post by ykcirt on 2008-09-13
I want to automatically sudo a couple of console commands every time Ubuntu starts up. Doing it manually now, and I think there ought to be an easier way. How would I go about doing this?

---

### Post by iaculallad on 2008-09-13
> **ykcirt said:**
> I want to automatically sudo a couple of console commands every time Ubuntu starts up. Doing it manually now, and I think there ought to be an easier way. How would I go about doing this?


You can add terminal commands which will be executed as root each time the computer boot in /etc/rc.local file. You don't need to add the 'sudo' command since it's already running as root at that point.

---

### Post by Too Late on 2008-09-13
You can also put sudo commands to gnome session autostart properties (System -> Preferences -> Sessions; the files are stored in ~/.config/autostart/). But I think that they wouldn't work if you'd not disabled the sudo password thing in the /etc/sudoers file.

---

### Post by ykcirt on 2008-09-13
Ooh. Well, I think I understand the first post. I'll go with that. ;)

Thanks!

---

