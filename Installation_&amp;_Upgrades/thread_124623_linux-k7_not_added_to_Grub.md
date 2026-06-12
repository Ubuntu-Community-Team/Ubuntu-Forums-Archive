---
title: "linux-k7 not added to Grub"
date: 2006-02-01
forum: Installation &amp; Upgrades
---

### Post by rmaple on 2006-02-01
Hello,
   I just finished a clean install of 32bit Breezy on a new Athlon64 machine,   Once everything was up and running, I used Synaptic to install the linux-k7 kernel packages.  Everything seemed to proceed without difficulty, but when I rebooted, the 386 kernel came up (confirmed with uname -r).  I rebooted again and went into the grub menu, and the k7 kernel was not even listed.  This surprised me since I did the same thing a few weeks ago on a different machine, and the k7 kernel was automatically added and made the default.  Should I manually add the k7 kernel to menu.lst, or is there a utility that I should run (that should have run) to rebuilid the grub config?

Thank you,

Ray

---

### Post by o_fortuna on 2006-02-01
[QUOTE=rmaple]Hello,
   I just finished a clean install of 32bit Breezy on a new Athlon64 machine,   Once everything was up and running, I used Synaptic to install the linux-k7 kernel packages.  Everything seemed to proceed without difficulty, but when I rebooted, the 386 kernel came up (confirmed with uname -r).  I rebooted again and went into the grub menu, and the k7 kernel was not even listed.  This surprised me since I did the same thing a few weeks ago on a different machine, and the k7 kernel was automatically added and made the default.  Should I manually add the k7 kernel to menu.lst, or is there a utility that I should run (that should have run) to rebuilid the grub config?

Thank you,

Ray[/QUOTE]
Try this in a terminal (Applications-->Accessories-->Terminal):
```
sudo update-grub
```
This will search for the kernels installed, and add k7 to the list, hopefully. Open the file in /boot/grub/menu.lst to make sure that it's there.

---

### Post by rmaple on 2006-02-01
Thanks - that would have done the trick.  Unfortunately, the reason it wasn't updated in the first place is that I screwed up and made my /boot partition way too small.  (Its been a long time since I bothered to manually partition - I remember when 10MB was more than enough for several kernels)  I made it 15MB, and it hit 100% with just 2 kernels.  At least the installation is painless.

Thanks again,

Ray

---

