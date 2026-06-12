---
title: "Any lightweight releases for older laptops?"
date: 2008-03-04
forum: Hardware &amp; Laptops
---

### Post by Krunktor on 2008-03-04
I want to install Ubuntu on my seven-year-old Toshiba Satellite Pro 4200, with 128 mb RAM, 12 GB HDD and ~500 MHz CPU (my hardware profile won't tell me exactly). Obviously, this isn't going to run any of the latest Ubuntu releases. It doesn't even have enough RAM to install Xubuntu, apparently.

I can't find the system requirements for any of the older releases of Ubuntu, but is there one that should run well on my laptop?

---

### Post by loserboy on 2008-03-04
thats strange that you can't install xubuntu, but there are other distros you can use... puppy linux seems to be a popular one

---

### Post by dptxp on 2008-03-04
Go for AntiX. It is a light version of Mepis. Debian based.
If needed, make a SWAP partition of 512MB first with GParted.

You can use Puppy too, shall run damn fast.

---

### Post by Krunktor on 2008-03-05
> **loserboy said:**
> thats strange that you can't install xubuntu, but there are other distros you can use... puppy linux seems to be a popular one
When I checked the installation specs for Xubuntu, it said I'd need 192 MB RAM. I have an empty RAM slot though, so I should probably try upgrading that first.

---

### Post by tagecho on 2008-03-05
older laptops without cd rom too . Looks interest.

---

### Post by kostkon on 2008-03-05
> **Krunktor said:**
> I want to install Ubuntu on my seven-year-old Toshiba Satellite Pro 4200, with 128 mb RAM, 12 GB HDD and ~500 MHz CPU (my hardware profile won't tell me exactly). Obviously, this isn't going to run any of the latest Ubuntu releases. It doesn't even have enough RAM to install Xubuntu, apparently.

I can't find the system requirements for any of the older releases of Ubuntu, but is there one that should run well on my laptop?

You can install *Xubuntu*; you just have to use the *Alternate Install CD* and not the *Live CD*. Although *Xubuntu* requires 128MB of RAM to run, it needs 192MB for installation using the *Live CD*. But, the *Alternate Install CD* only requires 64MB. Thus, I recommend you to go for it, it's a very good OS.

---

### Post by kerry_s on 2008-03-05
> **Krunktor said:**
> I want to install Ubuntu on my seven-year-old Toshiba Satellite Pro 4200, with 128 mb RAM, 12 GB HDD and ~500 MHz CPU (my hardware profile won't tell me exactly). Obviously, this isn't going to run any of the latest Ubuntu releases. It doesn't even have enough RAM to install Xubuntu, apparently.

I can't find the system requirements for any of the older releases of Ubuntu, but is there one that should run well on my laptop?

fluxbuntu would probably be the best "ubuntu" based version for those specs.
[http://releases.fluxbuntu.org/7.10/rc/](http://releases.fluxbuntu.org/7.10/rc/)

dsl is the standard for low resource rigs.
[http://damnsmalllinux.org/](http://damnsmalllinux.org/)

a debian custom install would be the fastest.
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

do the base install, when it comes to package selection uncheck both
log in as root
apt-get install xorg gdm synaptic iceweasel (a lite wm) (a lite filemanager) (a lite editor)
reboot(ctrl+alt+delete)
log in as the user you made
open synaptic and keep building up from there with what ever you need.

i don't think your ready for custom yet, so just use the prebuilts till you get familiar.

---

### Post by egalvan on 2008-03-05
I've installed Xubunu on 128mb machines, but as stated in previous msg, you need to use the Alternative Install CD, not the Live CD.

 It's slow with so little memory, though. You may be happier with Puppy or DSL, or FluxUbuntu.

---

### Post by barnacleboy on 2008-03-05
I'm running Xubuntu on a Pentium 766 with 128mb RAM. It runs OK, even got the RT73-based USB wireless working.

DSL was amazingly fast and had a nice GUI but nothing worked out of the box, which put me off.

---

### Post by santiagoward2000 on 2008-03-05
> **Krunktor said:**
> When I checked the installation specs for Xubuntu, it said I'd need 192 MB RAM. I have an empty RAM slot though, so I should probably try upgrading that first.

That's for installing with a LiveCD (at least according to Xubuntu's page, but since Fesity I can't install it using a LiveCD with my 192MB RAM laptop, so I started using AlternateCDs).
I guess an AlternateCD will install, but I'm not sure how smooth it'll be.
Perhaps Puppy will work for you.
Cheers!

---

### Post by Krunktor on 2008-03-06
Thanks for all of the help. Fluxbuntu certainly looks the most appealing. A big part of my interest in Ubuntu is the visual style, which sort of leaves DSL out of the running.

Anyway, I'll give that a try and let you know if there's any trouble.

---

### Post by jrusso2 on 2008-03-06
I run a 400 mhz Celeron Laptop with 128 mb of ram on Sam Linux.  It has a choice of desktops, standard is XFCE but I find the ICEWM to be the best in terms of being light yet easy to use

---

### Post by egalvan on 2008-03-11
> A big part of my interest in Ubuntu is the visual style

By "style" do you mean "how it works" or "how it looks"?

examples of each

"works" -- contents visible versus outline only while dragging
             menus fade-in versus pop-up

"looks" --  colors, rounded edges versus square edges

"works" is more demanding of CPU/GPU & RAM that "looks".

Even the light-weight desktops have different themes. Try them all. That's one beauty of Linux, the choices. Download them, or try OSDISC.com to order them, if your connection speed is slow.

---

