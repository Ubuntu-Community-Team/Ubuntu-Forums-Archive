---
title: "nasty upgrade problems"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by ray field on 2009-01-31
[using adamm's kernel on an eee PC 1000]

yesterday I installed a bunch of updates -- it took someone telling me that Grub was now booting a different entry for me to realize that was the initial source of problems.

now however, something seems seriously broken in X/gnome -- the first time I managed to boot the (proper) array kernel, my desktop had almost finished populating when it suddenly green-screened and locked up completely.  subsequent attempt either booting straight up or trying from the fisit mode, get me to the login screen, but gnome aborts at some point after that -- usually right after after the compiz-fusion splash, though at times the lockup has started after the first bootup soundfile is played -- blank (background) screen.

I guess the first step is uninstalling compiz -- how do I do this without losing the possibility of returning to my old configuration?

---

### Post by ray field on 2009-01-31
> **ray field said:**
> [using adamm's kernel on an eee PC 1000]
I guess the first step is uninstalling compiz -- how do I do this without losing the possibility of returning to my old configuration?

I booted to recovery mode and issued

sudo chmod a-x compiz.real

but froze up again as soon as the drums started sounding.

---

### Post by ray field on 2009-01-31
at other times, the desktop comes up successfully, but then the display goes wacko, like a busted television set

---

### Post by ray field on 2009-01-31
is it possible cairo-dock is causing these problems?  how can I disable it (hopefully without losing my configuration files) from recovery mode -- I don't know the version, so I can't do as instructed at cairo-dock org which is 

If you want to keep the configuration files:
sudo dpkg -r cairo-dock-plug-ins_++version++
sudo dpkg -r cairo-dock_++version++

---

### Post by ray field on 2009-01-31
well, okay (starting to feel like someone shaking the locked doors  to the store at 3AM Sunday morning)

I managed to boot to a command line and move out all the programs from the /.config folder, but I still cannot get to my desktop.  sometimes, after tte drumbeat, the background just vanishes and gives way to a darker color and all activity ceases; other times, the desktop nearly completes populating and then the "static-filled tv effect" comes and I have to hold down the power button to shot down.

it doesn't seem to be caused by cairo-desktop.  but I don't know what it is -- video driver issue?  I had done a good bit of playing around, mostly attempting to sync my Treo, but nothing I thought would affect gnome.

---

### Post by kvk on 2009-01-31
I'm experiencing a similar issue to yours, though somewhat reduced in scale. Running the most recent upgrades of the kernel headers added two new configurations to the GRUB boot file, and my system hangs on both shutdown and boot (boots into the recovery console).

I've set my GRUB configuration to boot from the rt kernel, so I'm not sure why the new headers would affect it as they were generic headers, if I recall correctly. 

I'm not sure of the solution- just wanted to say...you are not alone...

---

### Post by ray field on 2009-02-01
> **kvk said:**
> I'm experiencing a similar issue to yours, though somewhat reduced in scale. Running the most recent upgrades of the kernel headers added two new configurations to the GRUB boot file, and my system hangs on both shutdown and boot (boots into the recovery console).

I've set my GRUB configuration to boot from the rt kernel, so I'm not sure why the new headers would affect it as they were generic headers, if I recall correctly. 

I'm not sure of the solution- just wanted to say...you are not alone...

guess I should know, but what's the rt kernel?

I decided to try running the new kernel and strangely it seems to work ok, except for having broken wicd. so for the moment I've dispensed with this custom eeePC kernel.

---

