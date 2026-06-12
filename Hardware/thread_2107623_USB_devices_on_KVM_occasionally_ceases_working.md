---
title: "USB devices on KVM occasionally ceases working"
date: 2013-01-22
forum: Hardware
---

### Post by RAMChYLD on 2013-01-22
Hi, I'm having some problems with USB on Ubuntu Quantal. I have a USB mouse and keyboard, touchscreen and gamepad connected through a USB+DVI+audio KVM. Occasionally, the USB mouse would cease functioning until the machine is restarted, but the USB keyboard will still work fine. Switching to a console and running dmesg reports a barrage of *hub_port_status failed (err = -110)* messages. There are no preceding errors indicating why this happens, it just happens and at random times. Resetting the KVM also renders the keyboard inactive then and the only way to get the machine to work properly again then is to use the reset button. The way I handle the issue so far is to get to a console and run the reboot command as soon as the mouse ceases working.

The KVM shares the devices between the Ubuntu box, two Wintel boxes and a Mac. Of all 4 devices, only the Ubuntu box exhibits this issue. 

The box in question has an NVidia NForce 750a SLI motherboard with a pair of matching NVidia GTX260s in SLI configuration. The KVM is an Aten CS-1764. Truthfully, this error happens on all Linux distros run on the box, not just Ubuntu. However, it happens less frequently on Ubuntu than it does on OpenSuSE which I was previously running. However, the issue does not occur in Windows or Mac OS.

I have already tried using different keyboards and mice combos- the same thing happens.

What exactly does error -110 mean? And more importantly, is there any way I can clear the error without restarting the entire box? Or set a watchdog to fix the error for me everytime it happens?

Please help!

---

### Post by RAMChYLD on 2013-01-23
Just noticed something else in dmesg. 

This time when the mouse ceases working, there is the error "Still 7 active urbs in ep #73".

---

### Post by RAMChYLD on 2013-01-24
Ok, this time I have my keyboard and mouse connected direct to the linux box, and the freeze up still happens. This has led me to believe it may be a bug in the USB stack.

---

### Post by paraviz on 2013-04-21
Hey there RAMChYLD ...

I know your post is from a few months ago, but I'm dealing with a similar issue, error "-110".  It seems that I can connect my USB devices for a short period of time (maybe up to about 6 hours) when they either time out and get disconnected, or the USB device actually locks up the whole VM entirely, forcing a "destroy" scenario to restart my virtual machines.

Also, I am running my VMs on a Apple Mac mini server as the host.

In one situation regarding a USB2 disk, the entire VM froze up when I tried partitioning and formatting.

I have tried using a more recent version of QEmu/KVM, v1.2.0 compiled from scratch, which is not included in 12.10, to no avail.  Now, I'm actually thinking about trying the most recent version of [libusbx]("http://libusbx.org") to see if maybe that works any better.

The biggest issue I've been dealing with is that there seems to be absolutely *no* legitimate organization or authority to the USB stack in recent years.  I have spoken with Hans de Goede, who is either a creator or lead manager in the libusbx project (fork of libusb), regarding other USB issues, and he is a great help.  I know they are attempting (maybe already successfully) to revive a proper libusb, but that's all I know.

As far as the USB devices in the Ubuntu host are concerned, no issues exist unless I am working in a virtual machine.

If you find any solution, please post.  I will do the same.  Thanks!
~Laz

---

### Post by RAMChYLD on 2014-01-05
Well, After so many years with the problem and almost one year after posting, I finally figured out the problem, I think.

This board has a bad MSI implementation, but that's only half of it.

I reinstalled Ubuntu 13.10 again. Tried various suggestions, including:
- pci=nomsi only: First time try. No difference, but upon inspection the kernel now does a dump whenever the NVidia drivers are loaded
- Disabling Tri-state Mem in the BIOS = not a good move, it causes one of the CPU cores to randomly lock up
- clocksource=acpi_pm + pci=use_crs = no difference. In fact, the problem seems to spread to the previously working PS/2 keyboard and mouse after this
- hpet=disable (did this because previously I had an issue where my SBLive! card would cause hang on boot with hpet enabled) no difference

I tried rolling back to Nouveau for a while because with Nouveau running, the system never loses USB connection no matter how long the system was used. But Nouveau is not a permanent solution for me because I need SLI support. Then I read that Nouveau does not use MSI by default. So I began to research and I found out that NVidia drivers have been using MSI. But didn't I already disable MSI? Was the kernel panic the driver's way of re-enabling it?

Then I figured out that I could try adding the following line to /etc/modprobe.d/nvidia-graphics-drivers.conf
options nvidia NVreg_EnableMSI=0 

in addition to adding pci=nomsi in grub

I think that was the sweet spot. No kernel panic on boot, and the mouse remained responsive from boot even til now when it would have normally stopped working hours ago.

However, the nvidia-graphics-drivers.conf file warns that I should never touch it by hand for it will be overwritten with each driver upgrade.

Btw, currently I'm using the experimental 319 drivers. The 304 drivers have a nasty bug which caused SLI to be broken if the onboard third GPU is left enabled for whatever reason, that problem was fixed in the 310 drivers. 

So yeah. pci=nomsi in /etc/default/grub + options nvidia NVreg_EnableMSI=0 in nvidia-graphics-drivers.conf seems to be the magic combo for me.

PS: I also added pcie_aspm=force to grub to work around another bug in the chipset (the motherboard refuses to release aspm to the kernel). Also, added nomodeset to grub and blacklisted vesa as well just to be sure since the nvidia kernel module did put out an instability warning about it.

---

