---
title: "&quot;Ubuntu is running in low-graphics mode&quot; right after udate... (SunFire X2200)"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by k3Rn on 2009-10-24
Hi,

I installed Ubuntu 9.04 on a SunFire X2200.

Right after the installation everything worked correcty.
I then updated the system, and since then on bootup i get the error: 
> "Ubuntu is running in low-graphics mode.
Your screen, graphics cards, and input device settings could not be detected correctly. You will need to configure yourself."I searched the forums but still have no real clue about how to fix it.

Any help appreciated!

  Markus

---

### Post by pgngp on 2009-10-26
I was having the same problem today. I had installed the new Ubuntu (version 8.04) updates and when I restarted my machine, I got "Ubuntu is running in low-graphics mode".

After trying several things, I reinstalled the NVIDIA graphics card driver, and that did the trick!

Here are the steps I used to fix the problem:
1. Switch to the terminal mode by pressing CTRL-ALT-F1
2. Login
3. Stop the X server: $ sudo /etc/init.d/gdm stop
4. Locate the NVIDIA driver setup file and run it:
$ sudo sh NVIDIA-Linux-x86-180.22.pkg1.run
5. Follow the prompts (you mostly need to select 'yes')
6. Make sure that in /etc/default/linux-restricted-modules-common, DISABLED_MODULES="nv"
7. reboot: $ sudo reboot

Hope this fixes your problem as well.

---

