---
title: "modprobe: WARNING: bad line.... PLEASE HELP!"
date: 2004-12-01
forum: Hardware &amp; Laptops
---

### Post by nrm8d1 on 2004-12-01
I have a fresh install of Ubuntu 4.10 and was enjoying it very much until I broke it. I installed ltmodem drivers for my lucent winmodem, got them working well, then installed NVIDIA drivers from NVIDIA's script installer (didn't realize there was a deb for them, plus I already had the installer handy). Both devices worked flawlessly until I rebooted. Now, on reboot, as soon as it loads modules it gives me error messages:

modprobe: WARNING: /etc/modprobe.conf line 16: ignoring bad line starting with 'keep'

modprobe: WARNING: /etc/modprobe.conf line 25: ignoring bad line starting with 'post_install'

modprobe: WARNING: /etc/modprobe.conf line 26: ignoring bad line starting with 'post_remove'

modprobe: WARNING: /etc/modprobe.conf line 76: ignoring bad line starting with 'above'

and it just keeps repeating them until it finally boots. However, once it does boot X doesn't start because the nvidia module isn't loading. I can reinstall the nvidia driver and it will work, but I shouldn't have to do that.

Also after reboot, I can't get the ltmodem modules to work at all. When I go through the same process I did in the first place, it won't allow me to insert the modules, and spits out those error messages.

Commenting out the "bad" lines doesn't help either, and update-modules just puts those lines back in.

I'm very close to giving up and reinstalling, but I'm afraid I'll just run into the same problem again.

Thanks,
nrm8d1

---

### Post by wallijonn on 2004-12-01
do you have a backup copy of [COLOR=DarkGreen]/etc/modules.conf[/COLOR] ?

I would start by looking at that file for clues.

---

