---
title: "Problems with Nvidia drivers"
date: 2008-11-09
forum: General Help
---

### Post by 7hunderstruck on 2008-11-09
I had a dual-monitor setup with my Nvidia 7300LE in 8.04.  After switching to 8.10, upon startup I get the message that my graphics card is not correctly configured, and it gives me the option to just use the "Safe" graphics mode.  Before giving me the option, I get this message:

"Failed to initialize the NVIDIA kernel module"

So after booting with safe graphics, I try "nvidia-settings".  With that, I get a message that says something like:

"You are not using X-config, just run 'sudo nvidia-xconfig'" and retry.

Now to be clear, I already have a copy of my xorg.conf in the correct directory.  I do this anyway, and I just get the same errors.

As far as the driver situation goes, if I go to "Hardware drivers", it says "You are not using any proprietary drivers", and the list appears empty.  Usually the Nvidia drivers should at least be listed, and I don't know what to do about this problem.

---

### Post by Tamlynmac on 2008-11-09
You may wish to use this driver:

[http://albertomilone.com/wordpress/?p=294](http://albertomilone.com/wordpress/?p=294)

---

### Post by 7hunderstruck on 2008-11-09
> **Tamlynmac said:**
> You may wish to use this driver:

[http://albertomilone.com/wordpress/?p=294](http://albertomilone.com/wordpress/?p=294)

Thanks, but I think the problem goes deeper than which driver I'm using... the same drivers worked in 8.04 for my card.  I've tried both the 173 and 177 drivers, and I get exactly the same errors.

---

### Post by 7hunderstruck on 2008-11-10
bump?

---

### Post by 7hunderstruck on 2008-11-12
Please help, I can't find anything that works anywhere.

---

