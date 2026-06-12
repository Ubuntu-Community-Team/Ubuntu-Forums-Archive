---
title: "Problems after X.Org update"
date: 2011-01-25
forum: Hardware
---

### Post by DrazenZG on 2011-01-25
Hi everyone!

I have one HP NX4710s (with HD 4330 card) laptop and I need to use ATI proprietary drivers for it's graphics card (if i don't vent turns like crazy, laptop heats up). I downloaded and installed those drivers manually.

Problem is: each time after some X.Org update comes and I install it, my computer won't boot to Ubuntu GUI. I can go to recovery and start it with failsafe graphics. 

I found solution (on this great forum :D): remove fglrx drivers from withing shell (/usr/share/ati/fglrx-uninstall.sh) after which Ubuntu starts normally. 
But, after that I installed those same drivers from ATI as before, restarted computer and everything worked again great as before.
So basically, every time after X.Org update I have to uninstall and then again install ATI drivers :D

Today was the second time this happened to me and I would really like to know why. Firste time was some 2-3 (or 4) weeks ago.
Should I just avoid X.Org updates?
Is there a reason that my laptop need those proprietary drivers so it doesn't heat up?
Is this common thing to happen? 
Is there ANY way for me to move away from those proprietary drivers?

I hope I haven't complicated this too much :D.

---

### Post by slooksterpsv on 2011-01-25
A few questions:

What version of Ubuntu are you running? And is it 32-bit or 64-bit?

You said it was a 4330, are you installing the fglrx (I assume so, but still better to ask) via Hardware Drivers in Settings -> Administration?

After you install the drivers, have you ran, in a terminal:
```

sudo aticonfig --initial -f

```

If you could answer those, that would be great.

---

### Post by DrazenZG on 2011-01-25
It's 64bit version of Ubuntu. 

I didn't install driver via Hardware drivers, I downloaded it from ATI's web page and installed it manually (package comes with Catalyst Control Centre, graphics driver and kernel module) :). I did that because I had same problems with heating when I installed drivers from within Hardware Drivers. And yes, I know that this whole story sounds strange.

Today I forgot to do that but I think I've done that before. When I typed that in now i got "Saving back-up to /etc/X11/xorg.conf.fglrx-5" so there are 4 backups already :D.

It's not problem for me to install those drivers each but time but I'm afraid that there are some users who won't know how to solve it. It's pretty uncomfortable when you can't get in your OS :D.

---

### Post by DrazenZG on 2011-01-27
Any ideas? ([COLOR=Red]Bump[/COLOR])

---

