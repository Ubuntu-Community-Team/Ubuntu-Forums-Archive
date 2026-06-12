---
title: "Nvidiaaaaaaaa"
date: 2010-07-10
forum: Hardware
---

### Post by Ozzy-UK on 2010-07-10
Hey all, I have already posted something about this here in this forum but I just wanted to illustrate what the problem really is by uploading some pics.

I'm a Windows user dying to learn Linux, everybody recommended Ubuntu but seriously this is getting old already.

I have an nvidia GeForce 7150M / nForce630M and Ubuntu doesn't seem to recognize it from the very start of the installation process, so that means I can't even install it to further fix it because I can't see anything as shown in the pictures attached here.

I have read about the nouveau drives but really, if I can't even install ubuntu how am I supposed to fix it? Anyway, hope someone will be able to guide me. Thanks y'all for your help.

---

### Post by Ozzy-UK on 2010-07-10
Anybody please?

---

### Post by oldfred on 2010-07-10
I have a newer nvidia and it went to sleep as it started to load.

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
I edited my grub.cfg as I use grub to boot ISO, in syslinux.cfg or text.cfg
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf
Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by AltomineUK on 2010-07-10
I have heard of numerous complaints regarding the performance of the 7000 series of NVidia..... although most of them were related the 64-bit versions. Are you using such a version or the 32 bit edition?

---

