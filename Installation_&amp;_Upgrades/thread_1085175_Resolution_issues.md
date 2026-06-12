---
title: "Resolution issues"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by wrose51106 on 2009-03-02
Long time computer tech, first time outside the "box". Rather new to Linux so bare with me:)

Booting off 8.10 CD I get almost into the GUI but my machine locks but my mouse is fully functional.

Booting off 8.10 CD with "Safe Graphics" I am good to go, in fact I am typing this from there:)

Installing 8.10 CD works great, reboot and GUI starts then goes black.

I assume because the on-board video chipset has a max resolution of 1280x1024, and the display I am using defaults to 1680x1050. I am guessing I need to specify my resolution but do not see where to do it during install.

I would appreciate any help you can give me.

-Bill

---

### Post by utnubuuser on 2009-03-02
Hi Bill

Lots of "black screen" threads lately.  --and yes, mostly in reference to that resolution range.

If you post a bit more info about your system, you're more likely to get decent feedback/help.

Open a terminal (Applications>>Accessories>>Terminal) and post the output from> dmesgand > lspci

Also, if you google: "1680x1050 resolution ubuntu", you'll likely find several threads addressing the same issue.

---

### Post by wrose51106 on 2009-03-06
Thank you for the reply, I figured it out later that night, I hit "esc" at the grub loader and after the oot file I added vga=1280x1024. It started to load and tossed an error back of not a valid resolution, but it did give me the option of choosing a different one. I selected it, updated the system and rebooted and it all works fine now.

As I was going through the updates I did notice driver updates for Nvidia, ATI and Intel graphics. I am assuming that resolved the issue and or the boot loader edited itself correctly. Thank you for the help!

-Bill

---

