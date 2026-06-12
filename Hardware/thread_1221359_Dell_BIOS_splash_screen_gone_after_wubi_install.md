---
title: "Dell BIOS splash screen gone after wubi install"
date: 2009-07-23
forum: Hardware
---

### Post by jrcraft on 2009-07-23
I installed Xubuntu via Wubi on my old Dell Inspiron 8200 with GeForce 440 Go video. GUI would not work and I had to toggle into terminal to log in. I had to edit the xorg.conf to add DFP=0 and wound up being able to boot into Windows or Xubuntu fine after that. Problem is that my BIOS splashscreen is now gone and the Windows bootloader doesn't appear on screen. I have to select the operating system "blind" and guess which one will actually start. Pressing F2 when the machine starts up won't display the BIOS settings, either, which is VERY concerning.

I have since uninstalled Wubi/Xubuntu and removed the entry from the bootloader, but I still have the same problem. Any suggestions besides a full restore?

---

