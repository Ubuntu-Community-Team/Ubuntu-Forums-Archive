---
title: "&quot;Windows could not start...&quot;. how to force a boot from CD?"
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by misterloogs on 2009-02-09
i have a toshiba laptop with windows XP installed. some months ago it stopped booting up properly with this message:
> 
Windows could not start because the following file is missing or corrupt:
\WINDOWS\SYSTEM32\CONFIG\SYSTEM
You can attempt to repair this file by starting Windows Setup using the original Setup CD-ROM.
Select 'r' at the first screen to start repair.

i no longer have this window setup disk. i managed to recover the contents of my hard drive and would now like to install ubuntu on the laptop, and it's fine if i lose my old hard-drive contents (including XP) because i have everything backed up. i downloaded the .iso for ubuntu 8.10 and inserted it into my laptop. i tried pressing a few keys when i saw the message above (Delete, F10, Ctrl), but they don't seem to matter.

how can i force my laptop to boot off of the inserted CD?

---

### Post by cyfur01 on 2009-02-09
This is a BIOS setting you need to adjust. Right after you turn on your computer, there should be mention somewhere about pressing a key to enter setup or configure your BIOS, which will likely be DEL, F2, F10 ,F12 or somehting.. varies from computer to computer.

Then, once you're in the VIOS configuration menus, you need to find where it mentions the boot order, and set it so that hte CD drive has a higher priority than your hard drive. Then, save the settings and reboot.

---

### Post by misterloogs on 2009-02-09
nevermind. i found a solution that works in a thread titled "How to force boot from CD?" (Ubuntu Forums > The Ubuntu Forum Community > Forum Archive > Absolute Beginner Talk). i had to hold down the 'ESC' key to skip the default boot sequence, then F1 to move the CD to be the first in the boot order.

---

### Post by misterloogs on 2009-02-09
sorry cyfur01, didn't see your post until just now. thanks anyway!

---

### Post by Tomatz on 2009-02-09
> **misterloogs said:**
> i have a toshiba laptop with windows XP installed. some months ago it stopped booting up properly with this message:

i no longer have this window setup disk. i managed to recover the contents of my hard drive and would now like to install ubuntu on the laptop, and it's fine if i lose my old hard-drive contents (including XP) because i have everything backed up. i downloaded the .iso for ubuntu 8.10 and inserted it into my laptop. i tried pressing a few keys when i saw the message above (Delete, F10, Ctrl), but they don't seem to matter.

how can i force my laptop to boot off of the inserted CD?
 

EDIT: too early :P

---

