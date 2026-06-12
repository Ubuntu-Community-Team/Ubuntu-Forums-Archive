---
title: "[SOLVED] Kubuntu 8.10 amd64 live cd"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by bdjohnso on 2008-12-29
I just downloaded the iso of Kubuntu 8.10 64bit and wanted to test it using the Live CD. The MD5 checked out, so I burned the disc and booted from it.
 
My screen shows the Kubuntu logo with the load bar moving back and forth, and then after a couple of minutes, it displays a mostly black screen with my mouse cursor on it. (By mostly black, I mean that a small number of pixels, organized in diagonal strips, are visible, but the entire cursor is there.) I can't see anything to change any settings, so I have to do a hard reset. I've tried booting a few times, but it's always the same.

Anyway, I really don't know what to do. I've not found anyone else experiencing similar problems either. I have Ubuntu 8.10 64bit running well on my machine, so I don't understand why Kubuntu won't cooperate.

My only guess is a video driver (my laptop uses nVidia Go 7400), but I wouldn't know how to fix that even if it was the problem.

I'm somewhat green, so be forgiving; and thanks in advance.

---

### Post by kunixos on 2008-12-29
This is my least favorite part of LiveCDs, so I totally understand your frustration.

You have to disable practically all the auto-settings that attempt to load when you start a LiveCD to ensure a propper boot across all systems. Adding boot parameters to your Grub menu (just edit the line that says /root ....) like ```
noacpi
``` will most likely cause all of your troubles to go away. Check for more ways to disable pesky boot parameters if you are still having problems.

Let me know how this works!

---

### Post by bdjohnso on 2008-12-29
noacpi solved my problem. Thanks for the help!

---

