---
title: "VirtualBox NIC questions"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by Bapu on 2009-04-17
I've setup VirtualBox on my Ubuntu OS. I'm restoring my OS for the first VM from a Ghost Backup.

How do set it up so that the IP address is recognized for the VM?

---

### Post by Bapu on 2009-04-17
Uh Oh. A Ghost restore would not boot. I got a BSOD for inaccessible boot device.

So now I guess I need to know how to make an ISO image of my W2K Server.

Anyone have any suggestions? I've never made an ISO let alone of os boot drive/OS.

---

### Post by Bapu on 2009-04-17
Well, after some digging around I discovered that it is advisable to run mergeIDE on the host machine before I create the Ghost Image. Which I did.

Then I set the VM to use Intel 1000 LAN and set it for Bridged. Then in the VM I set the Newtork properties of the newly recognized NIC (in the VM) the way the real NIC was set when the W2K Sever was stand alone.

My first VM is now working and is recognozed in my Windows doamin. This is a DC and it seems to be acting just like it did asa standalone server.

---

