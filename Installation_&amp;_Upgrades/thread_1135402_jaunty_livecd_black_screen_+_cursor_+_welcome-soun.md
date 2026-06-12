---
title: "jaunty livecd: black screen + cursor + welcome-sound after login, then nothing. help?"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by pavel__ on 2009-04-24
hi!

just downloaded and burned 9.04 32-bit. booting from live-cd, everything goes fine, but after login, i see only a black screen, hear the welcome-jingle and can move the cursor. then nothing happens, gnome doesn't load, system doesn't response. i can switch to another tty and perform sudo commands, but nothing seemed to help:

[LIST]
[*] removing compiz, gnome-power-manager and nvidia-*
[*] booting with acpi=off and/or graphic safe mode
[*] copying my old xorg.conf into /etc/X11
[/LIST]

running on lenovo 3000 n100 notebook.

some info:

```
$ lspci -nn | grep VGA
 00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)

$ uname -a
Linux slick 2.6.27-14-generic #1 SMP Wed Apr 15 18:59:16 UTC 2009 i686 GNU/Linux

```

does anybody experience the same and how did you fix it? i'm not going to upgrade my production system until i can at least get the live-cd running.

thanks!

p.

---

### Post by pavel__ on 2009-04-26
/var/syslog ends up with following lines
```
Apr 26 12:00:13 ubuntu console-kit-daemon[3773]: WARNING: Couldn't read /proc/3772/environ: Failed to open file '/proc/3772/environ': No such file or directory 
Apr 26 12:00:24 ubuntu kernel: [  176.228049] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Apr 26 12:01:08 ubuntu x-session-manager[4441]: WARNING: No required applications specified 
Apr 26 12:03:06 ubuntu x-session-manager[4441]: WARNING: Failed to send buffer 
Apr 26 12:03:06 ubuntu x-session-manager[4441]: WARNING: Failed to send buffer 
Apr 26 12:03:06 ubuntu x-session-manager[4441]: WARNING: Running '/usr/bin/gconftool-2 --shutdown' at logout returned an exit status of '15' 

```

other logs seem to contain nothing unusual..

any ideas?

p.

---

