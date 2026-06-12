---
title: "Question about graphics drivers and hardware support"
date: 2016-03-11
forum: Hardware
---

### Post by lakeshore2985 on 2016-03-11
So I've been having some annoying issues regarding Linux distributions and graphics support with my NUC D54250XXX (IGP HD5000). I have experienced noticeable screen tearing under certain Linux distros and came to realize it's about the desktop environment, not the distro itself or the display manager in use (probably, not sure). So far Cinnamon, LXDE and XFCE all of which give me terrible screen tearing and slow 2D performance. Now XFCE4, KDE and Unity seems to work fine without screen tearing. Also it's worth noting Unity, which is considered heavyweight runs faster and much smoother than lightweight Cinnamon for example, which is quite weird! Can anybody explain why this is happening?

---

### Post by buzzingrobot on 2016-03-12
Google will turn up various tweaks claiming to fix that tearing on Intel.  I haven't tried any of them, though.

You are probably noticing the differences between the windows managers in each of those environments, as well as their compositor. Cinnamon uses a fork of Gnome's Mutter window manager.  LXDE uses Openbox and has no compositing. Unity uses Compiz. XFCE uses xfcewm, and KDE uses Kwin. 

I generally run on Intel Haswell. I don't stress the video side, so the most annoying thing I see is mild tearing with smooth scrolling enabled in Firefox. I don't see that at all in Unity or Gnome, or Mint's Cinnamon. It's very apparent in XFCE, LXDE and KDE.

Subjectively, Unity 15.10 gives me the smoothest display performance of any of the Ubuntu flavors.

---

### Post by lakeshore2985 on 2016-03-12
> **buzzingrobot said:**
>  Subjectively, Unity 15.10 gives me the smoothest display performance of any of the Ubuntu flavors.  Isn't this kind of weird though? Unity, which is perhaps considered the most heavyweight of all desktop environments, yet running faster than LXDE or Cinnamon... For me it seems like a graphics driver compatibility issue or something. And since I'm not a Linux expert, could someone explain whether this is a Linux driver development issue or is it Intel's lack of passion for the Linux community?

---

