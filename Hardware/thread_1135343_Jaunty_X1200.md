---
title: "Jaunty X1200"
date: 2009-04-24
forum: Hardware
---

### Post by Jaded Misanthrope on 2009-04-24
Are there any drivers available on Ubuntu 9.04 for the ATI X1200? It worked fine on 8.10, and although I could downgrade back to 8.10 I'd prefer to run 9.04 if at all possible. The card worked fine on 8.04 and better still on 8.10, but all of the drivers seem to have vanished for 9.04: surely drivers are still available?

---

### Post by Jaded Misanthrope on 2009-04-25
Surely there has to be a workaround; I only really need them to run Google Earth and a few other programs with similar graphical demands.

---

### Post by StuartN on 2009-04-25
> **Jaded Misanthrope said:**
> Are there any drivers available on Ubuntu 9.04 for the ATI X1200? It worked fine on 8.10, and although I could downgrade back to 8.10 I'd prefer to run 9.04 if at all possible. The card worked fine on 8.04 and better still on 8.10, but all of the drivers seem to have vanished for 9.04: surely drivers are still available?

If you upgrade to 9.04 then you lose the proprietary ATI Catalyst driver which no longer supports "legacy" cards (some just 2 years old!) and you can't downgrade the Catalyst to an earlier version because earlier versions do not work with X server 1.6.

Ubuntu does a good job of selecting either "ati" or "radeon" according to your card, but performance will be worse than the proprietary driver that works with Ubuntu 8.10 or 8.04.

Anyone who has not upgraded should test their current graphics and the performance on the Live CD before upgrading. fgl_glxgears from a terminal will display a frames per second performance indicator.

---

### Post by Jaded Misanthrope on 2009-04-25
I don't suppose there's a way to downgrade the X server version to that used in 8.10?

---

### Post by Jaded Misanthrope on 2009-04-25
Sorry to bump this, but I really would like to use Jaunty if possible.

---

### Post by StuartN on 2009-04-25
> **Jaded Misanthrope said:**
> Sorry to bump this, but I really would like to use Jaunty if possible.

I think you are stuck with the ati or radeon drivers in 9.04, at least for now.

---

### Post by Jaded Misanthrope on 2009-04-25
> **StuartN said:**
> I think you are stuck with the ati or radeon drivers in 9.04, at least for now.

You mean the open-source drivers, right? If I could use the proprietary ATI drivers it'd be fine.

---

### Post by burvowski on 2009-04-25
> **Jaded Misanthrope said:**
> You mean the open-source drivers, right? If I could use the proprietary ATI drivers it'd be fine.

At this point you can't, unless you downgrade Ubuntu back to 8.10

---

### Post by StuartN on 2009-04-25
> **Jaded Misanthrope said:**
> You mean the open-source drivers, right? If I could use the proprietary ATI drivers it'd be fine.

Yes, the open source drivers. The new ATI 9.4 proprietary driver doesn't support "legacy" cards and versions 9.3 and earlier don't support X server 1.6.

My card runs glxgears at 320 fps using the "radeon" driver under Ubuntu 9.04, but 2,200 fps using the ATI driver under 8.10 (seven times faster). Compiz effects looked okay in 9.04, although I didn't try video playback.

---

### Post by Jaded Misanthrope on 2009-04-25
> **StuartN said:**
> Yes, the open source drivers. The new ATI 9.4 proprietary driver doesn't support "legacy" cards and versions 9.3 and earlier don't support X server 1.6.

My card runs glxgears at 320 fps using the "radeon" driver under Ubuntu 9.04, but 2,200 fps using the ATI driver under 8.10 (seven times faster). Compiz effects looked okay in 9.04, although I didn't try video playback.

Unfortunately, I can't even run glxgears under 9.04: I get some kind of buffer error, if memory serves (I never bothered to check the exact error, though I could get it from the LiveCD is necessary). Out of curiosity, what is your card, anyway?

---

### Post by StuartN on 2009-04-26
> **Jaded Misanthrope said:**
> Out of curiosity, what is your card, anyway?

ATI Radeon Xpress 200M with driver fglrx_pci (in Ubuntu 8.10).

---

### Post by GOVATENT on 2009-04-26
I hope we find a solution. I formated my system for the new release. I don't want to setup 8.10 to do an update later. Ill play with Windows 7 for a few days :( and keep an eye on AMD and ill send them an email. Though I am sure I am screwed now on using 9.04 with the ati driver. Last ATI product ill buy if they don't fix it.

---

### Post by burvowski on 2009-04-26
Same here. I'll be buying Nvidia from now on.

---

### Post by HPD2 on 2009-04-26
I know for a fact that my Dell D810 has the last ATI product i will use. The laptop has a radion X600m in it. The sad part is I can't use some of the screen savers because it screws up the computer. I get horazonal lines going acrost the screen and it changes colors from my normal desktop to a white then to a violet color. I never had that problem in 8.10.

---

### Post by zoward on 2009-04-27
Folks, before you go on hating on ATI: before they dropped proprietary driver support for the R300-R500 chipsets, they released the full specs for the chipsets and have at least one full-time developer (and some surouces say three developers) working on the open source ati driver to add full acceleration.  I have the Xpress 1200 chipset, and can run compiz flawlessly.  My glxgears numbers are terrible (~350 FPS range), but there's also a regression bug in mesa (the open source OopenGL implmentation) that may be responsible since other people running the x1200 have recompiled mesa and reported much higher framerates from glxgears ([http://www.nabble.com/R300-regression-td23108996.html](http://www.nabble.com/R300-regression-td23108996.html))

What would you rather have: a proprietary solution that works now and will go away soon, or an open-source solution that will, for all intents and purposes, be available forever?  Nvidia drops support for chipsets all the time, and once they do, you're out of luck. I wish there was less of a gap between availability of the proprietary and open source ati drivers, but it's worth taking the long view here.

---

### Post by GOVATENT on 2009-04-30
Hey zoward. Thanks for your words. I did get 9.04 setup and running using the opensource drivers. And to think about it, i don't know why i did not do it before. I can run compiz and play game without the screen flashing and compiz does not lag my system anymore. So ill stick to open source. Very good point. This driver is god like. Yea, I do get 300 fps in gfxgears but I know they will fix it.

---

### Post by ckyidr9 on 2009-05-01
> **zoward said:**
>   I have the Xpress 1200 chipset, and can run compiz flawlessly.

On Ubuntu 9.04?

Which open source drivers are you using? radeonhd? I try those with my Xpress 1200 and Xserver failed to start and needed to be reconfigured.

Am I using the right drivers?

Thanks

---

### Post by Klaynos on 2009-06-14
I'd like to echo, which driver are you using? my glxgears numbers are around 55fps... and no compiz either :(

---

### Post by Klaynos on 2009-06-14
OK, so with a bit of playing, putting Driver "ati" into xorg.conf I can now get compiz to work and glxgears values of around 250fps... much much better!

---

