---
title: "Neomagic sound hangs hotplug"
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by Heretic09 on 2005-12-08
I have a Dell Latitude CPi A366XT with a neomagic sound chip. Its detected fine but only boots 1 out of 6 tries, the rest hangs at the Hotplug script. After a bit of research i've found that the driver for neomagic is very buggy:

[http://http://www.alsa-project.org/alsa-doc/doc-php/template.php?module=nm256]("http://http://www.alsa-project.org/alsa-doc/doc-php/template.php?module=nm256")

The only useful information on making it work was the last post on the link above:

> Dell Latitude CPt 333GT with NM2360 chip, Neomagic 256ZX, works great
with ALSA 1.0.2 under SUSE 9.0.  Did enable snd_viao hack and ac97 force
options in Yast2 config of card.  Have booted from cold boot with no
problem.

Thank you!!

I have no idea what the snd_viao hack is or how to force ac97. Anyone with a neomagic sound chip have the same problem or know of a work around?

---

### Post by Heretic09 on 2005-12-08
Ok I found out a lot of info on this issue here: 

[https://bugzilla.ubuntu.com/show_bug.cgi?id=7939]("https://bugzilla.ubuntu.com/show_bug.cgi?id=7939")

Basically its a known issue, the fix has been put into one of the hoary kernel updates but for some reason is not in the breezy kernel (which i'm running). There is a patch available to fix this but before trying that i'll try some of the workarounds mentioned. Anyone with a neomagic 256 sound chip should look into it.

---

### Post by Sammy_Da_Cat on 2006-02-18
Thanks for th info! I am loading 5.10 Breezy on a ols Dell CPI. It did hang on the hotplug script on the first boot. After I rebooted it finaly went through! I will check out your links because I am sure this problem will come up again. Thanks alot!! \\:D/

---

