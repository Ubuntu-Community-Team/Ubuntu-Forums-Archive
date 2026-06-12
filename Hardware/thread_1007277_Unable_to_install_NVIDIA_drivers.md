---
title: "Unable to install NVIDIA drivers"
date: 2008-12-10
forum: Hardware
---

### Post by cliffcolli on 2008-12-10
I have a fresh install of Ubuntu 8.10 and I'm unable to install NVIDIA drivers and change the resolution of my display to 1600x1200.

I've used HW Drivers application to install version 177 of the driver, but when I try to boot the machine, the following errors appear and X fails to start:

(EE) NVIDIA(0): Failed to initialize the NVIDA graphics device PCI:0:5:0
(EE) NVIDIA(0): Failed to initialize the NVIDA graphics device!
(EE) Screen(s) found, but none have a usable configuration

If I run 'sudo lspci' I see the following entry:

00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2).

I've tried re-installing, installing the NVIDIA drivers from their website, all to no avail.  Please help!!!

---

### Post by Beavis6953 on 2008-12-10
did you try envy. search for it in the packages.

then the command is envyng.

Thats my guess.

---

### Post by Ayuthia on 2008-12-10
Hardware Drivers usually installs nvidia-glx-177 but envyng should work also.

---

### Post by ions on 2008-12-10
I am having the same problem.

---

### Post by ions on 2008-12-10
Problem was somehow I now have the server kernel after upgrading to 8.10 from 8.04 and did not have the correct headers.  No idea how that happened but it's working now.

---

### Post by cliffcolli on 2008-12-12
I installed envy via synaptic, then uninstalled the NVIDIA driver and reinstalled via envyng, with the same issue.

---

