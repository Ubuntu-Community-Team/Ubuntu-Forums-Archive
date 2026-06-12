---
title: "Burn DVD causes sudden reboot"
date: 2009-06-18
forum: Hardware
---

### Post by johanneskoester on 2009-06-18
Hello,
when I want to burn an iso with cdrecord or growisofs the system reboots suddenly during the burn process without an error message.

Has someone an idea what could cause this? It happens at least with 2.6.28 to 2.6.30 kernels. System is Ubuntu intrepid, upgrading is not a choice at the moment.
I did try installing the original cdrecord from the burning ppa, but this does not help.

Maybe somebody at least knows a logfile which persists over reboot where I could find an error message?

System:
Intel D945GCLF2

Edit:
I didn't realise that wodim has to be removed before installing cdrecord.
Cdrecord seems to solve the problem.

---

### Post by markmckee601 on 2009-06-18
You can check the messages log file (/var/log/messages), it's the log file for Post-boot kernel information.

Are you using growisofs and cdrecord directly or using a graphical interface like k3b or gnome-baker?

Is the dvd writer ide or sata?

If the dvd writer is ide, is it using the first ide interface on the motherboard e.g. channel 0 on some boards.

Also if the dvd writer is ide, is it set to master or slave and is your boot hard drive on the same ide ribbon cable as the dvd writer?

---

