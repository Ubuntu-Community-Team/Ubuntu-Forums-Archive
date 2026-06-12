---
title: "What is the best looking boot loader?"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by stev91 on 2009-08-09
I have grub and it works fine to choose between ubuntu and vista. However I am wondering if there is a way to have a boot loader that lets you choose between the two by clicking an icon. Or something a little bit more aesthetic.

---

### Post by stlsaint on 2009-08-09
check out startup manager thru system>administration>startupmanager...you can do some custom stuff there but as far as choosing icons instead of kernels im not too sure about that!! but ubuntu never ceases to amaze me!!!

---

### Post by phillw on 2009-08-09
I would doubt it. The reasoning being is that your 'pretty' icons are dependent on the Operating system you are running being able to 'talk' to the graphics device in your computer.

As, at the stage of choosing which OS you wish to run, you don't have one (Hence them being called boot loaders) - Thus, you will only have the text option.

If you install Ubuntu 'under' XP / Vista, etc.. you will boot to that O/S then be able to switch to Ubuntu - very nice icons :-\  - but, you will not be running pure Ubuntu and will also take a hit in terms of speed and some of the funtionallity.

So, dual boot may not too graphical, but it does give you a 'clean' start into whichever OS you then choose.

Hope that helps explain.

Regards,

Phill.

---

### Post by wojox on 2009-08-09
[http://www.erodov.com/forums/how-install-gfx-grub-ubuntu/4386.html](http://www.erodov.com/forums/how-install-gfx-grub-ubuntu/4386.html)

Check that link out.

---

### Post by stev91 on 2009-08-09
Thanks wojox that looks promising and all other replies thank you. When I tried to change the background I forgot to do it using root. So, the link helped.

---

### Post by tgalati4 on 2009-08-09
The newer kernels are "mode-setting", check out Fedora's bootup graphics.  This requires the kernel (or user) to correctly pick out the graphics card before booting.  Once the graphics card and mode is set, you can get fancy.

I imagine that GRUB will take advantage of these mode-setting features in the future.

I don't spend much time rebooting so a graphical GRUB is not exciting.  I just want something that works consistently.  And GRUB works fine the way it is.

---

