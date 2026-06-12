---
title: "Dual boot problem: Grub doesn't display menu, can't access Vista."
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by personalmg on 2009-11-03
Hello there, I have a problem with my new installation of Ubuntu. I have Ubuntu and Vista dual-booted in my laptop which was working before I upgraded. Recently, Ubuntu updated my Jaunty Jackalope into Karmic Koala. But then I had driver problems with my WLAN adapter so I decided to re-install my Ubuntu partition. I have successfully installed Karmic Koala but then whenever I boot my laptop, I do not see a list of operating systems that I can choose. It just directly boots into Ubuntu and I can't access my Vista partition anymore.

I have been looking around for workarounds for this one but then they don't seem to work. Not to mention it looks like the guides around are outdated and won't work with the new grub that is bundled with Karmic Koala.

Could anyone help me? I can't access my vista partition for some reasons I don't know and I have plenty of files there to back-up. I just can't format my Vista partition :\

---

### Post by Torquemada28 on 2009-11-03
> **personalmg said:**
> Hello there, I have a problem with my new installation of Ubuntu. I have Ubuntu and Vista dual-booted in my laptop which was working before I upgraded. Recently, Ubuntu updated my Jaunty Jackalope into Karmic Koala. But then I had driver problems with my WLAN adapter so I decided to re-install my Ubuntu partition. I have successfully installed Karmic Koala but then whenever I boot my laptop, I do not see a list of operating systems that I can choose. It just directly boots into Ubuntu and I can't access my Vista partition anymore.

I have been looking around for workarounds for this one but then they don't seem to work. Not to mention it looks like the guides around are outdated and won't work with the new grub that is bundled with Karmic Koala.

Could anyone help me? I can't access my vista partition for some reasons I don't know and I have plenty of files there to back-up. I just can't format my Vista partition :\

There seems to be a common problem with dual-booting 9.10 with Vista/Win7. I'm having the same issue, as are many others.
Your best option might be to try to overwrite GRUB2 with the Vista bootloader.

Have a read [HERE]("http://ubuntuforums.org/showthread.php?t=1311693&page=2"). It's written for Win7 but Vista is probably similar.

---

### Post by sliketymo on 2009-11-03
Check this out:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

