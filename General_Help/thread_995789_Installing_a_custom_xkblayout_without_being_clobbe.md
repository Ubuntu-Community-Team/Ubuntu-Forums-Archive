---
title: "Installing a custom xkb*layout without being clobbered by xkb-data updates?"
date: 2008-11-28
forum: General Help
---

### Post by Yuri Khan on 2008-11-28
How do I install a custom-made xkb layout?

I already know how to create a file in /usr/share/X11/xkb/symbols and what patches to apply to /usr/share/X11/xkb/rules/base, /usr/share/X11/xkb/rules/base.lst and /usr/etc/X11/xkb/base.xml (and for some reason, on my laptop the correct files to modify are evdev.* rather than base.*).

But every so often apt comes and writes a new version of xkb-data all over my setup that I have to reapply the patches. I wonder how can I install a layout without modifying files belonging to that package and also still have xkb-data updates apply to me?

I am using Ubuntu 8.10 and Kubuntu 8.04 if this matters (which it probably shouldn’t).

---

### Post by akaihola on 2009-05-14
Oh, a solution to this would be fantastic. Have you found any clues?

---

### Post by Yuri Khan on 2009-05-14
I asked this same question in my blog at LiveJournal and people have directed me to [this discussion](http://community.livejournal.com/xkbconfig/6179.html).

Also, one reply was “I have an .xkbmap file in my ${HOME} which is fed to 'xkbcomp .xkbmap ${DISPLAY}' in /etc/Xsession.d”.

Meanwhile, in Jaunty xkb_data received an update (addition of typographical characters) which made my modifications unnecessary.

---

