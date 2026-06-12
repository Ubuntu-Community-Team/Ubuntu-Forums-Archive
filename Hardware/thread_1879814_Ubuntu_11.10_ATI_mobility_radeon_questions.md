---
title: "Ubuntu 11.10 ATI mobility radeon questions"
date: 2011-11-12
forum: Hardware
---

### Post by Tamale on 2011-11-12
I just upgraded my HP Elitebook nc8430 laptop to 11.10, and upon doing so I of course decided to give unity a try.

Unfortunately, I can't say that I like it. I have external monitors hooked up to my laptop and I don't like the launcher bar being locked to the left side of the screen - I'd very much prefer to have that at the bottom for my workflow, and it doesn't look like moving it is going to be an option anytime soon.

I'd like to get the standard gnome interface back with compiz, but after trying to follow a guide to install fglrx I rebooted and found that aticonfig is saying:

:~$ sudo aticonfig
aticonfig: No supported adapters detected


So, basically, all I'd like to do now is go back to standard gnome with compiz with fglrx enabled and running properly again.  Can anyone help?

Thanks

-- edit - looks like fglrx support was dropped for older cards like mine some time ago.. ugh.  Ok then, can I still have compiz and standard gnome with the open source drivers?  If so, how?

---

### Post by Erik500002 on 2011-11-12
Well to my knowledge the fglrx driver only works with the Radeon HD series and above. Older legacy cards like the x1600 must use the open source drivers. Don't worry I have the same issues, in fact I have the same laptop and I'm struggling quite a bit to improve performance on 11.10. I remember back in the days with lucid lynx everything worked like a charm. The only alternative is to install the legacy drivers but I have no idea how to install them on orneiric since they are only for kernel 2.6. Well anyways good luck.


EDIT: Forgot the link to the legacy drivers.

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx)

---

### Post by Roasted on 2011-11-12
I was disappointed to hear this as well. ATI has been all kinds of fail lately.

---

### Post by Erik500002 on 2011-11-12
Indeed, I have another laptop with a pretty old nvidia card and the drivers are compatible with the latest kernels. It's a big shame for ATI and to be honest the x1600 is not that old of a card and has great performance running under windows. I wish there were patches to the catalyst driver like there are in windows, to be able to install them for legacy cards. I guess I'm going back to windows with this distro. :(

---

### Post by Roasted on 2011-11-12
> **Erik500002 said:**
> Indeed, I have another laptop with a pretty old nvidia card and the drivers are compatible with the latest kernels. It's a big shame for ATI and to be honest the x1600 is not that old of a card and has great performance running under windows. I wish there were patches to the catalyst driver like there are in windows, to be able to install them for legacy cards. I guess I'm going back to windows with this distro. :(

I haven't noticed anything with my older Nvidia systems. They keep chugging along great with the latest releases. However ATI on the other hand drops support for hardly "old" equipment? Fail.

---

### Post by MoreOrLess on 2011-11-12
> **Erik500002 said:**
> EDIT: Forgot the link to the legacy drivers.
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx)

Bad advice. Please don't link people to those drivers as they don't work on any modern version of Ubuntu ( >= 9.04).

---

### Post by MoreOrLess on 2011-11-12
3D/Compiz should work fine once you completely remove your botched install of fglrx/Catalyst: [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

### Post by Tamale on 2011-11-12
> **MoreOrLess said:**
> 3D/Compiz should work fine once you completely remove your botched install of fglrx/Catalyst: [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx)

And how do I get gnome/compiz working once I remove the driver?

---

### Post by scradock on 2011-11-12
> **Tamale said:**
> And how do I get gnome/compiz working once I remove the driver?

I have an even older HP Pavilion, with the open-source drivers. No problems with gnome2, compiz, unity or even gnome shell. I'm running Precise, Oneiric, Natty and maverick on it. The open-source drivers don't give me accelerated 3d, apparently, but that's not what I need.

Make sure you have the open-source drivers for -ati and -radeon installed (you may need -radeonhd with your "modern machine"). Get rid of any xorg.conf file you may have in /etc/X11/. Then purge fglrx...

Then you could try installing the unity2d packages, which don't need compiz, or re-install compiz and unity with all their hangers-on.

HTH

---

### Post by Roasted on 2011-11-12
> **scradock said:**
> I have an even older HP Pavilion, with the open-source drivers. No problems with gnome2, compiz, unity or even gnome shell. I'm running Precise, Oneiric, Natty and maverick on it. The open-source drivers don't give me accelerated 3d, apparently, but that's not what I need.

Make sure you have the open-source drivers for -ati and -radeon installed (you may need -radeonhd with your "modern machine"). Get rid of any xorg.conf file you may have in /etc/X11/. Then purge fglrx...

Then you could try installing the unity2d packages, which don't need compiz, or re-install compiz and unity with all their hangers-on.

HTH

I'm surprised it works. My mother's laptop isn't *that* old yet her ATI card failed to work with Gnome Shell in 11.10. :(

---

### Post by MoreOrLess on 2011-11-12
> **scradock said:**
> No problems with gnome2, compiz, unity or even gnome shell. I'm running Precise, Oneiric, Natty and maverick on it. The open-source drivers don't give me accelerated 3d, apparently, but that's not what I need.
If you're running compiz, then of course you have hardware-accelerated 3D. Where did you get the idea you don't?

> Make sure you have the open-source drivers for -ati and -radeon installed (you may need -radeonhd with your "modern machine").
The "radeonhd" driver is long deprecated. "radeon" handles all GPU's with radeon(hd) in their name.
```
man radeon
```

---

### Post by njrob on 2012-02-17
> **MoreOrLess said:**
> If you're running compiz, then of course you have hardware-accelerated 3D. Where did you get the idea you don't?


The "radeonhd" driver is long deprecated. "radeon" handles all GPU's with radeon(hd) in their name.
```
man radeon
```

Just let me clarify: Are you saying that Compiz provides OpenGL support for ATI graphics cards in an Ubuntu os?

---

