---
title: "Is this hardware capable to install Ubuntu 17.04?"
date: 2017-04-11
forum: Hardware
---

### Post by hd.scania on 2017-04-11
Hello, my friend has a ‘legacy’ hardware whose motherboard and hard drives were OEM by HP and before 2009, and i have no time to check out its BIOS device if shown with UEFI OS compatibility (UEFI has been since 2005), before it can be installed with Ubuntu 17.04.

---

### Post by yancek on 2017-04-11
Ubuntu can be installed using the older MBR method if the machine is not UEFI capable.  Information on the hardware would be necessary to know if or how well Ubuntu might run on it.  The recommended minimus for 16.04 was a 2Ghz processor and 2GB RAM as shown at the link below.

 [https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)

---

### Post by Autodave on 2017-04-11
You may want to look at Xubuntu: simpler desktop and uses less memory. You can still install all of the programs that Ubuntu can install.

---

### Post by hd.scania on 2017-04-11
I have acknowledged only RPM Linux distro are MBR-exclusive (as tested under MY hardware not HIMS, my hardware is now GPT-rEFInd-BIOS, but HIMS is still MBR).
So will ```
/boot/grub
``` be wrought to be acted as BIOS-GRUB bootloaders (instead of GRUB-EFI) under an MBR drive before installing Ubuntu/Xubuntu?
[COLOR=#000000][FONT=&quot]PS HIS hardware has been an HP MicroTower whose architecture is x64, finally whose RAM are <= 3.72G (as told to you it was BEFORE 2009).[/FONT][/COLOR]

---

### Post by pete-br on 2017-04-24
The way to found out if it would work is actually very easy!

Download the ISO of the distro you like. Burn it to DVD or make a USB-Stick with it. (Use UNetBootin of Rufus or similar software to create the USB-Stick)

Then boot it up. Choose 'Try Ubuntu' (that means you boot up a fully functional Ubuntu Linux straight from the DVD or USB-Stick without installing).

If it boots, it should work. (Both BIOS and EUFI are available, so don't worry about that)

---

