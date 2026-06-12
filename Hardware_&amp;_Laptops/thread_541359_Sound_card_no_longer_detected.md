---
title: "Sound card no longer detected"
date: 2007-09-02
forum: Hardware &amp; Laptops
---

### Post by Scooter7 on 2007-09-02
Hi, I was trying a bunch of solutions to fix my problem of sound only working for one app a time, and tried this:

[http://ubuntuforums.org/showthread.php?t=8882&highlight=hear+multiple+sound&page=2](http://ubuntuforums.org/showthread.php?t=8882&highlight=hear+multiple+sound&page=2)

After rebooting, I had no sound, and in System -> Preferences -> Sound, my sound card is no longer listed:

[img]http://shadowserve.ath.cx/stuff/images/Screenshot-Sound Preferences.png[/img]

If I click on the volume control,l get this message:

[IMG]http://shadowserve.ath.cx/stuff/images/Screenshot-mixer_applet2.png[/IMG]

If I close that and click again, I get this:

[IMG]http://shadowserve.ath.cx/stuff/images/Screenshot-gnome-volume-control.png[/IMG]

I've tried restoring the backup I made of /etc/asound.conf, as well as deleting the /etc/esound/esd.conf file I created.

This didn't work, so now I'm stuck sitting here without sound.   I haven't tried it in Windows, but I doubt I'd have trouble with it there - as far as I can tell, this is a Linux-specific problem.

Just before rebooting, I had installed some updates - I have no idea if they're part of the problem, but they might be.

---

### Post by Scooter7 on 2007-09-03
*bump*

---

### Post by Scooter7 on 2007-09-20
Sorry for the double-post and bump.

I've been looking around, and realized the guide I followed was intended for Hoary users.

As such, I have a feeling that my system's now misconfigured, but I have no idea how to configure it back the way I need it.

I tried reinstalling the alsa drivers, but this didn't work.

I also tried this command in the terminal, to see the output:

```
aplay -l
```

This is the output:

> aplay: device_list:204: no soundcards found...

My sound card works perfectly in Windows.   So I know now that this is not a hardware issue.

If anyone can help, please do!   I don't want to have to resort to a reinstall of Ubuntu.

---

