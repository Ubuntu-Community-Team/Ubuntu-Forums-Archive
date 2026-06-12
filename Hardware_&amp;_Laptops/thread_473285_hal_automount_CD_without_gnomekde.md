---
title: "hal automount CD without gnome/kde"
date: 2007-06-13
forum: Hardware &amp; Laptops
---

### Post by deviantintegral on 2007-06-13
I've set up a custom xsession for Elisa on my media centre. The only problem is that CD's/DVD's aren't automounted. What process(es) do I need to run for automount to work?

Thanks,
--Andrew

---

### Post by DagMan on 2007-06-14
ivman and you may have to have it run at startup by the user the session runs under but I'm not sure, I haven't used it on ubuntu and don't know how it configures itself on install.

gnome-volume-manager will run in a non-gnome environment and I think it needs to be started up by the user the session runs under.

I'de take a look at what the dependancies are for both packages and then decide based on that.  Maybe it's worth looking into if both unmount and eject the CD when the button is pushed as well.

---

