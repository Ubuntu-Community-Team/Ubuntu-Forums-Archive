---
title: "after reboot with the new nvidia drivers X does not start"
date: 2010-06-24
forum: Hardware
---

### Post by Ko$ on 2010-06-24
If I got this right its not a problem of nvidia driver but the grub or kernel...

What I did is:

(there are new nvidia drivers available - 256.35)

1. stoped kdm

2. Removed everything old: apt-get --purge remove nvidia*

3. Installed new driver : sh N*.run

4. Started kdm

And it works great.

BUT. After reboot my X does NOT start and says "failed to initialize the Nvidia graphic device".

So I think its a grub issue cause it simply didn`t update something. 

What do I have to do to update grub correctly? 

Or is there another solution to this problem?

---

### Post by dabl on 2010-06-24
Looks like you did everything correctly.  Maybe a kernel boot option, like vga=785, would help (depending on the rest of your hardware and monitor).  Or maybe it's an ACPI or APIC issue -- there are boot options to turn those off, too.

---

### Post by realzippy on 2010-06-24
You can add a ppa with that driver and install it with *hardware drivers*.(nvidia current)


[http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html)

---

### Post by Ko$ on 2010-06-24
> **realzippy said:**
> You can add a ppa with that driver and install it with *hardware drivers*.(nvidia current)


[http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html)

Just tried:

1. First reboot kernel panic, so poweroff button.

2. Second boot goes in a low graphics mode without any questions.

---

### Post by realzippy on 2010-06-24
Would boot in recovery mode and delete xorg.conf (or edit "driver" line to *nv* instead *nvidia*)
Then exit&boot again (VESA should run),then again try to uninstall/install the driver with the hardware drivers GUI....

---

### Post by dino99 on 2010-06-24
if you want/need the latest release, better to use a trusted ppa:

open synaptic repo and add it

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

search into synaptic "nvidia" and remove/purge (right click) ALL the nvidia packages installed

into a console:
sudo apt-get update

then with synaptic, install: nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings

then remove xorg.conf
sudo rm -f /etc/X11/xorg.conf

and reboot

then goto: system admin hardware driver, to check that nvidia-current is activated

---

### Post by realzippy on 2010-06-24
> **dino99 said:**
> if you want/need the latest release, better to use a trusted ppa:

open synaptic repo and add it

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

search into synaptic "nvidia" and remove/purge (right click) ALL the nvidia packages installed

into a console:
sudo apt-get update

then with synaptic, install: nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings

then remove xorg.conf
sudo rm -f /etc/X11/xorg.conf

and reboot

then goto: system admin hardware driver, to check that nvidia-current is activated


That is the *same* ppa,*ubuntu-x-swat.*Would not suggest any dark ppa...

---

### Post by Ko$ on 2010-06-24
> **dino99 said:**
> if you want/need the latest release, better to use a trusted ppa:

open synaptic repo and add it

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

search into synaptic "nvidia" and remove/purge (right click) ALL the nvidia packages installed

into a console:
sudo apt-get update

then with synaptic, install: nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings

then remove xorg.conf
sudo rm -f /etc/X11/xorg.conf

and reboot

then goto: system admin hardware driver, to check that nvidia-current is activated

nothing new, after that I had kernel panic.

---

### Post by Ko$ on 2010-06-24
> **realzippy said:**
> Would boot in recovery mode and delete xorg.conf (or edit "driver" line to *nv* instead *nvidia*)
Then exit&boot again (VESA should run),then again try to uninstall/install the driver with the hardware drivers GUI....

The problem is that what you`re saying is not the solution but the reason.

There is no xorg.conf been genereted automatically.

But now I have that driver worked.

In save mode I repeired "broken packages", and then installed "Recommended driver" so because of the ppa (I guess) it was the 256.35.

---

### Post by dino99 on 2010-06-24
> **Ko$ said:**
> nothing new, after that I had kernel panic.

oh i've forgotten its a feature, you are lucky (but not alone) :lolflag:

---

