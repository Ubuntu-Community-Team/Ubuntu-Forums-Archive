---
title: "tascam us122 doesn't seem to work on intrepid"
date: 2008-11-07
forum: Hardware
---

### Post by Bartje on 2008-11-07
Hi,

I got a tascam us 122 working on a 32bit hardy, but on my 64 bit intrepid it doesn't seem to work. Can anyone help me?

I've followed this guide, but it doesn't help me.

[http://alsa.opensrc.org/Tascam_US-122]("http://alsa.opensrc.org/Tascam_US-122")

it would be of great help if I got it working on my 64 bit intrepid

---

### Post by ouija on 2008-11-07
The following worked for me in Hardy 64x and maybe will fix your issue.  Please try and post your results, or I'll post mine if and when I upgrade to Intrepid.

Hardy Heron Fix

From energymomentum on the Ubuntu forums ([http://ubuntuforums.org/showthread.php?t=734730):](http://ubuntuforums.org/showthread.php?t=734730):)

I upgraded from Kubuntu Gutsy to Kubuntu Hardy and found that my US122 USB sound interface didn't work any more.

The main issue was that usx2yloader (in alsa-firmware-loaders package) in hardy assumes that the necessary files are in /lib/firmware/usx2yloader, while for the old usx2yloader it was /usr/share/alsa/firmware/usx2yloader.

I already had everything under /usr/share/alsa/firmware/usx2yloader from my Gutsy installation, so I just symlinked this to a new location:

ln -s /usr/share/alsa/firmware/usx2yloader /lib/firmware/usx2yloader

After doing this, a local udev rules file I copied from this thread ([http://ubuntuforums.org/showthread.php?t=431066](http://ubuntuforums.org/showthread.php?t=431066)) took care of everything.

Somewhat strange thing is, there is a udev rule for Tascam interfaces (/etc/udev/alsa-firmware-loaders.rules) in udev package, which apparently doesn't do anything for my US122. I still need to keep my own udev rules file mentioned above.

---

### Post by Bartje on 2008-11-08
What you describe is exactly what I did, linking usx2yloader to the other folder and making a udev.rules file. It is exactly that which is described on the page I mentioned on my earlier post.

It did not work.

Perhaps it should have yet another location now?

Maybe these "/etc/udev/alsa-firmware-loaders.rules" you talk about now do play an important role?

---

### Post by Bartje on 2008-11-12
no other suggestions?

---

### Post by Maddy on 2009-01-27
> **Bartje said:**
> no other suggestions?

Bart,


Can you check with 'dmesg' in a terminal window if the firmware for the tascam-122 is loaded ? If not you will see errors.


Regards,
Dirk

---

