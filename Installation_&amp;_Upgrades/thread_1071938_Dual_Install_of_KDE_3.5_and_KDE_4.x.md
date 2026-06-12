---
title: "Dual Install of KDE 3.5 and KDE 4.x"
date: 2009-02-16
forum: Installation &amp; Upgrades
---

### Post by AeroNautica0909 on 2009-02-16
I'm new to Ubuntu but have been using it for three months now. Since I made the switch from Windows Vista, I have vowed to myself I will never go back to Windows. So far, I'm holding true to my promise.

Anyway, I'm using GNOME 2.24 on Ubuntu Intrepid. I installed KDE 3.5.10 on my Intrepid installation from the Pearson Computing Repository. However, I am not entirely a fan of the KDE 4.x series so far but I want to know is it possible to have all three desktop environments installed- GNOME 2.24, KDE 3.5.10 and KDE 4.x installed simultaneously?

Thanks!

---

### Post by Gen2ly on 2009-02-16
I don't think in Ubuntu its possible, at least I've never heard of it.  The only distro I've heard of that's able to do this is Gentoo that makes use of slotting to be able to do this.

---

### Post by AeroNautica0909 on 2009-02-18
Thanks for the information! I decided to remove KDE 3.5.10 and install KDE 4.2. I'm warming up to it. Thanks for the help!

---

### Post by maybeway36 on 2009-02-18
I think it is possible in Ubuntu. The guy who runs the KDE3 repo takes care to rename to avoid conflicts.

---

### Post by AeroNautica0909 on 2009-04-02
You're absolutely right. I was able to install KDE 3.5 and KDE 4.2 by installing the KDE 4.2 Nightly Neon repository. That allowed me to have GNOME, Xfce, and both versions of KDE simultaneously installed. This way I can switch whenever I have that urge.

I suppose I'll have some issues when I decide to upgrade to Jaunty when it comes out... but I'll cross that bridge when I come to it.

---

### Post by zevans on 2009-04-03
> **AeroNautica0909 said:**
> 
I suppose I'll have some issues when I decide to upgrade to Jaunty when it comes out... but I'll cross that bridge when I come to it.

You should be fine - I've done it.

I had KDE 3.5.x and nightly-neon together for quite some time, but now Jaunty seems to have overtaken Neon in functionality and keeping pace with upstream changes. (Neon is run by one guy, basically, so fair enough!)

I uninstalled the Neon packages and dist-upgraded to Jaunty last month - when it was still in early testing - and even most things survived without me doing anything else. I had to purge kdm and force the Jaunty version in if I remember correctly, but once I had done that it would load the 3.5 environment OK. The version of Amarok in Jaunty is much better, unless Neon has caught up again now I've stopped looking...

kdelibs4c2a caused me some dependency problems - this was the only thing that Jaunty and Neon got in a fight about. Eventually uninstalled a few things that synaptic suggested when I tried to remove 4c2a, forced an upgrade to jaunty version of the libs, and then reinstalled all those apps.

I used both for about a month. Now I have purged all the 3.5 stuff because 4.2 / xorg 1.6 is working well for me, and on my hardware happens to be a lot quicker. (With 2.6.29git8 and the xorg-edgers Intel drivers it flies, but it wasn't stable with release 2.6.29, ironically.)

4.2 is the first 4.x version that I've been able to set up anything the way I like, which is why I stuck with 3.5 for some time. Showing my age I guess, I learned on an SS5 with CDE. :-)

Last Friday I commented out the Neon and 3.5.x repos at last and used synaptic to see what had been orphaned by doing that, and purged them all, so everything's neat and tidy now.

---

### Post by AeroNautica0909 on 2009-04-04
Do you have any hardware related issues with using the Jaunty betas? I'm considering installing it since I'm having some issues with newer NVIDIA drivers on my Intrepid installation. I preferably want to wait until the final release comes out.

---

### Post by cacycleworks on 2009-04-06
> **zevans said:**
> I used both for about a month. Now I have purged all the 3.5 stuff because 4.2 / xorg 1.6 is working well for me, and on my hardware happens to be a lot quicker. (With 2.6.29git8 and the xorg-edgers Intel drivers it flies, but it wasn't stable with release 2.6.29, ironically.)

4.2 is the first 4.x version that I've been able to set up anything the way I like, which is why I stuck with 3.5 for some time. Showing my age I guess, I learned on an SS5 with CDE. :-)

Last Friday I commented out the Neon and 3.5.x repos at last and used synaptic to see what had been orphaned by doing that, and purged them all, so everything's neat and tidy now.

Thank you for your post -- it will get me to try KDE4 again. Do you happen to know if they have khotkeys working? That's almost a deal breaker for my work flow & productivity...

Thanks,
Chris

---

