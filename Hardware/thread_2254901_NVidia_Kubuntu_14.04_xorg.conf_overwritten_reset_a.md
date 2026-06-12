---
title: "NVidia Kubuntu 14.04 xorg.conf overwritten reset after reboot"
date: 2014-11-30
forum: Hardware
---

### Post by FreeFog on 2014-11-30
Running Kubuntu 14.04 64bits.
  Followed tips on the launchpad:
  [https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1310489](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1310489)
  But xorg.conf keeps getting reset.
  It also seams that if I uninstall nvidia-311 and then try to patch to  the latest drivers on NVidia the OS does not seam to find them.
  Any guidance?
  Thanks for everything.

---

### Post by carlwsnyder on 2014-12-01
First, xorg.conf has been deprecated (not fully utilized) since about Kubuntu/Ubuntu 10.04.  Only if you have multiple monitors or you are using some of the keyboard or other hardware configuration functions of X does /etc/X11/xorg.conf even get read or created.

Second, did you use the **[COLOR=#333333][FONT=monospace]nogpumanager[/FONT][/COLOR]**[COLOR=#333333][FONT=monospace] kernel parameter on your GRUB menu selection or in /etc/default/grub at the line ending in "quiet splash"?  By that I mean did you interrupt GRUB and edit the line beginning **vmlinuz** to add the **nogpumanager** parameter immediately following the **quiet splash** parameters on that line, or did you edit the /etc/default/grub file to add the **nogpumanager** immediately following the "quiet splash" line so that it looks like this?[/FONT][/COLOR]```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nogpumanager"
```

If you did modify /etc/default/grub, did you then run **sudo update-grub** from a terminal, followed by **sudo grub-install /dev/sda**, changing the sda to whatever your boot disk is, before rebooting to check what changes occurred?

---

