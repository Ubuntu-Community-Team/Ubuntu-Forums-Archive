---
title: "Lost desktop, system access"
date: 2008-09-18
forum: General Help
---

### Post by diver858 on 2008-09-18
I am relatively new to Ubuntu and Linux. Successfully installed 8.0.4 as a dual boot with Win XP on a Dell XPS-M140 laptop.

After several successful sessions, I attempted to run Ubuntu; it booted properly, asked for login information, but the desktop would not load - only a blank orange screen, with a small (~3" on a side) white square in the top left corner of the screen. The mouse continued to work - showed an arrow on the screen, but turned to a cursor when over the white area. As no keystrokes seemed to be effective, I manually powered the system down and tried again - same result. I then attempted to try some of the recovery options, booting in safe mode, with no success. Rather than waste time, I was able to reinstall an image of the partition, but would like to know what might have caused this condition, and what actions to take should it reoccur.

TIA!

---

### Post by Titan8990 on 2008-09-18
I find that on some rare occasions Gnome just takes a few minutes to load. It would appear that it has locked up but actually it could just still be loading. This issue occurs for me when switching from XFCE to Gnome.

---

### Post by prshah on 2008-09-18
> **diver858 said:**
> but would like to know what might have caused this condition, and what actions to take should it reoccur.


Well these tips are academic now; but try:

a) Restarting the X server (Ctrl_Alt_BkSpace)

b) Restarting GDM: Switch to a Virtual Terminal with Ctrl_Alt_F1, then login and give the command ```
sudo /etc/init.d/gdm restart
```

If the problem still persists, a list of programs running at the time and the (partial) output of the message log can give useful clues:```

top -b -n 1
tail /var/log/messages
#for good measure
tail /var/log/Xorg.0.log 
```

---

### Post by diver858 on 2008-09-18
> **Titan8990 said:**
> I find that on some rare occasions Gnome just takes a few minutes to load. It would appear that it has locked up but actually it could just still be loading. This issue occurs for me when switching from XFCE to Gnome.

Thanks - considered that on the second reboot - don't believe it was the case.

---

### Post by diver858 on 2008-09-18
> **prshah said:**
> well these tips are academic now; but try:

A) restarting the x server (ctrl_alt_del)

b) restarting gdm: Switch to a virtual terminal with ctrl_alt_f1, then login and give the command ```
sudo /etc/init.d/gdm restart
```

if the problem still persists, a list of programs running at the time and the (partial) output of the message log can give useful clues:```

top -b -n 1
tail /var/log/messages
#for good measure
tail /var/log/xorg.0.log 
```

thank you!

---

