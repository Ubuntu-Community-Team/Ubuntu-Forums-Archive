---
title: "Can compiz be enabled with Nvidia Legacy?"
date: 2008-08-12
forum: General Help
---

### Post by zieglerj on 2008-08-12
I'm helping out a friend who is new to Ubuntu and we're having some problems getting compiz going for him.
The read-out from compiz check is:
Gathering information about your system...

Distribution: Ubuntu 8.04
Desktop environment: GNOME
Graphics chip: nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 15)
Driver in use: nv
Rendering method: None

Checking if it's possible to run Compiz on your system... [SKIP]

Checking for hardware/setup problems... [SKIP]

At least one check had to be skipped:
Error: No rendering method in use (AIGLX, Xgl or Nvidia)

Would you like to know more? (Y/n) y

The nv driver is not capable of running Compiz, you need to install the
proper driver for your graphics card.

Check if there's an alternate (proprietary) driver available? (Y/n) n

The driver he has set-up is through Envy NG. The restricted driver that ubuntu originaly used didn't allow me to enable compiz either. I know his video card is a little old but isn't there anything I can do to get compiz working for him?

---

### Post by overdrank on 2008-08-13
> **zieglerj said:**
> I'm helping out a friend who is new to Ubuntu and we're having some problems getting compiz going for him.
The read-out from compiz check is:
Gathering information about your system...

Distribution: Ubuntu 8.04
Desktop environment: GNOME
Graphics chip: nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 15)
Driver in use: nv
Rendering method: None

Checking if it's possible to run Compiz on your system... [SKIP]

Checking for hardware/setup problems... [SKIP]

At least one check had to be skipped:
Error: No rendering method in use (AIGLX, Xgl or Nvidia)

Would you like to know more? (Y/n) y

The nv driver is not capable of running Compiz, you need to install the
proper driver for your graphics card.

Check if there's an alternate (proprietary) driver available? (Y/n) n

The driver he has set-up is through Envy NG. The restricted driver that ubuntu originaly used didn't allow me to enable compiz either. I know his video card is a little old but isn't there anything I can do to get compiz working for him?

Hi and I do not believe that card will support compiz or 3d. :(

---

### Post by zieglerj on 2008-08-13
Is there an older version that could work or maybe a different desktop effects program?

---

### Post by Kevbert on 2008-08-13
You could try using the nvidia driver.  You need to edit a file.  In terminal enter
```
sudo gedit /etc/X11/xorg.conf
```
Look for the line that says
```
Driver     "nv"
```
and change it to 
```
Driver     "nvidia"
```
Save the file and reboot the machine.  Now run compiz-check again.

---

