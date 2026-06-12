---
title: "Creating a true virtual CDROM device, rather than just mounting to folder"
date: 2007-10-05
forum: Hardware &amp; Laptops
---

### Post by GavinZac on 2007-10-05
I am -attempting- to install Mac OS X Tiger on a virtual machine through vmware.

The main problem is that the .iso file is non standard (some strange mac format) so VMWare doesn't mount it properly. When I mount the .iso file through the terminal (mount loop etc etc), it creates a folder, ok - but it doesnt seem to create a device. VMWare specifically will only use something which is represented in the /dev/ folder.

In windows, Daemon tools simply creates a virtual drive, and whatever other software will think its a physical drive. With VMWare on ubuntu, it doesnt recognise the mounted .iso, without a device.

Has anyone got any ideas how this could be achieved? To not only mount an iso as a folder, but to trick VMWare?

---

### Post by Steveway on 2007-10-05
You know that that is illegal?
The Eula of MacOS X forbids it to be run on anything other than an Apple Pc.

---

### Post by GavinZac on 2007-10-05
> **Steveway said:**
> You know that that is illegal?
The Eula of MacOS X forbids it to be run on anything other than an Apple Pc.

Its the Intel Mac OS X, so I dont think that that is true.

Besides, the reason for asking this question isnt any more relevant than asking people what exactly they are doing to their games to make them run in Wine.

---

### Post by Steveway on 2007-10-05
Why should that be a difference?

---

### Post by GavinZac on 2007-10-05
> **Steveway said:**
> Why should that be a difference?

:confused: Because I'd imagine you're permitted to install Intel OSX on Intel foundations?

If we were to differentiate Virtual Machines from physical ones, it'd render VMWare pretty useless, since VMs aren't mentioned in EULA's, eg XP's:

.1 Installation and use.  You may install, use, access,
      display and run one copy of the Software on a single
      computer, such as a workstation, terminal or other
      device ("Workstation Computer").

If you're only intent on discussing the merits of virtualisation, can we do that in a seperate thread rather than derailing this technical question?

---

