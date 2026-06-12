---
title: "removed old kernels with there modules !"
date: 2008-08-16
forum: Hardware
---

### Post by Khaled Khalil on 2008-08-16
hi there
i need some advice
the whole story began when i have removed some old kernels to reduce used space (my installation was initially back to edgy eft and upgraded till latest hardy heron kernel upgrade, so i had lot of them), then i hibernated (hibernate-disk), after waking up i noticed that wireless card cannot be loaded, even by restartin networking service (/etc/init.d/networking restart), so i rebooted
after reboot i found that the touchpad also doesn't get response, but i didn't gave it much interrest (at least untill i can connect to the internet) after some trials and fails with ifup and ifdown i tried to load the kernel modules by hand, (insmod rt61.ko) but it couldn't find the module, while trying to get information to recompile the driver i realized that even ethernet (eth0) doesn't work!
now the state is:
1- can't load the wireless card driver module
and even can't find the card itself by lspcmcia nor lspci (it works fine on an old windoz installation)
2- touoch pad doesn't work (it worked oyt of box from initial inistallation)
3- even wired ethernet doesn't work (needless to say it used to work under all conditions from its first day)
4- i don't know what else hardware i had configured or was auto detected during installation and doesn't work anymore!

is there any possibility to retrieve those kernel modules (i guess they were removed with the old kernels), may be there is some way to repaire system by cd, (i remember this was possible with mandriva 2005 before i switched to ubuntu)

if there is no way to restore my same system, i am looking for a lightweight distro that has exellent hardware detection (i can't no more spend lots of time trying to configure everything), which could be better fluxbuntu or linux mint flux or another distro ? (hardware detection is prefered over any other thing)
sorry, i know it is not the appropriate place for the last question, but mint is also one of ubuntu sons.

---

