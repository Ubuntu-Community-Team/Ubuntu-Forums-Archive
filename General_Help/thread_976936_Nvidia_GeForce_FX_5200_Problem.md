---
title: "Nvidia GeForce FX 5200 Problem"
date: 2008-11-09
forum: General Help
---

### Post by jaygeebuntu on 2008-11-09
Using Intrepid Ibex 8.10 I can't enable Desktop Effects within Applications>System>Preferences>Appearance>Visual Effects. Attempts to set any of the Normal/Extra/Custom radio button options meet with a "Desktop effects could not be enabled" error report.

I've installed all the available Nvidia modules I can find using Synaptic and the card works fine in Fedora 9.

Is this a short term 8.10 Nvidia driver problem or is there a reasonably easy fix?

Any help would be appreciated.

---

### Post by WSmart on 2008-11-09
Did the System>Administration>Hardware driver install the proprietary?  Ubuntu just changed to a new system, called Jockey, and there's some early issues.  If you enable System>Admintration>Software Sources>Updates tab>enable/check Pre-release update(Intreprid Proposed), that should give you a driver, if you're not getting one.  

Worked for me and I'm so happy about it after messing with this for a week.  Thanks to Alberto Milone, the EnvyNG guy, for his blog post on this.   [http://albertomilone.com/wordpress/](http://albertomilone.com/wordpress/)

---

### Post by jaygeebuntu on 2008-11-10
System>Administration>Hardware Drivers reported "This driver - NVIDIA accelerated driver version 173 recommended - is activated and currently in use"

So I uninstalled the driver, rebooted, added the Intrepid Proposed repo, installed their updates, reintalled the drive when prompted, rebooted and re-tried Applications>System>Preferences>Appearance>Visual Effects.

Unfortunately no change. I'm stuck with "None - provides a simple desktop environment without any effects".

Having compared Fedora 9's list of installed Nvidia modules with Intrepid's I'm not convinced I've currently got the same functionality.

Thanks for your help anyway. I'll have to learn to live without wobbly windows and transparency until the situation improves.

Thought I'd add that the Nvidia driver seems to be working as monitor alignment and font definition are superior compared to when it's uninstalled.

---

