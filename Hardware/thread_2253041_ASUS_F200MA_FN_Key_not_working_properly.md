---
title: "ASUS F200MA FN Key not working properly"
date: 2014-11-16
forum: Hardware
---

### Post by noisekickkk on 2014-11-16
Hello Ubuntu Forum!

I do have some problems to get my FN+F5 and FN+F6 Keys working on Ubuntu.
The Model is ASUS F200MA, i have installed the latest Ubuntu 14.04. LTS release -  also did the updates from the official update center.
I did some researches and also tried some solutions to fix my problem:

1. modify the grub file in etc/default/grub - no success
2. installed xbacklight, tried to manually key bind "xbacklight inc/dec" - no success

**Only thing that worked for me:** to modify the /etc/rc.local
added the code line:
"echo 4 > /sys/class/backlight/acpi_video0/brightness"
-> i can now finally change the brightness level... :)

So do you guys maybe have an idea? Btw i had Win 8.1. installed before on that machine (it was pre-installed) - there the shortcuts worked.

Really appreciating any help, thanks in advice. ):P

---

### Post by Pilot6 on 2014-11-17
You need to do two things.

1. sudo gedit /etc/default/grub
And set there
[COLOR=#000000][FONT=dejavu sans mono]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="
[/FONT][/COLOR]  [COLOR=#000000][FONT=dejavu sans mono]
Then

sudo update-grub
[SIZE=2]2. sudo gedit /usr/share/X11/xorg.conf.d/[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Beta]20-intel.conf

And paste there

[/FONT][/COLOR]```
[COLOR=#000000][FONT=dejavu sans mono]Section "Device"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]   Identifier  "card0"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]   Driver      "intel"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]   Option      "Backlight"  "intel_backlight"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]   BusID       "PCI:0:2:0"[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]EndSection[/FONT][/COLOR]
```

---

### Post by noisekickkk on 2014-11-17
Thanks a lot! That worked. - Seems like i had bad formatting in my 20-intel.conf file.

Btw everytime im changing something in a conf/grub file - the terminal responses with:

```
(gedit:2382): Gtk-WARNING **: Calling Inhibit failed:  GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name  org.gnome.SessionManager was not provided by any .service files 
```

Is it better to run such commands with "gksudo" instead of "sudo"?

---

### Post by Pilot6 on 2014-11-17
Don't worry about that message in terminal. It's OK when you edit from root. This is just a warning.

---

### Post by sbaragnaus on 2014-12-03
Thank you, it also worked for me.

Please note in grub configuration I've added this line:

[COLOR=#000000][FONT=dejavu sans mono]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="[/FONT][/COLOR]

---

