---
title: "X11 SDK for Ubuntu?  Can't find it and need it for device driver config!"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by HaoTian on 2007-03-09
I did a search on the forum for this, and found one other user ([http://www.ubuntuforums.org/showthread.php?t=83540&highlight=xorg+x11+sdk](http://www.ubuntuforums.org/showthread.php?t=83540&highlight=xorg+x11+sdk))  who posted something similar, but his question was never answered and it was from 2005, so I figured maybe I'd post a fresh thread on it.

I'm trying to configure my tablet (like the user in the other thread), a WACOM Graphire Bluetooth.  I've got it connecting to the computer as an HID, and it works great... but now I need to compile the X11 driver (supplied here: [http://cs.ozerki.net/zap/wacom-bt/](http://cs.ozerki.net/zap/wacom-bt/) by Andrew Zabolotny) to get the pressure sensitivity working.  Unfortunately, I need the X11 SDK to do it and like the poster in the previous post, have met with trouble when attempting to find it.  There is no package mentioned in the Synaptic package manager and the only other method I've seen for getting it involves yum, which also doesn't run on Ubuntu due to a python bug.

Does anyone have any suggestions on where I can obtain this?  I'm running 6.10 (Edgy).

For reference, the point I'm stuck at in the guide I'm using (posted above with the driver) is where you are instructed to type:

./bootstrap
./cfg.sh
make

After typing ./bootstrap, I get "./bootstrap: 3: aclocal: not found"

Thanks in advance!

Scott Dellinger

---

