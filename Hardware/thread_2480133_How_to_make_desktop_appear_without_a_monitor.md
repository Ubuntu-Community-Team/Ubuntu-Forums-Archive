---
title: "How to make desktop appear without a monitor"
date: 2022-10-20
forum: Hardware
---

### Post by webmiester on 2022-10-20
I recently installed Ubuntu 22.04 LTS on a HP Compaq Elite 8300 PC.  My purpose was to connect this PC to my network and if I need anything done in the network, I would control this PC using Real VNC Remote Desktop.
Now here is the thing, when no monitor is connected to this computer, the computer doesn't detect a monitor and it wont display a desktop for the GUI, so when I connect using RealVNC, there is no desktop and I cant manipulate anything.  When the monitor is connected, the RealVNC works just fine.  So No, this isn't a wayland issue as wayland is already turned off.

Is there a way for me to still have a desktop even when there is no monitor connected, like is there a line I can add at the configuration file to do this?  I was using Ubuntu 16 on an older computer, and it would work properly even without a monitor, so I'm surprised that I always need to have a monitor in this setup.  Thank you in advance.

---

### Post by TheFu on 2022-10-20
You need a virtual desktop.  I don't know if VNC or RDP allow that, but I know that x2go does.  x2go uses the NX protocol - which is a more secure, more efficient version of VNC. Authentication is through ssh.  x2go is completely separate from other tools, but setting up ssh first, at least on the remote server, is required.  Since ssh is how Unix systems communicate, the idea that someone wouldn't have ssh setup is completely foreign to me and all other Unix/Linux professionals. It is the only package that I ensure is installed on all my Unix systems.

The x2go / NX virtual desktop doesn't care if there is or isn't real hardware. It won't be displayed anyway.  I've used x2go from 5 continents.

But inside the same LAN, I seldom use NX.  There are better options, like the built-in X11 forwarding that ssh supports.  I don't know if Wayland works with it or not. In theory, XWayland should work, but Wayland breaks many of my workflows and automation, so I can't use it.

Try x2go or ssh X11 forwarding. These don't care about having a monitor or even a GPU inside the remote system.

---

### Post by webmiester on 2022-10-21
> **TheFu said:**
> You need a virtual desktop.  I don't know if VNC or RDP allow that, but I know that x2go does.  x2go uses the NX protocol - which is a more secure, more efficient version of VNC. Authentication is through ssh.

The x2go / NX virtual desktop doesn't care if there is or isn't real hardware. It won't be displayed anyway.  I've used x2go from 5 continents.

But inside the same LAN, I seldom use NX.  There are better options, like the build-in X11 forwarding that ssh supports.  I don't know if Wayland works with it or not. In theory, XWayland should work, but Wayland breaks many of my workflows and automation, so I can't use it.

Try x2go or ssh X11 forwarding. These don't care about having a monitor or even a GPU inside the remote system.

Thank you for this suggestion.  I am not familiar with x2go yet.  So how does this work?  Does X2go replace VNC completely or do I install X2go and then log into the computer using VNC?

---

### Post by mIk3_08 on 2022-10-23
> **TheFu said:**
> Try x2go or ssh X11 forwarding. These don't care about having a monitor or even a GPU inside the remote system. Thanks TheFu. I'll save this info because maybe I'll use it in the near future. Regards and cheers.

---

