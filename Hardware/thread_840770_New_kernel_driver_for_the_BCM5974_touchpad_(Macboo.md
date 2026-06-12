---
title: "New kernel driver for the BCM5974 touchpad (Macbook Air, Penryn)"
date: 2008-06-25
forum: Hardware
---

### Post by kosumi68 on 2008-06-25
This has already been posted in the Apple forum ([http://ubuntuforums.org/showthread.php?t=840040](http://ubuntuforums.org/showthread.php?t=840040)), but I thought it might suit here too:

I just completed the first version of a new kernel driver (bcm5974) for the multitouch trackpad on the Macbook Air. It is prepared to also work with the new Macbook Pro Penryn.

It replaces the appletouch driver for these machines, and it works well with the synaptics driver, thus integrating smoothly with the ubuntu desktop.

It can be downloaded here: [http://web.comhem.se/rydberg/Bits/](http://web.comhem.se/rydberg/Bits/)

Both source code and a binary for the 2.6.24-19-generic is available. A patch has been submitted to kernel.org, so hopefully we will have support for the new macbooks in the not-so distant future. :)

Cheers!

---

