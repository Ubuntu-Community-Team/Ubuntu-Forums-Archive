---
title: "eee 1005HA webcam not working"
date: 2010-05-20
forum: Hardware
---

### Post by JunkYardKid on 2010-05-20
I just put UNE on my eee 1005HA and it doesn't seem to know the webcam is there. any ideas on how to fix this?

---

### Post by tehwalrus on 2010-06-02
Hmm, not sure...

I have the Eee 1005HA too. what version of UNR are you running? karmic or lucid?

I just upgraded from Karmic to Lucid, and I only tried the webcam AFTER the upgrade, so I don't know how it was in K.

now in L, it seems to work fine but dies if you try recording video. it can take stills fine, and the preview works in real time, but recording video stutters and dies, and only seems to update every 10 seconds or so.

As a temp solution I tried seeing if I was missing a kernel module (but as a novice I seem to have broken EVERYthing and causing a kernel panic with the config I chose, so no support for me!) but the health warning says you shouldn't need to recompile the kernel just to get a driver, so I guess it was a bit pointless.

anyone else know of any common webcam problems/solutions in ubuntu, esp in the netbooks?

---

### Post by tehwalrus on 2010-06-03
Just to update what I said here, the kernel panic was due to Lucid's requirement to manually build an initramfs, which is now sorted.

However, having rebuilt the kernel with all possible video input included, this still leaves us with a broken/jumpy webcam for video!

everything else is much faster (now that I've optimised for Atom) but when I try and capture video I get the same problem still.

any answers would be very much appreciated.

---

### Post by tehwalrus on 2010-06-03
further to this, I have got /something/ to work a bit.

* put the resolution down to the absolute minimum
* record sound using an alternative application
* stitch the 2 tracks back together in PiTiVi afterwards.

it just about works; you get a tiny video file that just about syncs up (best to use "space" to stop recording, and then you can sync up the end of the video with that noise and it works ok...)

anyone with ANY time to look at this it would be greatly appreciated...

---

