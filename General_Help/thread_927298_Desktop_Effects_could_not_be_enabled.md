---
title: "Desktop Effects could not be enabled"
date: 2008-09-22
forum: General Help
---

### Post by genros on 2008-09-22
:confused: I'm trying to get my Ubuntu 8.04 to show the "Cube" I've looked around the web and tried what they mentioned and nothing helps. One thing that I'm sure is a problem is how I get the message "Desktop effects could not be enabled". How can I enable it? I know my hardware is more than capable of doing this:

I have a nvidIa GeForce 9800, 4 GB RAM, Intel core 2 quad processor, and 2 500GB harddrives.

I have the "Advanced Desktop Effects Settings installed and the Cube is checked to work. However, nothing works. Not even the magnifier.

Also, my display resolution won't go higher than 800x600 which doesn't make sense.

How can I solve these two problems? :confused:

---

### Post by empty_spaces on 2008-09-23
Have you downloaded and enabled the NVIDIA "Restricted Drivers"?
If not, I would recommend that you use EnvyNG to install them

---

### Post by anotherdisciple on 2008-09-23
> **empty_spaces said:**
> Have you downloaded and enabled the NVIDIA "Restricted Drivers"?
If not, I would recommend that you use EnvyNG to install them

To do this, open a terminal (Applications > Accessories > Terminal) and enter:

```
sudo aptitude install envyng-gtk
```


After installing, it can be found in your Applications menu... not sure which sub-menu.

---

### Post by dxplosiv1 on 2008-09-23
I was going to suggest lowering you resolution to 1024 X 768. I had to do that to get mine working but I just saw that your only goes to 800 X 600. You could try downloading and running compiz-check. This should tell why compiz is not running like it should.

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by AibyoukaKyu on 2008-09-23
I just started toying with Ubuntu Hardy for the past few days, and my Nvidia 6200 was spazzing out, then finally started working but not fully. After dl'ing EnvyNG everything is in pristine condition, Desktop Effects are working and im a happy kitty :3  Thanx a ton![IMG]http://209.85.12.234/11293/78/emo/Neko_by_VikingHeart.gif[/IMG]

---

### Post by anotherdisciple on 2008-09-24
Good stuff! Can you mark this thread as solved please? Directions are in my signature.

---

### Post by genros on 2008-09-24
Awesome. My first problem is fixed. However, my second problem isn't. Now I can't even access my screen resolution. I would love to have it higher than 800x600. My monitor and graphics card can handle more than that.

---

### Post by loomsen on 2008-09-24
Hi.

I don't exactly know if nvidia-settings and nvidia-xconfig will work with your card, I have a 8600M GT, and it works.

Maybe try dropping to a terminal with Ctrl+Alt+F2, login and type:

/etc/init.d/gdm stop

to stop gnome and the X server, in case they are still running.

Then run:
sudo apt-get install nvidia-xconfig nvidia-settings

This should install these tools, which with you'll be able to reconfigure your X-Server automatically to use the nvidia-driver.

After installation completes just run:
sudo nvidia-xconfig

and after a confirmation about the xorg.conf being reconfigured and the old one backed up, type startx to start X again.

If you see a nvidia splash screen, you succeeded, and your card should be konfigurable through gnome too, by running nvidia-settings as root (Applications--system tools-->nvidia-settings)

You might have to change the launcher by prefixing a gksu to the command.
Easiest way, open up a terminal and do:

gksu nvidia-settings

that should be it.

Oh, and btw, you should decide for yourself which packagetool you want to use. It is not recommended to mix them up, so either use apt-get or aptitude, up to you, but you should choose one and keep it :) Just because I saw disciple uses aptitude.

*edit*
You might have to enable the non-free repos if you didnt so yet, tho I'm not sure about that cause I'm running debian...

---

