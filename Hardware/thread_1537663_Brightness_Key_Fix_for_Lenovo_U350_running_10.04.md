---
title: "Brightness Key Fix for Lenovo U350 running 10.04"
date: 2010-07-23
forum: Hardware
---

### Post by Betobuntu on 2010-07-23
I came across this fix, sadly i dont remember from where. It so that you can use the Fn+Up/Fn+Dn to adjust desired brightness on your display. This worked on a lenovo U350 running 10.04

open terminal type in:

             sudo nano /etc/default/grub

Change:
 [INDENT]GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
[/INDENT] to


             GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi backlight=video"

also change:

             GRUB_CMDLINE_LINUX_DEFAULT=”"

to

             GRUB_CMDLINE_LINUX="nomodeset acpi backlight=video"

then run:

              sudo update-grub

---

### Post by Kopasakis on 2010-09-05
hi im having a brightness issue myself i tried the fix but once i change 

> GRUB_CMDLINE_LINUX_DEFAULT=”"

to

             GRUB_CMDLINE_LINUX="nomodeset acpi backlight=video"


i don't know how to exit the code and go back to the terminal to run the grub updater

---

### Post by Kopasakis on 2010-09-05
nvm got it to work just supplemented sudo nano for gksudo gedit then just saved and ran the update thanks :KS

---

### Post by crowderd on 2010-09-20
Awesome fix!! I have been using Ubuntu for a few years now and never cared to find this. This worked on my g530. Thank you

---

