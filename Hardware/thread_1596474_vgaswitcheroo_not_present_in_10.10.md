---
title: "vgaswitcheroo not present in 10.10"
date: 2010-10-14
forum: Hardware
---

### Post by gjamdad on 2010-10-14
I just upgraded to 10.10 on the understanding that this would provide vgaswitcheroo, as stated in a number of forum posts. There is no sign of it. Should it be there? 

I am hoping to finally turn on the nvida graphics in my ACER Aspire 5935G. 

By the way after the upgrade I had to remove the nvidia proprietary driver which had been installed, but provided no glx.

---

### Post by Cutler on 2010-11-10
Same problem here. I even tried to install latest kernel which is 2.6.37 from ppa and still nothing in /sys/kernel/debug/vga....... , I already googled a little and found some help at Gentoo pages here [http://en.gentoo-wiki.com/wiki/Vga_switcheroo](http://en.gentoo-wiki.com/wiki/Vga_switcheroo). Of course it requires kernel compile and enabling vgaswitcheroo option. If I'll be desperate enough I will compile my own kernel and try it. 

I also tried the Ubuntu Control Center, more info can be found here [http://sites.google.com/site/ubuntucontrolcenter/](http://sites.google.com/site/ubuntucontrolcenter/) and here [http://code.google.com/p/ucc/](http://code.google.com/p/ucc/) , unfortunately I wasn't able to switch graphic card at all. Respectively I managed to switch rendering from dedicated card to integrated, but it didn't power off the dedicated one. Battery was running low still very quickly:/

Then I realized that UCC is only GUI for vga_switcheroo, so when it's not present, no success.

---

### Post by shaslinger on 2010-11-29
Same problem here, .../vgaswitcheroo missing for a GForce GT 355M.

---

### Post by malsmith3044 on 2011-01-13
Same problem for me on Dell XPS L401X with 10.10 64-bit

Has anyone sort this out yet?

---

### Post by Ondrejicek on 2011-01-13
I didn't try this on Ubuntu, but it may help:

```
mount -t debugfs none /sys/kernel/debug
```

After running that command, I can see /sys/kernel/debug/vgaswitcheroo/switch

---

### Post by gjamdad on 2011-01-13
That's not it, /sys/kernel/debug is mounted ok, there just isn't any mention of vgaswitcheroo.

---

### Post by oldskool on 2011-01-15
Looking for a solution to this too

---

### Post by FelixII on 2011-01-23
The module disappears when I install the proprietary radeon driver. It shows up again when I uninstall it.

---

