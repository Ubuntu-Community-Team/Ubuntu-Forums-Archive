---
title: "Installing HP Laserjet P1102W"
date: 2011-12-29
forum: Hardware
---

### Post by grandsatrap on 2011-12-29
Hi, just finished installing this printer after hours of struggle. I thought I'd quickly give advice to others.

I am installing on **Ubuntu 10.04.3 Lucid Lynx**

** You'll have to download hplip. The version I had was not the most recent and didn't support the printer. "sudo apt-get install hplip" said that I already had the most recent version so I had to download the version I needed. Thess HPLIP page is very helpful

[http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)
[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)
[http://hplipopensource.com/hplip-web/install/manual/hp_setup.html](http://hplipopensource.com/hplip-web/install/manual/hp_setup.html)

Next was trying to install it. It needs a proprietary driver which you get by typing in "hp-plugin". This kept dying on me, giving me "eval: 1: ./hplip-plugin-install: Permission denied"  The reason was that I had set /tmp as a RAM drive (in /etc/fstab)
/tmp tmpfs defaults,nosuid,nodev,noexec 0 0

See these webpages.
[http://forumubuntusoftware.info/viewtopic.php?f=71&t=5501&sid=4782b280ef5b25fc49851fb0738763a5&start=10](http://forumubuntusoftware.info/viewtopic.php?f=71&t=5501&sid=4782b280ef5b25fc49851fb0738763a5&start=10)
[http://debian-facile.org/forum/viewtopic.php?id=3358](http://debian-facile.org/forum/viewtopic.php?id=3358)

I fixed the /tmp problem (no longer tried to mount it in RAM) and re-ran "hp-plugin".

It works!!

Other useful things are hp-setup. Or look at all of the "hp-" stuff by typing "hp-<TAB><TAB>" at the commandline.  

One other cool thing, CUPS is installed somehow and you can do all sorts of things by browsing to "http://localhost:631"

---

### Post by grandsatrap on 2011-12-29
Darn! I forget how to set this thread to SOLVED !!

---

### Post by jeiw on 2012-06-12
hi! I just read your thread and I'm actually having loooong struggles with my printer (the same as  yours, HP LaserJet P1102w). I think I probably have the same error, but I didn't understand how to fix it.. what should I exactly type in the console?
Thank you.. :)

jeiw

---

