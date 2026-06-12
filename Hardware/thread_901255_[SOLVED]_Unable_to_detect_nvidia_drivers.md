---
title: "[SOLVED] Unable to detect nvidia drivers"
date: 2008-08-26
forum: Hardware
---

### Post by malachi1990 on 2008-08-26
After the most recent kernel updates (8-25-2008), I was unable to use my nvidia card. Prolly related, I am unable to detect the proprietary drivers on my system, or any need of them.

I ran the recovery mode to fix a problem with the X-server, which allows me to change my screen resolution, but doesn't allow me to detect proprietary drivers.

I also tried downloading different drivers through Synaptic, as nothing I did with the online driver worked (tried aptitude (then I realized the idiocy of this), and sudo <driver>, and tried to alien it, among other things).

Any help would be appreciated.

---

### Post by chrisdeckard on 2008-08-26
It appears that new NVidia packages built against the new kernel aren't out yet.  I too noticed the kernel update was available.  You are kinda stuck without them until they release the new packages.  Not sure why they can't get everything out all at once.

In the future, don't update to the newest version until you also see your NVidia packages will get updated at the same time.

If you really need it back, do a search for going back to a previous kernel package.

-Chris

---

### Post by malachi1990 on 2008-08-26
Thanks for that bit of info, but apparently an older driver will work, but you have to create the module for the driver via sudo <driver> in the CLI.

When I say CLI I mean disable gdm/whatever else you use and go from there.

---

### Post by chrisdeckard on 2008-08-26
You can do that as well.  I didn't want to suggest you go and build the module on your own as I didn't know your experience.  Glad you got it working though.

-Chris

---

