---
title: "Firefox strange behavior"
date: 2008-08-31
forum: General Help
---

### Post by lovinglinux on 2008-08-31
Every time I start Firefox with compiz enabled using Glide 1 effect, it will show this weird behavior below, until it is fully maximized.

[[IMG]http://img507.imageshack.us/img507/3197/screenshotdesktopoggug1.th.png[/IMG]](http://img507.imageshack.us/my.php?image=screenshotdesktopoggug1.png)

I use FastDial extension, with a wallpaper, which is the distorted image displayed in this screen shot. You can see the wallpaper below:

[[IMG]http://img172.imageshack.us/img172/8916/2186099966b07e779d34bpp0.th.jpg[/IMG]](http://img172.imageshack.us/my.php?image=2186099966b07e779d34bpp0.jpg)

Any ideas what could be the culprit?

---

### Post by diwas on 2008-08-31
What is ur grafics memory?

---

### Post by lovinglinux on 2008-08-31
> **diwas said:**
> What is ur grafics memory?

256M

I have nVidia 7300GT

---

### Post by diwas on 2008-08-31
Press ALT+F2 then type firefox.

And tell if the behavior repeats.

---

### Post by lovinglinux on 2008-08-31
Yes it repeats.

I tried disabling all extensions and the result is the same. What I notice is that after a few hours using the machine, Firefox takes longer to initialize. Nothing drastic, but like a second slower. That is when the effect is more noticeable. Now that I just started the machine, the effect is still there but I can barely perceive it.

---

### Post by diwas on 2008-09-01
Completely remove compiz and emerald. Reboot the system and install those softwares again. I dont think the problem is wid firefox.

Does this type of behavior(grafics malfunctioning) occur wid other software too?

Did u try removing and installing the graphics driver?

---

### Post by lovinglinux on 2008-09-05
> **diwas said:**
> Completely remove compiz and emerald. Reboot the system and install those softwares again. I dont think the problem is wid firefox.

Does this type of behavior(grafics malfunctioning) occur wid other software too?

Did u try removing and installing the graphics driver?

It is happening with videos too. I installed the latest nVidia drivers usign Envy, but the problem is still there.

---

### Post by Crafty Kisses on 2008-09-05
Try disabling desktop effects and see if that solves the issue.

---

### Post by lovinglinux on 2008-09-05
> **Codename said:**
> Try disabling desktop effects and see if that solves the issue.

It doesn't help. I have already uninstalled nVidia driver, emerald and compiz, but I got similar results. Instead of freaking bars, the window shows a square like a thumbnail of the last window displayed.  Some videos do not show this effect, depending on the encoding codec I guess.

Recently, Cairo dock started to display this too. Maybe is something related to overlay. I don't know.

Everything else work pretty fine, including compiz cube and other effects. The thing is when I open a new screen with fancy stuff or video, the content takes some time (just a few seconds) to updated the window and when it does, the freaking effect appears.

I also tried installing xserver-xgl, but the problem doesn't go away.

Firefox is not suffering anymore. In the other hand, if I maximize a virtualbox to full screen the effect is the same. Videos running inside a Windows XP vbox doesn't seem to be affected.

---

