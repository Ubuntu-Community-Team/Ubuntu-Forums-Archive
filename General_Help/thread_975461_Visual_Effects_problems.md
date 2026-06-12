---
title: "Visual Effects problems"
date: 2008-11-08
forum: General Help
---

### Post by ToastyMallows on 2008-11-08
I'm new to Ubuntu and I finally have it installed on my computer, yay!

I have upgraded from 8.04 to 8.10 and I've been having problems with the visual effects.  I don't know if this is answered somewhere else on the forums, but when I click Normal or Extra effects, it says "Desktop Effects could not be enabled."

Is there any way around this?  A driver update or something?  I've tried **System>Administration>Hardware Drivers** but it says it can't find anything.  Using Sysinfo I found out that my Graphics Card is a VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)

Can anyone help?  I'd love to use the 3D effects.

ALSO: I'm starting to learn the terminal a little so if terminal commands will help the problem feel free to post them.

---

### Post by kennykng on 2008-11-10
I had a same prolem with you. That would be a pity if we could not use 3D effects on Ubuntu. I saw that before. Thats why I want to use Ubuntu.

---

### Post by xcorsary on 2008-11-10
if you made an upgrade via internet (without installatin cd/dvd), it can be that some packages are not well installed. 
Check your package manager (synaptic?) and look for damaged or corrupted packages. if you find them, install them again.

On the other hand, i recomend you to install directly from the cd. the configuration will be more solid and stable then.

good luck!

---

### Post by Daimoneze on 2008-11-10
I agree with xcorsary. You might also want to try searching your package manager for some of the keywords related to you video adapter (VIA, K8 etc.).

There is also a way to try reconfiguring your display settings. I **believe** this command is ```
dpkg-reconfigure -phigh xserver-xorg
```
This must be run as root and might take you through a few prompts. You should be OK with the defaults. Then restart X (ctrl+alt+backspace). Good luck!

---

### Post by ToastyMallows on 2008-11-12
> I agree with xcorsary. You might also want to try searching your package manager for some of the keywords related to you video adapter (VIA, K8 etc.).

There is also a way to try reconfiguring your display settings. I believe this command is
Code:

dpkg-reconfigure -phigh xserver-xorg

This must be run as root and might take you through a few prompts. You should be OK with the defaults. Then restart X (ctrl+alt+backspace). Good luck!

I tried this and got this error,

```
xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20081112213725
```

What does this mean?

I also ran Compiz-check and I found out that my driver for my graphics card is currently "vesa", which isn't capable of running compiz.  On a Synaptic package manager search of VIA I seem to have found my driver,

```
xserver-xorg-video-openchrome
```

Is there a way to make this driver work?

---

### Post by ToastyMallows on 2008-11-15
bump, still need help

---

### Post by eternalnewbee on 2008-11-16
Your graphic card most probably doesn't support 3D acceleration. I hate to bring you the bad news, but I have the same problem on another computer.
If you can afford it, buy a graphic card (check if you plan to buy one whether it's supported, here on the forums).

---

### Post by ToastyMallows on 2008-11-16
OK then no 3D Visual Effects but can I get it so it at least runs well on my computer?  I have a decent processor and I can't run the Matrix (code) screensaver without it being choppy and taking forever to run.

Any fix to this problem?

---

