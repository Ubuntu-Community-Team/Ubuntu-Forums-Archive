---
title: "Laptop screen flickering."
date: 2016-10-15
forum: Hardware
---

### Post by diesel13 on 2016-10-15
Hi all,

I am trying to install Ubuntu 16.10 for my daughter on her new Acer E 17 E5-772-34HF Core i3-5005U Intel HD5500.

The screen is flickering all the time except when using the mouse (trackpad) or entering keystrokes.

I have tried adding a config file to xorg as per this...

[http://askubuntu.com/questions/766725/annoying-flickering-in-16-04-lts-chrome](http://askubuntu.com/questions/766725/annoying-flickering-in-16-04-lts-chrome) (I do realise this is titled 16.04).

I have also tried using the module options...

options i915.enable_psr=0
options i915 enable_rc6=0


I need to sort this as my daughter needs computer access for her new high school classes.

I have the same results using Arch (my personal desktop distro) on the laptop too.

Any help would be appreciated.

Diesel13.

EDIT: I have used i915.modeset=0 to make the system fallback to the vesa driver as a temporary measure.

---

### Post by oapa2 on 2016-10-18
Hi,

i had the same problem. 

found this solution on other forum:

[COLOR=#000000]open terminal[/COLOR]
[COLOR=#000000]sudo gedit /etc/default/grub[/COLOR]
[COLOR=#000000]edit line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash” [/COLOR]
[COLOR=#000000]add i915.enable_psr=0 in the quotes e,g.[/COLOR]
[COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.enable_psr=0”[/COLOR]
[COLOR=#000000]save[/COLOR]
[COLOR=#000000]sudo update-grub[/COLOR]
[COLOR=#000000]reboot

[/COLOR]

---

