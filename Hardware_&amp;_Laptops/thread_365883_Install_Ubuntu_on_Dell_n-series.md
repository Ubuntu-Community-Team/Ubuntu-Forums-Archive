---
title: "Install Ubuntu on Dell n-series"
date: 2007-02-20
forum: Hardware &amp; Laptops
---

### Post by daehenoc on 2007-02-20
Hi all,

I've been handed a n-series Dell desktop (i.e. only comes with FreeDOS), model DCNE, and asked to install Ubuntu on it. I've tried Dapper (6.06), Edgy (6.10) and Feisty (7.04 - build date 20070219).

Dapper, Edgy and Feisty all fail a couple of seconds after selecting the default install method with an error message similar to this:
[xxxx.xxxxxx] PCI: Cannot allocate resource region 1 of device 0000:00:14.0

Where the xx's seem to be a timer count. (On Edgy, this number is in the 17 millions.something).

Now with Feisty when I select 'Install a command-line system' the installer actually starts and has problems detecting the SATA drive or controller:
ata1: SATA link up 3.0 Gpbs (SStatus 123 SControl 300)
ata1.00: qc timeout (cmd 0xec)
ata1.00: failed to IDENTIFY (I/O error, err_mask=0x104)

These lines are repeated a few times during what I assume is a timeout of some sort (takes a few minutes) and the installer proceeds. Choose language and keyboard layout and the installer eventually reports "No disk drive was detected." and asks me to select a driver for the disk drive.

So I'm figuring that this doesn't look too good. I'm guessing that the kernel on Feisty hasn't got support for the SATA controller on the motherboard, what do you think? Does anyone have any suggestions on something that I can try to get around this problem? Or know of one of the disk drivers that will work with this hardware?

On top of that, does anyone know of a workaround for the first problem when trying to do a GUI install? Again I'm guessing that it's a kernel issue with this hardware.

Thanks,
Greg

---

### Post by daehenoc on 2007-02-22
As much as I love replying to my own posts, I've had some progress on this issue:

I bet the first problem is a video driver problem, this desktop has an ATI X300 integrated video card and I bet it's not supported by the GUI installer. Using a text-mode install gets the installation process started.

After a few searches, I found the following page:
[Installing Fedora on a Dell Optiplex 320 << wirelessness](http://wirelessness.wordpress.com/2007/02/07/installing-fedora-linux-on-a-dell-optiplex-320/)
This page tells me that the kernel boot option pci=nomsi will mean the HDD is recognized by the kernel, yay!

Once I get the system installed and X running, I'll post further information.

---

