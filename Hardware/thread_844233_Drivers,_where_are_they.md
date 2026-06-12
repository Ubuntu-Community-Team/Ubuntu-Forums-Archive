---
title: "Drivers, where are they ?"
date: 2008-06-29
forum: Hardware
---

### Post by glx51mm on 2008-06-29
Hello everyone,
I have installed ubuntu 8.0.4 on two laptops, hp 530 and hp pavilion dv5000.
Most of the things work great on both but there seems to be some trouble with the graphics driver on both. I tried to find where the installed drivers are listed but no luck. Where can I see what drivers are installed on the system ?
The strange thing is that on the pavilion, when running the live cd, the desktop effects work great but after installing the os they can't be enabled.

Thanks in advance for your help.

---

### Post by AlexBellisBrown on 2008-06-29
Whats the name/model of the Graphics Card?

---

### Post by phidia on 2008-06-29
From the top panel/menu click System>Admin>Hardware drivers.
You can check or enable your video card there.

If your card doesn't show there you can search the forums-specifically the multimedia and video section to find how your card can be made to work.

---

### Post by claschxtreme on 2008-06-29
HP530         - Intel Graphics Media Accelerator 950
HP Pav DV5000 - ATI Radeon XPRESS 200M

Is that right?

---

### Post by glx51mm on 2008-06-29
The hp 530 has the 945gme and the other the 945gm. About the 530 there is a thread explaining what is wrong.
I already tried the "hardware drivers" which is empty.
However, i am not only concerned about the graphics drivers but all the system drivers. Isn't there anything that can show all drivers installed on the system ? For example both wired and wireless net work fine but where can i see what drivers are being loaded for these devices ? Is there something like the windows device manager for example?

---

### Post by bford16 on 2008-06-29
> **glx51mm said:**
> The hp 530 has the 945gme and the other the 945gm. About the 530 there is a thread explaining what is wrong.
I already tried the "hardware drivers" which is empty.
However, i am not only concerned about the graphics drivers but all the system drivers. Isn't there anything that can show all drivers installed on the system ? For example both wired and wireless net work fine but where can i see what drivers are being loaded for these devices ? Is there something like the windows device manager for example?
I have an HP dv8110us with the same ATI video card. Xubuntu did not detect the card right away. I had to do some updates first, then reboot twice! to make the system detect the proprietary hardware. Once it was detected, it was very easy to install the drivers.

Here are some commands that can help identify hardware.
lspci (lists pci devices)
lsusb (lists usb devices, if any are plugged in)
lsmod (lists kernel modules loaded)

---

