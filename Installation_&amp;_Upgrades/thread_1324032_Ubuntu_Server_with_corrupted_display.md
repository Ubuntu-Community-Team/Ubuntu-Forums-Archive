---
title: "Ubuntu Server with corrupted display"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by pawhtiobo on 2009-11-12
Hi all :)

I recently installed ubuntu 9.10 server in a IBM Netfinity 4000R (1GB RAM, 8.9 GB RAID HD's, Chips & Techs F69000 VGA with 2 MB RAM), the installation worked great with no errors, until i restarted the server and it started with a corrupted display of the splash screen, the refresh rate was not configured correctly (i guess), after i updated the distro and rebooted, the splash screen was OK, but the root console had the same problem, corrupted display, i installed the ubuntu-desktop, rebooted, the splash was not ok, the login window was OK, but i couldn't login in to the gnome desktop, it started the login process, but after a few seconds I'm back to the login window, i tried the failsafe-gnome and i was able to login, i added the source of Xorg to the update repository, i updated the system, rebooted, the splash was OK, the root console OK, the login window OK, but this time can't login in gnome or failsafe gnome, the xterm works, i can launch the applications from there and they are showed with no windows decorations. I tried to do the **dpkg-reconfigure -phigh xserver-xorg**, no success, i also tried to generate a xorg.conf with the display modes, screen model, adapter model, etc... the error persists...
I also know that this VGA (cursed one) supports only 1024x768 in 16 mode, and 800x600 in 24 mode... i also read a similar tread in the fedora forum:

[http://forums.fedoraforum.org/showthread.php?t=228131](http://forums.fedoraforum.org/showthread.php?t=228131)

and the bug was in the driver...and someone made a change to it and created a new RPM package to solve the bug...

In attachment i put the xorg log, and as far i can understand in has a lot of errors related to the   [FONT=&quot](insufficient memory for mode)[/FONT] and   [FONT=&quot](bad mode clock/interlace/doublescan)...[/FONT]

Any suggestions... :)???

Thank you in advance...

---

### Post by pawhtiobo on 2009-11-19
Hi all...

Well the problem persists, but i manage to do a workaround, the workaround consists in setting the "DefaultDepth" to 16 the Xorg.conf, this way i can login in to Gnome and the root console is displayed correctly, but with only 640X480, but that's no big deal for me, i installed webadmin and i can manage the server in the web interface, i just needed the GDM has another option to do some configurations. I also tested Debian 5.0 installed in the same server, and after setting the default depth to 16, all the display option work fine...so i thing its a driver/kernel issue with this particular VGA Card in Ubuntu...maybe it will be fixed one day, if it worth the effort... :)

See ya...

---

