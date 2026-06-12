---
title: "LG 32UN650 Monitor blurry - subpixel problem?"
date: 2021-12-08
forum: Hardware
---

### Post by yourjunkhere14 on 2021-12-08
Hello All,

Yesterday I got a LG 32UN650 monitor and attached it to my laptop running Ubuntu 20.04LTS.  I noticed that some of the text, especially red bold text (things like grep bold matching text in red) are blurry on the LG monitor.  When I drag the window back to the laptop monitor it looks great!  I'm guess I had sub-pixel matching problem.

I've tried adjusting the sub-pixel and font antialiasing settings in Gnome Tweaks => Fonts, using dconf-editor (org.gnome.settings-daemon.plugins.xsettings/rgba-order) and adjusting which files are selected in /etc/fonts/conf.d/. but even with a restart it makes no difference on either monitor (laptop screen looks great - LG monitor looks blurry).

I've exhausted my search abilities and not found any solutions.  Questions:

1) How do I adjust the sub-pixel settings and have them actually work?
2) How do I tell what settings X is using on which monitor?
3) Is there a different solution I should be trying?
4) Should i return the monitor and try a different one?

Thanks in advance!

Sincerely,
Stephen

---

