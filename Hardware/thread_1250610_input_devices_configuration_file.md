---
title: "input devices configuration file"
date: 2009-08-26
forum: Hardware
---

### Post by grackleman on 2009-08-26
Hi
Where is the input devices configuration in 9.04 since it is no longer in xorg.conf?
Thanks

---

### Post by tommcd on 2009-08-27
The X server automatically detects input devices, so very little or no xorg.conf is required these days. You can still create an xorg.conf file with the options you want, or edit an existing xorg.conf. The X server should still (hopefully) honor them.

Other hardware, like usb drives, cdrom drives, network cards, etc, are configured by hal and udev. See the file: /etc/udev/rules.d/README and the rules files in /lib/udev/rules.d/ for more info.

---

### Post by Yellow Pasque on 2009-08-27
You need to to direct X to use your configuration options in xorg.conf, or it will just ignore them and use HAL and evdev drivers anyway.
[http://wiki.archlinux.org/index.php/Xorg_input_hotplugging#I_don.27t_want_this_crap.2C_how_do_I_turn_it_off.3F](http://wiki.archlinux.org/index.php/Xorg_input_hotplugging#I_don.27t_want_this_crap.2C_how_do_I_turn_it_off.3F)

---

