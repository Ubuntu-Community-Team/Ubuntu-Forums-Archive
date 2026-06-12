---
title: "LXDE minimal install questions"
date: 2008-09-29
forum: General Help
---

### Post by briantm on 2008-09-29
I've just installed LXDE on a CLI install of Ubuntu for use with an LCD TV.

Everything is working fine but I can't figure out how to change the screen resolution.

When I try ```
sudo dpkg-reconfigure xserver-xorg
``` it just reconfigures the keyboard settings.

This may be because when I installed I was connected to the TV with a HDMI cable, but have since switched to a VGA cable do to an unsolvable overscan issue.

How do I change the res?



Also, when I try to launch synaptic from the panel nothing happens. I have to run "sudo synaptic" from the terminal. Is there something I can install that will prompt me for the password?

And finally, are there any other non-application packages you would recommend that I install that I will probably need in the future?

Thanks

Brian

---

### Post by dreadmeat on 2008-10-19
> **briantm said:**
> I've just installed LXDE on a CLI install of Ubuntu for use with an LCD TV.

Everything is working fine but I can't figure out how to change the screen resolution.

When I try ```
sudo dpkg-reconfigure xserver-xorg
``` it just reconfigures the keyboard settings.?
hey i get this too, acer travelmate 210TE [pos]
clean/fresh install pud/lxde from live disc.
"util-linux" error here too.

i found [**[COLOR="blue"]this[/COLOR]**]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=488311") just now, trying it as we speak, so to speak =p

---

### Post by dreadmeat on 2008-10-20
i grabbed > /etc/init.d/hwclock.shfrom another machine here and implanted it on the pud/lxde laptop and all is peachy...

---

