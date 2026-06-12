---
title: "Again the 8800GT driver"
date: 2008-08-19
forum: General Help
---

### Post by jo4 on 2008-08-19
The problem
I installed Ubuntu 8.04 (with a alt. install cd) and upgraded and then selected the proprietary nvidia driver, installed and rebooted. It all goes well until gdm starts, then everything is black. Unable to get a terminal. No response on ctrl+alt+delete. Just completely dead.

I've read a bit about this on the forum, but it's apparent that the driver is the problem. What i don't understand is how it can be SO dead.

So of what i understand i have to append "DISABLED_MODULES="nv"" in /etc/default/linux-restricted-modules-common. So i'll do this and then get the proprietary driver?

What i don't understand is what the difference really is. Will the driver still be loaded or can i scrap my plans with Compiz and the like?

---

### Post by p_motch on 2008-08-31
jo4, I'm experiencing the exact same issue as you. I'm able to use the 8800gt without the nvidia drivers, but when I turn it on (either through enabling nvidia restricted drivers through Ubuntu, or by manually installing the nvidia drivers) I get the same problem you're having.

I've also tried the remedy of removing the splash screen in grub. No luck there either.

I'm stuck too.

---

### Post by fooman on 2008-08-31
i use an 8800gt with no problems.  i have installed using envyng (recommended) or the manual way (drivers from nvidia's site)....both work well for me.

envyng is in the repo's, so you can use synaptic. ...or install from the terminal;  for ubuntu use:

```
sudo apt-get install envyng-gtk
```

for kubuntu use:

```
sudo apt-get install envyng-qt
```

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

