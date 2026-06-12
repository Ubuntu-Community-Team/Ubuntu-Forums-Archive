---
title: "smooth wubi install of Ubunto 8.04.1 on a Libretto U100"
date: 2008-07-08
forum: Hardware
---

### Post by Anfanglir on 2008-07-08
A short note to any Toshiba Libretto U100 users that are hesistant to try Ubuntu (since there are some problems reported in old threads on previous Ubuntu versions). 

I made a Wubi-install of Ubuntu 8.04.1 from Windows XP, it went very smoth, no hitches!  The system runs smooth and fast (Libretto U100-S213, 1 gb ram). The Libretto has some non-standard properties, like a 7.2 screen @ 1280x768 pixels, and an external docking station with cd/dvd-burner. These seem to be recognised and configured correctly, no tweaking needed (havent burned anything yet though). Likewise ethernet jack, pc-card and usb works on first try. The built in wifi finds my router, but I've forgotten what wep key I used, lol damn.

Ubuntu owns OK!

EDIT: forgot to say that suspend works as well, I have set the Libretto to suspend when I close the lid - it goes into suspend mode as expected, and resumes the session when the lid is opened again.

---

### Post by Anfanglir on 2008-07-08
Remembered wep key at last, so now I can confirm that wireless works as well.

---

### Post by Anfanglir on 2008-07-10
After messing around a bit with the wubi install I decided to try a normal harddrive install of Ubuntu Hardy Heron on the Libretto U100, since hibernation is not supported in wubi. 

First I tried to boot and install from CD, the OS installed but not the boot-menu, the Libretto went straight into XP after reboot. Had another go, this time running the Live CD and installing from the desktop of the live session. Now everything worked smoothly and upon reboot i get the boot menu and can choose between Ubuntu and XP.

As before with the wubi install everything seem to work. The only thing I have had to configure manually so far is the SD drive. After some searching here on the forum and with Google i found out how to do it. Here's a how-to in case another newbie wants to configure a Libretto:

press Alt+F2 to get Run application window, write:

gksudo nautilus
press enter
give password when prompted

A file manager windows with Root/administrator privileges open. Browse to: 

/etc/modprobe.d/options

and open the file (right click, open with text manager). Add the lines:

#SD Card reader
options wbsd irq=11 nopnp=1

Save and close. 

Then hit Alt+F2 and write:

sudo rmmod wbsd
sudo modprobe wbsd

Insert a SD card, it should now automount.

/ Anfanglir

---

