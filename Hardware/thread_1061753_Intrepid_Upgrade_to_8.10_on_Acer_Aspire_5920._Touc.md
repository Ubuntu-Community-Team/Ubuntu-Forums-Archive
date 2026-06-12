---
title: "Intrepid Upgrade to 8.10 on Acer Aspire 5920. Touchpad no longer works."
date: 2009-02-06
forum: Hardware
---

### Post by philbarr on 2009-02-06
Hi all,

I just upgraded from Hardy (8.04) to Intrepid (8.10), and now my touchpad won't work?! I tried replacing my xorg.conf with a previous version and that didn't help. After much googling, I realised that you have to configure HAL using the fdi files. I tried changing the settings in 11-x11-synaptics.fdi to what my xorg.conf says (using the xml syntax), and restarting, but still no luck.

What was wierd was that the mouse would work on the login screen, but not after having logged in. This makes me think that the system was using xorg.conf BEFORE login, and HAL after. Is that true?

Unfortunately, with all my messing around, the mouse no longer works before login either. I think if I'd copied the xorg.conf settings into 11-x11-synaptics.fdi when it was working before login then maybe I'd be ok.

Regenerating the xorg.conf via dpdk-reconfigure (or whatever that command is that it says in xorg.conf) gives me a very basic xorg.conf that doesn't work.

Is there any way to get xorg.conf regenerated properly, or to get HAL to properly identify my touchpad device?

Also, I ran: xinput list, and my "Synaptics Touchpad" was listed. So I tried: xinput set-pointer "Synaptics Touchpad", and got a Bad Device error. I'm thinking that either means my configuration is bad, or maybe when I upgraded, something happened to my touchpad device driver?

Thanks for any and all help!

Phil.

---

### Post by philbarr on 2009-02-06
I borrowed a usb mouse, plugged it in and it worked fine. then I went to System->Preferences->Mouse, went to the "touchpad" tab, and ticked "enable touchpad". now the touchpad works!

I don't get it (although I'm ecstatic my touchpad works). What's the equivalent of ticking "enable touchpad" on the command line?

Also, before I got hold of the usb mouse, I had managed to get my touchpad working before login again by restoring xorg.conf and 11-x11-synaptics.fdi to their original states. It was only AFTER login that it wouldn't work.

---

