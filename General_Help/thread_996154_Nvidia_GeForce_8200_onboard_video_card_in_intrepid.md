---
title: "Nvidia GeForce 8200 onboard video card in intrepid 8.10 causes screen to &quot;flicker&quot;"
date: 2008-11-28
forum: General Help
---

### Post by Adunamia on 2008-11-28
I am a decently experienced user with my experience between Fedora 8 and 9, Mint, PDL, and now Ubuntu. I am currently running Ubuntu 8.10 "intrepid" with the gnome desktop. My problem right now is that with the given NVidia drivers (including the one you can download from their site) my screen "flickers" constantly during certain tasks. It seems to do this while loading things in firefox, if I have nothing open in the Desktop, or if anything is using any significant system resources (5% or more it seems). I have tried tinkering with the nvidia x settings using the sync to v blank option, but nothing I have done there has worked. The best driver I have found so far is the proprietary 173 driver, as it has the most windows and situations that cause the screen not to flicker. I have tried looking at my xorg.conf file to see if anything was obviously wrong, but i could not spot anything. I know intrepid is still in a bit of a development and use at your own risk type stage right now, but unlike every other distro (including earlier versions of ubuntu) it actually recognizes my NVidia hardware and makes my sound work properly. Any help would be appreciated and if you want any output of commands simply ask for it and I will be happy to supply it.
Thanks,
Adunamia

---

### Post by Kyosys on 2008-12-26
same card, same problem. 

If I use dual monitors, only the second monitor flickers regularly when clicking something or scrolling. The first one then flickers very, VERY rarely. 

Could anybody help me? (perhaps the original poster found a solution?)

---

### Post by Usufruct on 2008-12-26
I had some annoying flickering issues that were solved starting with the 180.06 beta driver.  It did not solve the flickering issue I'm having with screensavers.  If you feel up to installing beta graphics drivers, here's an easy way:

Download the most recent beta from nVidia ([x86]("http://www.nvidia.com/object/linux_display_ia32_180.17.html")) or ([AMD64/EM64T]("http://www.nvidia.com/object/linux_display_amd64_180.17.html")).

Stop X windows.  If you're using gnome, run:

```
sudo /etc/init.d/gdm stop
```

Install the driver:

```
sudo sh NVIDIA-Linux-x86_64-180.17-pkg2.run
```

Follow the instructions during the install, it's pretty straightforward.  Then reboot or re-start x-windows:

```
sudo /etc/init.d/gdm start
```


I'm not specifically *recommending* you use the beta drivers, and I can't even guarantee that they will solve your issue, but if you're into testing pre-release software, have at it.

---

### Post by Kyosys on 2008-12-26
it's always saying I'm still running X. Even if I don't even log in to the grpahical linux and press CTRL + ALT + F1 right at the start. 
Could this have something to do with the fact that I am running an ubuntu that was turned into a kubuntu (and thus has both KDE and Gnome)?

edit: I got it to work, but the flickering is not fixed.

---

### Post by CubsKing99 on 2008-12-28
Has anyone figured this out yet?  I'm pretty new to Linux, and I'm getting really frustrated trying to get this working.  I'm getting most of the screen flickering white almost constantly and it's driving me insane...

Mark

---

### Post by flameproof on 2009-01-10
... have the same problem with onboard GeForce 8100 and 8.10-64

173 - some flicker then moving the mouse. Much worse when I use the 8.10 background. With monochrome background it's better, but not gone.

177 - strong flicker also with monochrome background. Can only see top of screen, bottom stays mostly black.

I did not manage to install any of the 180.** versions. All failed, or I am too dumb.

---

### Post by Adunamia on 2009-07-01
Sorry about the huge delay here, but I figured out a way to fix this. Go to the xfx support webpage ([http://www.xfxforce.com/en-us/Help/Support.aspx]("http://www.xfxforce.com/en-us/Help/Support.aspx")) and register your motherboard. Install the bios update and any sound and/or video problems you have should disappear. Worked like a champ for me!

---

