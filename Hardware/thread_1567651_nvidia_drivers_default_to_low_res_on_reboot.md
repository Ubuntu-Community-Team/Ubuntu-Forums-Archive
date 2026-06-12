---
title: "nvidia drivers default to low res on reboot"
date: 2010-09-04
forum: Hardware
---

### Post by kja999 on 2010-09-04
Hi,

I am running maverick with the new 256.53 NVIDIA driver.
Everything works fine apart from on reboot the display always defaults back to 800x600.

Each time, I can use the nvidia settings tool to reset back to 1280x1024 without issue.

Has anyone seen this before and knows a solution ? Or is there a bug in maverick I need to report ?

Xorg.conf file is attached...

---

### Post by kja999 on 2010-09-05
Simple in the end. Don't use the nvidia settings program, it obvously has no idea how Xserver works ;)

Use the gnome tool (System>Preferences>Monitors) and everything worked properly...

---

