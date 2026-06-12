---
title: "Install on USB with vmware (without CD)"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by emeurant on 2009-11-01
For those like me who own a netbook without a cd player, you can install ubuntu quite easily and with no risk on a ssd card using Vmware player.

The idea is simple, you create a Virtual machine with no Hard drive, USB support and mount the ubuntu iso of you choice (successfully tested with ubuntu 9.04 and 9.10).

When you start this virtual machine, you can enabled the support for any usb device present on the host. So, in my case, I enable the SSD card of aspire one.

The VM boots on the CD and within the installation process, you only can see your ssd card (or USB key) as a possible drive to install onto. (This remove the risk of an installation on your main drive).


Once the installation is completed, reboot the vm when asked but do not let it restart. Close the VM player before.

You ssd is now created and installed with you best ubuntu.

Shut down your whole PC and you can now start on the ssd (via f12 for exemple on an AAO or <esc> on an eepc)

---

### Post by Dave33 on 2009-11-01
With unetbootin, you can do the same thing without any virtual machine.

You can download for win, or install with "sudo atp-get install unetbootin" or synaptic

win: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Just select iso, and choose your usb, memory card, or regular hard drive. Best from usb, you can test the live, and if is working, then you can install from it.

---

### Post by emeurant on 2009-11-01
your are right but unetbootin creates an installation source. Here I create an installation of the OS on the USB drive like if it were a hard drive install.

---

