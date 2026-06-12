---
title: "usb not responding"
date: 2008-12-14
forum: Hardware
---

### Post by jerryroy on 2008-12-14
my usb not responding after i copy a file from the drive. in short it disapears and i have to restart my pc to use it. what can i do to sort this out

---

### Post by Mark_in_Hollywood on 2008-12-15
> **jerryroy said:**
> my usb not responding after i copy a file from the drive. in short it disapears and i have to restart my pc to use it. what can i do to sort this out

Before reading further, backup whatever you don't want to lose from your usb device.

For future reference, please post the terminal output of

lsusb

when asking questions about usb devices, so forum members can see what's what.

As for a solution, my version, and there are undoubtedly others, would be to go to a LiveCD session. Once that is onscreen, open GParted. If you haven't done this before, it's:

Click

System
Administration
GParted

a few moments later, GParted will come on-screen. On the upper right side is a pull down box (do you know what that is?), open that and find your usb device. Select it.

Once the usb device is viewable, right click on the horizontal box, click delete, click again and select format. Follow the onscreen instructions.

Once the device is re-formatted, you need to go back to your regular (not the LiveCD) session, so reboot normally.

Next you must reset the permissions for the usb device.

Alt-F2

type 

gksudo nautilus

enter your password when asked.

When the Nautilus file mgr. opens, find your usb device. Click once on it to highlight it. Right click and click the permissions tab. Set both your user name and your group name to 'read and write'.

Close Nautilus.

Cut, copy & move files to and from the usb device.

---

