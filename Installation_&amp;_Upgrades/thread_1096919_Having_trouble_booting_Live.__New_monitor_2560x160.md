---
title: "Having trouble booting Live.  New monitor 2560x1600"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by Urinemachine on 2009-03-15
Hey all,

I have run Ubuntu 8.10 for a long time on this PC.  I formatted last night to reload Vista and left a 50GB partition for Ubuntu.  I threw the live CD in to boot and install, but I don't boot up!  I have a new monitor (30" LG) that runs 2560x1600 that uses a DVI-D cable on my Nvidia 8800 GTX and that's the only hardware change I can think of.  The video card is the same, cpu, ram, mothe.... actually the motherboard is new too I went from a Evga 680i to an Evga 780i, but still.

I think I am having issues with the monitor or something because I can't see anything.  I see the Ubuntu with the progress bar thing, and then nothing.  If I hit CTRL+ALT+BCKSPACE I can see where it was at (waiting for battery or something), but thats it.

Any ideas?  I'd like to get Ubuntu on this machine!

Thanks!

---

### Post by wpshooter on 2009-03-15
A suggestion.

If you still have your "old" monitor which possibly is not 2560 x 1600 resolution try installing Ubuntu to the machine you are referring to with the old monitor.  That way if it installs you know that it is a problem with Ubuntu working with your new monitor.

If it will install with the old monitor, you might want to switch back to the new monitor and then try the installation with the ALTERNATE (texted based) CD version of Ubuntu if you have not already tried that.

---

### Post by Urinemachine on 2009-03-15
> **wpshooter said:**
> A suggestion.

If you still have your "old" monitor which possibly is not 2560 x 1600 resolution try installing Ubuntu to the machine you are referring to with the old monitor.  That way if it installs you know that it is a problem with Ubuntu working with your new monitor.

If it will install with the old monitor, you might want to switch back to the new monitor and then try the installation with the ALTERNATE (texted based) CD version of Ubuntu if you have not already tried that.

Hrmmm - I don't actually have it but I think I can find something to plug in.  Worth a shot to see if its the new motherboard or new monitor.

---

### Post by Urinemachine on 2009-03-15
Fixed!

Found a CRT monitor and plugged it in w/ a DVI-VGA adapter, installed Ubuntu 8.10 off of x64 CD (non-alternate, just the std. CD).  Got into X and let it detect that nvidia restricted drivers are available - installed those.  Shutdown, swapped the 30" display back in, and woo!  Rockin' and rollin'!

ubuntu at 2560x1600.... its a thing of beauty.

---

