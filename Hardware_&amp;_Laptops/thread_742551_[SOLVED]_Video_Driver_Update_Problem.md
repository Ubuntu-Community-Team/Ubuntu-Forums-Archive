---
title: "[SOLVED] Video Driver Update Problem"
date: 2008-04-01
forum: Hardware &amp; Laptops
---

### Post by ldarkwarriorl on 2008-04-01
Hey, i'm a super noob when it comes to linux and I ran into a problem but i do not want to have to reinstall ubuntu, so heres what happened.

I was playing around with settings and programs (learning how things work) and i opened the System>Administration>Hardware Drivers and noticed a video driver or update that was uninstalled.  So with the mindset that all updates are good I checked the box to install it and restarted my machine.  Now i dont get any visual when i boot up Ubuntu except for the loading screen.

Can someone please help me undo this problem?  Is there maybe a "Safe Mode" I can boot into to make it easy?

btw, I'm running 8.04 Beta,
thanks

---

### Post by overdrank on 2008-04-01
> **ldarkwarriorl said:**
> Hey, i'm a super noob when it comes to linux and I ran into a problem but i do not want to have to reinstall ubuntu, so heres what happened.

I was playing around with settings and programs (learning how things work) and i opened the System>Administration>Hardware Drivers and noticed a video driver or update that was uninstalled.  So with the mindset that all updates are good I checked the box to install it and restarted my machine.  Now i dont get any visual when i boot up Ubuntu except for the loading screen.

Can someone please help me undo this problem?  Is there maybe a "Safe Mode" I can boot into to make it easy?

btw, I'm running 8.04 Beta,
thanks

HI and you can try and boot into recovery mode which is usually the second choice in the grub. Then reconfigure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Then use the command ```
reboot
``` hopefully this will get you to a GUI, Desktop. Good luck.

---

### Post by ldarkwarriorl on 2008-04-02
I already recovered it.  But i'm definitley going to email this topic to myself in case i ever find myself in a similar situation.  Thank you.

---

