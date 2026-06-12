---
title: "Switching from proprietary nvidia driver to nv: fonts become too big"
date: 2008-05-22
forum: Hardware
---

### Post by sanguini on 2008-05-22
Hello!

Sorry if I have chosen the wrong forum for discussing this problem, - I'm newcomer on Ubuntuforums.org. I've tried to search but it seems that no one have the same problem :( If I am wrong, please, give me a link to corresponding discussions.

I'm working on Xubuntu 8.04 with proprietary NVidia driver 169.12. But sometimes I need to load X.org with standard 'nv' driver. I have two xorg.conf files, differing in only one line - that, where video driver is specified. In base case this driver is "nvidia", in special case it's "nv".

X.org loads in both cases, but when driver is "nv", some fonts, that are used in Xfce interface (window titles, menus, button titles, etc) become very-very big - about 100 pt. This does not allow to work at all - I cannot even load the settings panel to see what font sizes are used! At the same time fonts in, e.g., xterm, xfontsel, xvidtune and any other base X.org program are normal-sized. Only interface fonts are big.
If I switch back to "nvidia" driver, everything's OK.

I've tried to locate the problem, but the only thing, I've found is that if I remove almost all fonts from /usr/share/fonts, then Xfce interface loads normally. But in this case I can't use the big set of fonts I have, moreover, symbols from my national alphabet practically cannot be read normally. Finally, it's not a good solution - simply to remove fonts.

Fonts sizes that are stored in Xfce settings files (somewhere in ~/.config/xfce4*) are reasonable: about 12 pt.  But in case of "nv" driver these sizes does not affect what is shown on the screen.

This problem concerns not only Xubuntu 8.04, but 7.10 too - I have it for several months already.

As far as I remember, when I had just installed Xubuntu (it was 7.04 probably) , the driver in xorg.conf was "nv" and at that time fonts were normal-sized. Then I switched to proprietary "nvidia", and everything was OK too. But now I can't switch back.

Where can be the problem here?

Thank you for your attention and help!

---

