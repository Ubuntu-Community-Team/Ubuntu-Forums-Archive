---
title: "New Notebook - Can I use my SSD HD without Reinstall"
date: 2009-08-13
forum: Hardware
---

### Post by sml on 2009-08-13
I have a relatively new notebook with basically current specs (Intel GM45 chipset etc) with a nice SSD HD running Ubuntu.

I have upgraded my notebook to a similar but slightly higher spec notebook - again with an Intel chipset.

Can I drop the SSD HD into the new notebook - without having to reinstall Ubuntu?

---

### Post by PatrickVogeli on 2009-08-13
you should be able to do that, yes. Just mount your SSD in place and boot, you may have troubles with the graphics driver, if the card is different (intel vs nvidia vs ati), but it should be easy to fix, I think by removing the driver line in xorg.conf or putting in the right driver.

The best you can do is just try it, see what happens and, if it doesn't work, report here and ask for help.

---

### Post by sml on 2009-08-13
:)

it actually has the same onboard graphics ... 4500MHD .. so the intel xf86 driver should be ok hopefully.

the only difference is really the resolution 16:9 vs 16:10 ... but i think xorg is using hal to grab the details for the xorg config, so i think it should be ok (at least on my archlinux install I never used an xorg.conf.)

---

