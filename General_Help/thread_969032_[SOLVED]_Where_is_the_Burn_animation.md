---
title: "[SOLVED] Where is the Burn animation?"
date: 2008-11-03
forum: General Help
---

### Post by GumpTron on 2008-11-03
Hello,

I installed the new Ubuntu and I can't seem to find the burn animation option. Is it no longer available?

---

### Post by Fass on 2008-11-03
Are you talking about the compiz animation? Have you installed ccsm? If not, run:

```
sudo aptitude install compizconfig-settings-manager
```

The run it by selecting it in Applications -> System -> Settings. There in the animation settings, you'll find the burn animation.

You may need to install the package "compiz-fusion-plugins-extra" and "compiz-fusion-plugins-unsupported".

---

### Post by GumpTron on 2008-11-03
> **Fass said:**
> Are you talking about the compiz animation? Have you installed ccsm? If not, run:

```
sudo aptitude install compizconfig-settings-manager
```

The run it by selecting it in Applications -> System -> Settings. There in the animation settings, you'll find the burn animation.

i did that but still i am missing that animation and i think some others.

---

### Post by tuxxy on 2008-11-03
Open ccsm > effects > animations

the burn effect should be listed here with all the others ready for you to use as animations for close/open/minimize/maximize actions.

If you mean the burn effect for writing fire on screen thats located at 

Open ccsm > effects > paint fire

---

### Post by Fass on 2008-11-03
> **GumpTron said:**
> i did that but still i am missing that animation and i think some others.

*You may need to install the package "compiz-fusion-plugins-extra" and "compiz-fusion-plugins-unsupported".*

If that doesn't get you the burn animation, then... I guess it's no longer there.

---

### Post by GumpTron on 2008-11-03
i have take all the steps above and I am now convinced that some of the animations have been removed from Ubuntu by the developers.

---

### Post by JudFromHud on 2008-11-03
I don't have it either! Is there an effects package that needs to be installed?

---

### Post by JudFromHud on 2008-11-03
Got it!  

Open ccsm and goto preferences > plugin list
Uncheck automatic plugin sorting and enable animation addon.

For some reason all of the check marks in the main plugins window are now greyed out but you can still modify settings.

---

### Post by tuxxy on 2008-11-03
Its definitely still there :)

---

### Post by GumpTron on 2008-11-03
> **JudFromHud said:**
> Got it!  

Open ccsm and goto preferences > plugin list
Uncheck automatic plugin sorting and enable animation addon.

For some reason all of the check marks in the main plugins window are now greyed out but you can still modify settings.

PERFECT! thank you so much.

---

### Post by Shmalignant on 2008-11-03
Woot!  Everything's gettin' back to normal.

---

### Post by mockdeep on 2008-11-09
It got the Burn effect to return, but the settings for it don't show up in the CCSM.  Is there a different plugin that has to be enabled to allow you to change colors and burn rate?

---

### Post by GumpTron on 2008-11-09
> **JudFromHud said:**
> Got it!  

Open ccsm and goto preferences > plugin list
Uncheck automatic plugin sorting and enable animation addon.

For some reason all of the check marks in the main plugins window are now greyed out but you can still modify settings.

that should do it, worked for me.

---

### Post by mockdeep on 2008-11-10
Nope, I can set the animation to the different window actions, but it doesn't show up under the "Effect Settings" tab so that I can change colors and such.  Any ideas?

---

### Post by Boss_scout on 2008-11-14
try this link a great tutorial on setting effects including animation

[http://linuxowns.wordpress.com/2008/...look-and-feel/](http://linuxowns.wordpress.com/2008/...look-and-feel/)

---

### Post by ellalan on 2008-11-14
> **mockdeep said:**
> Nope, I can set the animation to the different window actions, but it doesn't show up under the "Effect Settings" tab so that I can change colors and such.  Any ideas?
Its under Animations-Addon.

---

### Post by mockdeep on 2008-11-15
> **ellalan said:**
> Its under Animations-Addon.

I see.  Don't know how I missed that one.  Thanks!

---

### Post by Cyb3rPrince on 2011-09-05
what i was looking for this! im tired all the time...i got it that its work :D

thanks you so much <3

---

### Post by GumpTron on 2011-09-05
wooohooooooo! :guitar:

---

