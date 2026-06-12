---
title: "Gnome lost resolution settings after reboot (nVidia)"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by xeo_pt on 2007-07-18
Hi,
I have a nVidia and a Apple Cinema 22" and just install ubuntu 7.04 .

My problem is that after a reboot Gnome returns to to 800x600 and I have to run nVidia settings
to change to 1920x1200 mt working resolution.
Why does Gnome "forgets" the resolution settings?

Any help will be great.

Thanks in advance.

---

### Post by lawr_rawr on 2007-07-18
Someone else correct me if I am wrong, but I think the nvidia-settings application does not make permanent changes to your display because you are not running it as root.

I have noticed that if I adjust the color settings that way, they revert back after a restart. I have not yet tried gksudo nvidia-settings to start it as root.

You might want to adjust the resolution under System --> Preferences --> Screen resolution, or manually edit your Xorg.conf file.

---

### Post by xeo_pt on 2007-07-20
Thanks for your help.

I run nvidia-settings from sudo and it didn't work.
I save a xorg.conf file replace the file in etc/X11 and it works.

Thank.

---

### Post by bdtgp on 2007-07-20
Yeah you just need to save the file (sometimes manually) otherwise your xorg will revert back to the original.  good call.

---

