---
title: "usb not working in 10.1"
date: 2010-11-28
forum: Hardware
---

### Post by kd4dii on 2010-11-28
Hi all
     I just got a Toshiba Satellite C655-S5056 a few days ago,  It has Windows 7 on it.  I set up a dual boot system with 10.1.  It runs well except the usb is not working.  I see the light on my usb mouse dongle come on as I power up but it goes off as Ubuntu loads and I can't use the mouse or access my external hard drive.  I have tried live cds from several distros like Ubuntu 10.04 and 9.1.  10.04 acts the same as 10.1 and 9.1 sees the usb but not the ethernet connection.
     I would appreciate any help I can get on this.  Thanks.

Bob

---

### Post by dino99 on 2010-11-28
open synaptic (system admin synaptic) and check that:

those packages: mountall, usbmount, toshutils, toshset are installed

---

### Post by kd4dii on 2010-11-28
Hi, thanks for your reply.  Of the four packages you mentioned only 2 were installed, the Toshiba utils were not.  I installed them, do I need to do or run anything?

Bob

---

### Post by kd4dii on 2010-11-29
Hello
     As I mentioned above I installed the programs mentioned above.  Tried running them in the terminal but no joy.  Did some more digging around and found out about shutting off acpi when booting a live cd.  Tried that and booted 10.1 cd w/o acpi and it worked.  Edited my grubconfig file to no acpi and rebooted after running update-grub and it worked.:D
     So problem solved. Thanks for the help.

Bob

---

