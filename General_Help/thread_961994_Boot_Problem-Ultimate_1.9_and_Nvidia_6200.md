---
title: "Boot Problem-Ultimate 1.9 and Nvidia 6200"
date: 2008-10-28
forum: General Help
---

### Post by Buschbarber on 2008-10-28
HP Media Center PC m7060n, 3Ghz P4, 2Gb ram, Nvidia Gforce 6200 OC, WinTV HVR1600. All apps seem to work fine, including MythTV, except Google Earth boots with an Unknown Graphics Card error

I still have not been able to get a handle on a problem in which I cannot boot Ultimate 1.9, with the Nvidia PCI card installed, unless I set the PC BIOS default video to Onboard, instead of PCI.

As a result, I have a monitor connected to both the Nvidia card and the Integrated Intel Adapter. When the PC boots, the BIOS Splash Screen and the Grub Menu appear on the monitor connected to the Intel adapter and then Ultimate automatically switches to the Nvidia driver and displays on the monitor connected to the Nvidia card.

If I try to set the PC BIOS default video to PCI, Ultimate 1.9 will hang and never finish booting. At that point, it will not respond to any Keystrokes, as well.

It does this With or Without the Nvidia Restricted Drivers

Mandriva 2009 also requires that the PC BIOS video default be set to Onboard, however, Mandriva will not switch to the Nvidia driver and boots up on the monitor connected to the Onboard Intel adapter.

Microsoft XP MCE has no problems booting with the PC BIOS default video set to PCI. If the PC BIOS default video is set to Onboard, XP switches to the Nvidia driver like Ultimate does, and displays on the monitor connected to the Nvidia card.

I would much prefer Linux over Windows, however.

---

