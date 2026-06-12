---
title: "booting livecd with nvidia drivers"
date: 2009-10-12
forum: Hardware
---

### Post by fahadayaz on 2009-10-12
hello,

im wondering if its possible to build a custom ubuntu lived cd, one which loads the nvidia drivers on boot. i have seen this on sabayon livecd distros so it must be possible somehow.

---

### Post by rb0171610 on 2009-10-12
> **fahadayaz said:**
> hello,

im wondering if its possible to build a custom ubuntu lived cd, one which loads the nvidia drivers on boot. i have seen this on sabayon livecd distros so it must be possible somehow.

Would it simply involve building the Nvidia driver against the kernel on the CD, and having it load at boot time?

---

### Post by fahadayaz on 2009-10-12
> **rb0171610 said:**
> Would it simply involve building the Nvidia driver against the kernel on the CD, and having it load at boot time?

bingo.. thats exactly what i want :)
any ideas on how i might go about doing that?

---

### Post by rb0171610 on 2009-10-12
> **fahadayaz said:**
> hello,

im wondering if its possible to build a custom ubuntu lived cd, one which loads the nvidia drivers on boot. i have seen this on sabayon livecd distros so it must be possible somehow.

This is a little older, but might be useful to you:

[http://www.techsupportteam.org/forum/linux-alternative-os/3993-customizing-k-ubuntu-linux-live-cd.html]("http://www.techsupportteam.org/forum/linux-alternative-os/3993-customizing-k-ubuntu-linux-live-cd.html")

---

### Post by fahadayaz on 2009-10-12
i've tried remastersys in the past. it allows one to customise the installed programs but it wont load the driver on startup.. actually, it says it in the faq on that page too..
> 
NOTE

1)
Live CD/DVD created from a system with installed proprietary ATI or Nvidia drivers, when booted,
will not load these drivers because casper (the ubuntu Live CD boot routine) disables ati and nvidia proprietary drivers.

If you choose distributable copy you must to uninstall ATI or Nvidia 
drivers.

After that you can "slipstream" - install EnvyNG which will
detect the model of your graphic card (only ATI and Nvidia cards are supported)
and install the appropriate driver on a new machine.

---

### Post by fahadayaz on 2009-10-12
anything else i could try?

---

