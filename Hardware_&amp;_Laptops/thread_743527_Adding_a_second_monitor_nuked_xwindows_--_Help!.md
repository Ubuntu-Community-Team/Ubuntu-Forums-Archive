---
title: "Adding a second monitor nuked xwindows -- Help!"
date: 2008-04-02
forum: Hardware &amp; Laptops
---

### Post by wanorris on 2008-04-02
I installed Gutsy, patched it, and was setting apps up. Everything was running like a champ until I tried to add a second monitor. It wanted to bring it up at 800x600, so I went in and manually set it as a generic flatscreen 1680x1050. After I clicked ok, it said I had to wait until all sessions logged off to change the settings, so I saved everything and logged off. The system then froze when I logged off.

I waited to make sure it wasn't coming back up, then I killed the power and rebooted.

It booted using the external monitor as the primary and came up in some kind of safe mode. It gave me a screen setup, so I went in and tried to set my screen up. It also had a generic (VESA?) driver listed, so I tried to set it up to use the open source NVidia driver.

After that it froze. I may have gone through this one more time, trying to do the same thing.

The net result is that now I can't get it to boot into XWindows at all. The only way I currently know to get the system to boot is to tell GRUB to boot in recovery mode, which gives me a root prompt.

In principle, I expect the answer to be that there are some config files that are borked, and I should be able to fix them y editing them from this root prompt. But I don't know much about configuring X and other graphics stuff, so I'm not sure which config files, and I'm not sure what I need to fix.

Any assistance anyone can provide me will be much appreciate. Thanks!

Andy


System:
  ThinkPad T61p, 2.1GHz Core 2 Duo, 2GB RAM
  NVidia Quadro FX something -- 570M, I think
  1680x1050 onboard LCD

Monitor:
  a "Sceptre" brand 19" flatscreen 1680x1050

Driver:
  whatever Gutsy had installed by default; I haven't installed the binary-only NVidia driver yet.

---

### Post by wanorris on 2008-04-02
I figured it out. In the config dialogs, I switched xorg.conf to use the nv driver instead of the vesa driver. The nv driver implodes with the T61p.

The fix I found was here:

[http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p](http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p)

---

