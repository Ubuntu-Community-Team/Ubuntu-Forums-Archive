---
title: "ASUS N75SF and Ubuntu 11.10"
date: 2011-11-07
forum: Hardware
---

### Post by richbl on 2011-11-07
All,

I recently purchased a new ASUS N75SF laptop, which utilizes the Nvidia GeForce GT 555m graphics chipset. This chipset uses Nvidia's Optimus technology for managing GPU load between the discrete GPU and the onboard Intel chipset.

Getting Ubuntu 11.10 (Oneiric) installed on this new laptop has, so far, been without success.

With the nomodeset addition in GRUB, I can get Ubuntu installed, but it fails to recognize the Nvidia card properly (no Unity 3D; no correct screen resolution).

I have tried to use both Bumblebee and Ironhide, but these appear to be unstable solutions (no luck so far with getting either solution to hibernate/resume without hanging the system). Understandably, these are pretty new approaches.

Given the state of Optimus support, I'd be happy to just disable 3D acceleration entirely if I can get a stable 2D environment to run.

Ufortunately, BIOS for the N75SF does not permit the disabling of either graphics chipset.

What I REALLY would like to do is this:

A) Run Ubuntu on my Asus N75SF without 3D acceleration (at the moment, I don't care about this and can wait until stable drivers are made native to the platform)

B) Hibernate/resume with consistency.

Has anyone managed this with their ASUS N75SF? If so, how?

Thanks much.

---

### Post by agalitsyn on 2012-01-09
Hi, I have n75sf too.

I use KDE. Founded problems:
[LIST=1]
[*]Ubuntu installation process was crushed. Fixed with acpi=off in grub.
[*]Touchpad wasn't work. Fixed yesterday, I've update BIOS (v214) and made system update. Synaptic driver has been installed.
[*]Multimedia keys don't work.
[*]Subwoofer don't work.
[*]Power manager says "Battery not present"
[*]Sleep and Hibernate don't work.
[*]Battery lifetime is very bad. I think main issue is in Nvidia card. Just can't get how to set up bumblebee or ironhide for this model. So I would be satisfied with turning nvidia card off, as I did on my asus U35JC: [http://ubuntuforums.org/showthread.php?t=1569380](http://ubuntuforums.org/showthread.php?t=1569380)
I wanted to do it, but found inconsistency in on/off commands [http://hybrid-graphics-linux.tuxfamily.org/index.php?title=ACPI_calls](http://hybrid-graphics-linux.tuxfamily.org/index.php?title=ACPI_calls) . Why off command starts from "Cardon =..." ?
[/LIST]

I think my post is corresponds with previous post, so could anybody help?

---

### Post by Vakstal on 2012-01-23
Hello.
I have the same problems with my ASUS N75SF and Ubuntu 11.10.

- some of multimedia keys don't work (play, stop, on/off touchpad)
- subwoofer didn't work. But then I found this ( [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/871808](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/871808) ). I added some commands into /etc/rc.local like in post #17. And now subwoofer works but sounds not very good.
- can't enable/disable touchpad by any hot key, and can't fix it. With Jupiter I can disable it, but it is not really good way.

I solved the problem with Nvidia Optimus when I installed Bumblebee 3.0. Instructions are here ( [https://github.com/Bumblebee-Project/Bumblebee/wiki/Install-and-usage](https://github.com/Bumblebee-Project/Bumblebee/wiki/Install-and-usage) ). It really works, Nvidia card is off when it's not needed. The battery life in power saving mode is about 2-3 hours.

---

### Post by fuduntu on 2012-01-23
> **Vakstal said:**
> 
- can't enable/disable touchpad by any hot key, and can't fix it. With Jupiter I can disable it, but it is not really good way.


How is it not a good way?  What do you recommend be done to improve it?

---

### Post by agalitsyn on 2012-02-01
> **Vakstal said:**
> 
I solved the problem with Nvidia Optimus when I installed Bumblebee 3.0. Instructions are here ( [https://github.com/Bumblebee-Project/Bumblebee/wiki/Install-and-usage](https://github.com/Bumblebee-Project/Bumblebee/wiki/Install-and-usage) ). It really works, Nvidia card is off when it's not needed. The battery life in power saving mode is about 2-3 hours.

I've removed acpi=off and other additional options from grub and install Bumblebee. It works! Also my system now see battery, and some multimedia buttons works.

Except these, which you mentioned.

How to solve screen back-light problems? Brightness value changes when system switch one power profile  to another, but it don't take into account settings, which I configure with multimedia keys. So I often have sudden change of brightness. acpi_backlight=vendor isnt help

---

### Post by Vakstal on 2012-03-30
> **fuduntu said:**
> How is it not a good way?  What do you recommend be done to improve it?

Jupiter just works good, I have no problems with it.
But it would be good to enable/disable touchpad with Fn+F9 (or any other keys), not only in Jupiter menu.
If I disable touchpad and if there is no mouse - how can I enable touchpad?

> **agalitsyn said:**
> So I often have sudden change of brightness. acpi_backlight=vendor isnt help

I didn't find any working solutions for that. I have to put up with it for now.

---

### Post by fuduntu on 2012-03-30
> **Vakstal said:**
> Jupiter just works good, I have no problems with it.
But it would be good to enable/disable touchpad with Fn+F9 (or any other keys), not only in Jupiter menu.
If I disable touchpad and if there is no mouse - how can I enable touchpad?


Look here: [http://sourceforge.net/apps/mediawiki/jupiter/index.php?title=Keybindings](http://sourceforge.net/apps/mediawiki/jupiter/index.php?title=Keybindings) :)

---

### Post by Vakstal on 2012-03-31
> **fuduntu said:**
> Look here: [http://sourceforge.net/apps/mediawiki/jupiter/index.php?title=Keybindings](http://sourceforge.net/apps/mediawiki/jupiter/index.php?title=Keybindings) :)

Oh, I didn't even think that Jupiter is so good, thank you! :)

PS: I've just installed Ubuntu 12.04 and Jupiter. This is awesome - almost everything works fine by default!

---

