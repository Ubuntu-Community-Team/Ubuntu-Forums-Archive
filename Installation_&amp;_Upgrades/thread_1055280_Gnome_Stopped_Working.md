---
title: "Gnome Stopped Working"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by Chuchaqui on 2009-01-30
Hello,

I was working on my computer, and like usual it said I have some updates to install. I installed them, everything seemed normal. It said I needed to reboot so I did. After I rebooted, everything would load normally accept Gnome Display Monitor. If I were to hit alt+f1, alt+f2, ... I would get a terminal to login as normal, where I would be able to see my home folder and everything. However whenever I would go the the Gnome, it would just be a black screen with a '_' flashing. I can type things, but no commands do anything.

I tried going into one of the other windows with a terminal and used apt-get, but there were no broken packages. I tried reinstalling gnome and gnome-dektop*, both reinstalled, but it didn't fix my problem.

Thank you :)

---

### Post by em4r1z on 2009-01-30
You installed a new kernel that causes a problem with the X server, most likely due to your video drivers. Restart, press ESC when GRUB loads and choose the previous kernel.
Don't use the latest kernel until this errors are corrected. Visit the forums and you'll see many people with the same problem. In may case, the updates created a fatal kernel panic and I needed to reinstall. I hope you have better luck.

---

### Post by Chuchaqui on 2009-02-02
Thanks. I have a seperate home partition so I just reinstalled. Thanks though.

---

