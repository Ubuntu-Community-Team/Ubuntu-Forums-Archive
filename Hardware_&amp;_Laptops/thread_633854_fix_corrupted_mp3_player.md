---
title: "fix corrupted mp3 player?"
date: 2007-12-07
forum: Hardware &amp; Laptops
---

### Post by skullmunky on 2007-12-07
usb cable came loose on my Creative Zen Nano while transferring a bunch of music.  When I plug it back in, it doesn't come up (before it was coming up fine on the desktop and in Amarok).  Dmesg only gives me this:

[  119.884000] usb 1-7: new high speed USB device using ehci_hcd and address 6

previously udev was attaching it to /dev/sdc, but not any more.  Is the filesystem utterly wrecked?  is there any way to recover it ... ?  

i'm gonna go get out my walkman and some tapes for this long  bus ride tomorrow ...

FIXED: kinda.   how?  plugged it into a different USB port.  now pretty much all happy.  except amarok, when transferring the mp3's over, sliced and diced them all so each track actually contains little snippets of several other songs ... automated mashups ... oh well, could be worse.

---

