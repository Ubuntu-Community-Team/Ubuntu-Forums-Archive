---
title: "Booting in Legacy Mode Dell Inspiron 3670"
date: 2021-07-05
forum: Hardware
---

### Post by angel mike on 2021-07-05
I have installed Ubuntu 20.04 using an external dvd in Legacy Mode - the UEFI option does not accept external devices on the Dell Inspiron 3670.
The install was successful and on restarting the GNU Grub v2.04 appeared on the screen with command line options.

What do I do next?

---

### Post by oldfred on 2021-07-05
Most systems if UEFI, can boot external drives in UEFI mode.

Dell  Inspiron 3670 UEFI update & AHCI worked
[https://ubuntuforums.org/showthread.php?t=2412152](https://ubuntuforums.org/showthread.php?t=2412152)

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by angel mike on 2021-07-05
Thanks Oldfred - quick on the ball as ever!
Will look at the links you sent but in the first instant I remember my previous problems with installing from external devices. Your comment about UEFI set off my train of thought to using F12 and the Dell recovery file that I put on a USB. Hopefully this will work - if so will be back to mark 'Solved'

---

### Post by angel mike on 2021-07-09
I am still having trouble even using the F12 key. Although the Dell Inspiron 3670 has both systems UEFI and legacy - it seems only the latter can be used to load external devices. I did load the new version of Ubuntu 20.04 successfully and then asked to reboot - this then gave me the GRUB command menu. Are there a few commands that will bootup the installed Ubuntu ?

---

### Post by angel mike on 2021-07-09
Just to add - a used an external DVD drive with the Legacy Mode

---

