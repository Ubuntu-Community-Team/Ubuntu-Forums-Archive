---
title: "Sound: modprobe and esd problem"
date: 2005-05-03
forum: Hardware &amp; Laptops
---

### Post by Campitor on 2005-05-03
Hello:

  I finally got sound working by including the snd_sb16 module.  I have a soundblaster live card, and works fine with this module.  but everytime I reboot, sound goes away...I always have to type this in a console:

>sudo modprobe snd_sb16
>esd -d hw:0 &

and then sound works again.  Does anybody know what I can tweak to avoid doing this everytime I restart?

Camp

---

### Post by ludi on 2005-05-03
[QUOTE=Campitor]Hello:

  I finally got sound working by including the snd_sb16 module.  I have a soundblaster live card, and works fine with this module.  but everytime I reboot, sound goes away...I always have to type this in a console:

>sudo modprobe snd_sb16
>esd -d hw:0 &

and then sound works again.  Does anybody know what I can tweak to avoid doing this everytime I restart?

Camp[/QUOTE]

[http://www.ubuntuforums.org/showthread.php?t=21211](http://www.ubuntuforums.org/showthread.php?t=21211)
Much more in [http://www.alsa-project.org/alsa-doc](http://www.alsa-project.org/alsa-doc)

---

