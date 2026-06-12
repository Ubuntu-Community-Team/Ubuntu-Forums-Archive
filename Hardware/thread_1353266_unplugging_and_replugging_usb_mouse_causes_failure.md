---
title: "unplugging and replugging usb mouse causes failure to detect"
date: 2009-12-12
forum: Hardware
---

### Post by JoeJaz2 on 2009-12-12
Hello all, 
  I'm using kbuntu 9.10 on an IBM ThinkCentre desktop computer.  What's odd is that after booting to the KDE desktop, if I unplug the USB mouse and re-plug it in, the os fails to detect the mouse.  The "red light" of the optical mouse does not even glow.  
  This doesn't seem to be an X or KDE problem because if I stop X, run gpm from a virtual terminal, and preform the same unplug/plug operation, the mouse fails to work.  
  In either a desktop environment or using gpm, if I reboot, the mouse begins working again.  Also, I've found that if I run the command "lsusb" after the mouse is disabled, the mouse activates and becomes usable.  It's as if some hotplug detection doesn't trigger when I plug the mouse into the USB port.  This is a brand new installation of Kbuntu, so I've barely touched it. 
  I'm giving the computer to my parents and want them to see how cool Linux is, so I'd like it work as seamlessly as possible for them.
  Any help is much appreciated.
Thank you,
Joe

PS. If it helps, here is a link to my lshw output:
[www.jazstudios.com/a/devices.html](www.jazstudios.com/a/devices.html)

---

### Post by Dennis N on 2009-12-12
Just a comment fwiw:

This does not address the issue you are having, but if you are giving your machine to your parents, they would probably not even notice the mouse problem. It seems you would very rarely need to unplug the mouse since it is a desktop machine (I don't think my desktop mouse has ever been unplugged).

---

### Post by JoeJaz2 on 2009-12-13
Ya, I guess overall it's not a huge problem in the grand scheme of things.  I can just instruct them to reboot if they do need to unplug the mouse.  In this day and age of Linux, about the last thing I expect to have is a problem with a normal USB mouse.  But such is the case sometimes I realize. Thank you for your reply.

---

### Post by JoeJaz2 on 2009-12-13
Actually determined that this extends to all USB devices, not just mice.  Including USB flash drives.  Now that is more annoying as plugging and unplugging flash drives is a pretty common task.  Perhaps I should open up an Ubuntu bug report... however that is done.

---

