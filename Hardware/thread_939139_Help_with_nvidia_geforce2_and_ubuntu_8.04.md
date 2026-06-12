---
title: "Help with nvidia geforce2 and ubuntu 8.04"
date: 2008-10-05
forum: Hardware
---

### Post by eliwis on 2008-10-05
Hi, I just installed ubuntu 8.04 on a HP desktop machine with an nvidia geforce2 video card, and I have a major problem:
For some reason the maximum resolution that i can get to display on the screen is 800x600. I tried checking the nvidia legacy driver in System/Administration/Hardware Drivers, and that doesn't help.
I also tried using EnvyNG to install drivers, and that didn't help at all.

would you have any idea what to do?

any help will be greatly appreciated.

thanks

---

### Post by eliwis on 2008-10-07
Please, I still cant use resolution above 800x600.
:sad:

---

### Post by 3rag0n on 2008-10-07
I'm not sure this will work, but...
go to nvidia's site and download the proprietary driver from there ( 18.9 MB )
Paste it to your home dir and name it nvidia.run.

now kill your graphics system and go to command line mode :try Ctrl+Alt+F1.

You should see a command line environment.

navigate to your home dir and type :

*sudo sh nvidia.run*
and follow the rest of the guided installation.


if this does not work, then in command mode, become root and type *sh nvidia.run* and finish the driver installation.

----------
If you do not see a command line environment,
Reboot and go into the recovery mode.
enter the root password.
go to your home dir, not root's home dir.
type *sh nvidia.run* and you'll know what to do next.

---

### Post by 3rag0n on 2008-10-07
I'm not sure this will work, but...
go to nvidia's site and download the proprietary driver from there ( 18.9 MB )
Paste it to your home dir and name it nvidia.run.

now kill your graphics system and go to command line mode :try Ctrl+Alt+F1.

You should see a command line environment.

navigate to your home dir and type :

*sudo sh nvidia.run*
and follow the rest of the guided installation.


if this does not work, then in command mode, become root and type *sh nvidia.run* and finish the driver installation.

----------
If you do not see a command line environment,
Reboot and go into the recovery mode.
enter the root password.
go to your home dir, not root's home dir.
type *sh nvidia.run* and you'll know what to do next.

---

### Post by eliwis on 2008-10-09
I got it to work using EnvyNG, just had to install and reinstall the drivers a few times, wierd...

thanks anyway!

---

