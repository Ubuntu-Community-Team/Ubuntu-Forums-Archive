---
title: "Disabling CD/DVD drive when not in use"
date: 2009-11-01
forum: Hardware
---

### Post by sexyclient on 2009-11-01
I'd like to be able to disable my laptop's cd/dvd drive (either automatically or by creating scripts to run manually from the desktop) in order to save power.

I've been running my laptop from battery-power for about 2 hours now and it's at 61% remaining (4 hours remaining.)  Those are pretty nice figures, but I'd like them nicer.

---

### Post by sexyclient on 2009-11-05
I've tried powertop's suggestion of "usbcore.autosuspend=1" -- well, I've pressed "U" when prompted to do so, but this doesn't work.  There usn't a grub menu.lst (or whatever) and I can't figure out how to enable usb auto-suspend in grub2.  Any grub2 experts out there can offer some assistance?

---

### Post by sexyclient2 on 2009-11-06
bumpity-bump,

for the love of my battery, someone help me out here.

---

### Post by sexyclient2 on 2009-11-08
usbcore.autosuspend in grub2 (or grub-pc, if you will,) anyone?

---

### Post by nzroller on 2009-11-15
I'm looking for this too... if I figure it out I'll post an answer.

---

### Post by nzroller on 2009-11-15
OK from [this thread]("https://bugs.launchpad.net/ubuntu/+source/powertop/+bug/136549") it's possible that powertop is giving an incorrect suggestion — usbcore is a kernel module in ubuntu and not a part of the kernel proper which means adding as part of the kernel grub2 configuration doesn't do anything?

In any case your setup may be different so try changing the ``defoptions'' line in ``menu.lst'' in [exactly the same way]("https://wiki.ubuntu.com/Grub2") as you would with grub...

```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash usbcore.autosuspend=1

```

Then grub ``sudo update-grub'' and reboot.

---

### Post by sexyclient2 on 2009-11-15
Grub2 no longer uses menu.lst, so that's not in /boot or /boot/grub anywhere, just a bunch of .mod files.  Because of this, now, aside from not being sure whether it would work any longer (with all of the kernel updates since its release and powertop not having been updated in a few years,) I just don't know what file I'm supposed to edit since menu.lst no longer exists and there are big, bold, red letters in the FAQ telling you not to edit grub.cfg file.

EDIT:  I found the line, teehee (*GRUB_CMDLINE_LINUX_DEFAULT*, in /etc/default/grub .)  I'll give her a test now to see what's up.

Sweet!  It worked, thread solved -- but I can't remember my old password or, apparently, the email address either, so I can't recover my account...  PROBLEM (and thread) SOLVED!

---

