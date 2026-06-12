---
title: "Update on Epson Stylus CX4300 CX4400 CX4450 CX5500 CX5600 DX4400 DX4450"
date: 2008-09-06
forum: Hardware
---

### Post by jl6 on 2008-09-06
Dear Ubuntu users,

The thread "_[[SOLVED] Epson Stylus CX4300 CX4400 CX4450 CX5500 CX5600 DX4400 DX4450]("http://ubuntuforums.org/showthread.php?t=627471")_" is now closed, so I thought I'd start a new thread to post some updates on it.

Firstly, the title is incorrect as the problem of setting up these devices is NOT yet solved for everybody.

Secondly, _[this "bug"]("https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/156085")_ is probably the cause of a lot of peoples' troubles. Since /proc/bus/usb is empty on newer versions of Ubuntu, the scanner may not be found. There is a workaround posted in that launchpad thread, but it is not recommended. I did get an Epson DX4450 to scan properly with iscan and xscan on Ubuntu 7.10 though.

Finally, even if you apply the workaround, the howto still doesn't work on Ubuntu 8.04. It may have something to do with libsane no longer providing /etc/udev/rules.d/45-libsane.rules. I don't know for sure though.

If anybody has any updated wisdom on these devices, please post it here!

Thanks :KS
James

---

