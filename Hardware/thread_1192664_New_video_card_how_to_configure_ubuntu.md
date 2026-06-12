---
title: "New video card: how to configure ubuntu?"
date: 2009-06-20
forum: Hardware
---

### Post by tszanon on 2009-06-20
I've recently bought a new video card, and I'm currently using the onboard video card (both are NVidia's GeForce).

What must I do to configure ubuntu to use the new video card? I think I should run both
```
dpkg-reconfigure xserver-xorg
nvidia-settings
```
but I'm not sure if that's all.

---

### Post by 73ckn797 on 2009-06-20
System/Administration/Hardware Drivers gives no recommended driver to use?

---

### Post by tszanon on 2009-06-20
I still haven't installed it yet.

Before, I was using a 7600GT, but I had to take it out, so I switched back to the onboard video card. No driver was suggested, but I had to reconfigure the system for the card to work. But, after I did it, I had some problems, like system hangs (only REISUB worked).

I don't know if I did it correctly, due to the problems that I had.

So, now that I've got a new card, I wonder what's the correct way to configure the system to use another card. I thought that running dpkg-reconfigure and nvidia-settings would do it, but I'm not sure.

Maybe I'm lucky this time and a driver suggestion will come up when I turn it on. :)

Thanks!

---

### Post by markbuntu on 2009-06-21
Before you install that card remove completely any old nvidia drivers from you system. Install the new card and boot into recovery mode and use the fix x option. This will get you to the desktop with the generic VESA driver. Then you can install the nvivia driver.

Your system is hanging because the old nvidia driver is still installed. The nvidia drivers replace many important files in the X  server and these must be removed for other drivers to work properly.

---

### Post by tszanon on 2009-06-21
Last night I installed the card.
"Hardware drivers" informed me that the video driver was installed, but not active. I ran dpkg-reconfigure xserver-xorg, then nvidia-xconfig. After rebooting, everything was fine, until now at least :)

Everytime I ran skype, the system would hang a little later. It didn't happen, so it seems that the problems may be already solved.

Thanks for the instructions, I'll follow them next time (or if the system suddenly freezes :D)

---

### Post by bondmatt on 2009-06-21
What does everyone think of Envy (a package installed in synaptic used to automatically install and configure the 'best' driver)?

- MJB

---

### Post by 73ckn797 on 2009-06-22
> **bondmatt said:**
> What does everyone think of Envy (a package installed in synaptic used to automatically install and configure the 'best' driver)?

- MJB

You may want to start a new thread with this question.

---

