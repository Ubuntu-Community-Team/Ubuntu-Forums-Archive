---
title: "New intel video driver package"
date: 2008-07-31
forum: Hardware
---

### Post by melchiorre on 2008-07-31
Hi all, I packaged the last version intel video driver, 2.4.0 for hardy, both i386 and amd64.
This driver has New Intel 4 series chipset support (x4500 igp), improved 965 exa render performance, integrated HDMI support and SDVO-HDMI support (e.g ASUS P5E-VM board).
If you want to download it or just to know more, go here:

[http://melchiorre.wordpress.com/2008/07/31/driver-intel-240-deb-package/]("http://melchiorre.wordpress.com/2008/07/31/driver-intel-240-deb-package/")

I hope I have done one thing welcome :guitar:

---

### Post by trash on 2008-07-31
SWEET! but i just tried to install it and i'm told it conflicts with i810 driver:(... any ideas?

EDIT: nevermind, i didn't know gdebi has some limitations! I added your repo and all is well:)

Thanks!

---

### Post by n2dabloo on 2008-08-04
I just downloaded the new driver thru my update manager.  I still cannot use Compiz with my 965 card.  Any advice, or is Compiz still not an option with this chip?

---

### Post by n2dabloo on 2008-08-04
> **trash said:**
> SWEET! but i just tried to install it and i'm told it conflicts with i810 driver:(... any ideas?

EDIT: nevermind, i didn't know gdebi has some limitations! I added your repo and all is well:)

Thanks!
What did you do to make it work?  Please explain.

---

### Post by trash on 2008-08-04
> **n2dabloo said:**
> What did you do to make it work?  Please explain.

I just added the repo in synaptic and it upgraded...

deb [http://ppa.launchpad.net/melchiorre/ubuntu](http://ppa.launchpad.net/melchiorre/ubuntu) hardy main

My card is an gm855 and i don't know anything about your card sorry.
sorry if this is a silly question but is 'intel' already in your xorg.conf?

---

### Post by n2dabloo on 2008-08-04
> My card is an gm855 and i don't know anything about your card sorry.
sorry if this is a silly question but is 'intel' already in your xorg.conf?

I'm not sure if "intel" is in my xorg.conf, how do I determine this?  Thanks in advance.

---

### Post by trash on 2008-08-04
open a terminal and type:

cat /etc/X11/xorg.conf

then look at the 'device' section for Driver "xxxxxxx"

if it's something other than intel

you need to edit /etc/X11/xorg.conf and change the driver to intel.

good luck!

---

### Post by Junk_head on 2008-08-04
just installed this and my resolution and compiz setup is mucked up. I used the repo to install. Am i forgetting some crucial step or something?

---

### Post by trash on 2008-08-04
sadly, Hardy has some pretty bad xorg problems so things may not be getting configured properly.... search xorg configuration for you card and modify your file accordingly.

On my install compiz seems to work fine so i don't think it has anything to do with that... good luck.

---

