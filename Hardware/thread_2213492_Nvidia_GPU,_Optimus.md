---
title: "Nvidia GPU, Optimus"
date: 2014-03-26
forum: Hardware
---

### Post by CrackedP0t on 2014-03-26
I'm running Ubuntu GNOME 13.10, on a laptop with an Nvidia GPU that's not being used. Right now, I'm just using my CPU for graphics processing, but if I want to play graphics-intensive games, I'd like to be able to use the dedicated one. I've tried to install drivers several times in the past, but it's always one something terrible to Unity. This is the first time using Ubuntu GNOME, however.
How would I do this?

---

### Post by papibe on 2014-03-26
Hi  CrackedP0t.

Could you post the result of this command?
```
lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by CrackedP0t on 2014-03-26
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: Hewlett-Packard Company Device [103c:181b]
    Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107M [GeForce GT 650M] [10de:0fd1] (rev a1)
    Subsystem: Hewlett-Packard Company Device [103c:181b]
    Kernel driver in use: nouveau


Thanks for responding

---

### Post by papibe on 2014-03-26
Thanks.

Your system has a hybrid graphic system called [Nvidia Optimus]("http://www.nvidia.com/object/optimus_technology.html").

Both GPU's are available to the OS: the Intel integrated graphics and the discrete Nvidia card.

The easiest option to fully use the Nvidia card is to get into the BIOS and look for an option there. The option usually let you choose between Optimus, integrated or discrete.

If your machine does not allow you to do that. There's a couple of options. I know Nvidia is working in supporting Optimus in Linux, so it may be already a beta driver out there that is functional.

The last alternative is to use [Bumblebee]("https://wiki.ubuntu.com/Bumblebee").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by CrackedP0t on 2014-03-26
OK.
The problem with me accessing my BIOS is that I have no idea how to.
My laptop used to run Windows 8, so I always used the UEFI.
However, now, my laptop just boots straight into Ubuntu in less than half a second--no HP logo, nothing.
How would I get into it?

---

### Post by Yellow Pasque on 2014-03-28
Unless you're always hooked to AC power, forget about the BIOS (using the nvidia card for everything is a waste of battery life). Just try Bumblebee.

---

