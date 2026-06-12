---
title: "Dual-boot always boots netbook remix in text-mode until login"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by soumya92 on 2009-09-25
I have set-up Windows 7 and Ubuntu Netbook Remix to dual boot using a technique described in some other forum which involves the use of one tiny partition ONLY for grub.

The GRUB is working fine, and boots both OSes flawlessly. However, there is a minor annoyance, namely that Netbook Remix always boots in text mode, that is, the progressbar is not displayed. How can I get the progressbar to display while booting?

---

### Post by clonne4crw on 2009-09-25
By progress bar, you mean the Uslpash boot splash engine?

Try installing sysv-rc-conf, as tool that controls what services and other things get loaded and when:
```

# apt-get install sysv-rc-conf

# sysv-rc-conf

```

Arrow keys to navigate, Space to select, q to quit

Look for Usplash, and ensure that it is enabled in the same runlevels that GDM is enabled. I couldn't tell you which ones those are right now.

---

### Post by soumya92 on 2009-09-26
I mean the splash screen that I see when I boot Ubuntu from the live USB disk.
The one with Ubuntu, and a progressbar just beneath it. How do I enable that screen instead of the text-based booting progress that I see when I start up Ubuntu?

---

### Post by rreese6 on 2009-09-26
can't you just edit menu.lst and on the kernel line put "quiet splash"
at the end of the line.

you can test that by hitting "e" in the grub menu. highlight the kernel line and hit "e" again. add "quiet splash" then enter
then hit "b" to boot
if that doesn't work you could try "splash=enable" or "splash=1"

just  a thought

---

### Post by clonne4crw on 2009-09-26
> **rreese6 said:**
> can't you just edit menu.lst and on the kernel line put "quiet splash" at the end of the line.

Yes, you can, and that's worth a try as well, assuming that the menu.1st file hasn't been messed with before.

---

