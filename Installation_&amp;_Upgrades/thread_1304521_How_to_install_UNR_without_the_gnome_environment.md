---
title: "How to install UNR without the gnome environment?"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Serguei_89 on 2009-10-29
Hi,

I want to install UNR to take advantage of netbook-targeted performance tweaks, but I don't want to install the Gnome Desktop Environment. (I'm using wmii instead).

How can I do that?

I was thinking of using the "minimal" installation cd, but UNR claims to do some netbook-specific optimizations at the core. Hence the problem.

How can install UNR without the Gnome stuff?

---

### Post by compiledkernel on 2009-10-29
[https://launchpad.net/netbook-remix](https://launchpad.net/netbook-remix) 

Youll note the package involved to the right. You can I think, easily just install those packages indepedently and not fool with attempting to allow aptitude to install gnome with it. 

As far as what happens at the core, Im not real sure anything happens at the "core" level that doesnt already happen during a default install.

---

### Post by Serguei_89 on 2009-10-29
So none of those packages have anything to do with performance. They are all about the UI. 

So would you say I'm better off installing minimal? Or is there a way to opt out of Gnome when installing from a standard ubuntu disk?

---

### Post by compiledkernel on 2009-10-29
I have as a standard always installed with the minimal CD. Im one of those minimal service types (probably why Im also an occasional Archlinux user). Here is a script from the UDSF doc site that might be of interest to you. 

[http://gwos.org/udsf/doku.php/script:minimal:automated](http://gwos.org/udsf/doku.php/script:minimal:automated)

---

### Post by Serguei_89 on 2009-10-30
I just downloaded the minimal cd image (mini.iso), but the package usb-creator refuses to work with anything other than desktop images.

How can I install the minimal image onto my SD card or a flash drive?

---

### Post by snowpine on 2009-10-30
Xubuntu and CrunchBang are two "lightweight" Ubuntu variants that do not use Gnome and also happen to run very well on netbooks.

Don't install UNR unless you like the "launcher" user interface.

---

### Post by Serguei_89 on 2009-10-30
Thanks snowpine, but XFCE or openBox are also not my environments of choice.

I would prefer to install just the bare minimums and then add packages I need on top. Hence the minimal-cd thing.

That is of course unless there is a way to use the desktop or alternate installation image, but opt out from the desktop-environment packages. Is there a way to do that?

---

### Post by snowpine on 2009-10-30
So what do you want to use for your desktop environment, if not gnome/xfce/openbox?

ps Yes, you can do a Command Line Only (CLI) install from the Alternate CDs if you press one of the Fn keys.

---

### Post by Serguei_89 on 2009-10-30
I believe the term is that I want "no desktop-environment". I usually just use a window manager called wmii.

So alternative install image allows to opt-out of packages or somehow install just the CLI setup? I really would be happy with just the CLI setup and then install all the other stuff myself.

---

### Post by snowpine on 2009-10-30
> **Serguei_89 said:**
> I believe the term is that I want "no desktop-environment". I usually just use a window manager called wmii.

So alternative install image allows to opt-out of packages or somehow install just the CLI setup? I really would be happy with just the CLI setup and then install all the other stuff myself.

Gotcha, so your question really has nothing to do with UNR (which is basically a launcher "skin" on top of Gnome).

Lots of excellent guides on a minimal Ubuntu install. This is the one that got me started: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

(substitute wmii for icewm)

---

### Post by Serguei_89 on 2009-10-30
:) Right. Except usb-creator package refuses to build a bootable flash card/drive from a minimal mini.iso.

Hence I'm looking for a way to do that with what likely is an alternative install cd. Any guides for that?

Sorry if I phrased it poorly before. The reason for UNR in the post was that I saw things online claiming that UNR has low level optimizations for netbooks. But that no longer seems to be the case to me.

---

### Post by snowpine on 2009-10-30
In my (limited) experience, UNR is *slower* than regular Ubuntu because it adds an extra layer.

Anyway, you can do a minimal, command line only install from the Alternate CD as well as the mini.iso. Just hit one of the Fn keys (F4? F6? can't remember) at the very first screen.

---

### Post by Serguei_89 on 2009-10-30
Thanks. Gonna try as soon as alternative image is downloaded.

---

