---
title: "Ubuntu on an mac mini won't show grub nor boot when TV is connected."
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by jav on 2009-03-13
Hi Ubuntu forums.

I'm trying to upgrade my mac mini (intel cpu) to Ubuntu (8.10 64bit).

My intention is to have it as a HTPC. However I've run into trouble.

When I boot the mac with a DVI->VGA converter and a 'normal' pc-screen connected, every thing works fine. The machine boots, gnome starts and ssh-server autostarts (as I've configured it to).

However, when I connect my plasma-TV via a DVI->HDMI cable, and boot the machine I get no picture at all.
If I keep alt pressed, I do get the apple bootloader menu (that part works fine). 
But if I boot into ubuntu, I just get a black screen, no grub, no nothing.
And if I wait a reasonable time (compared to when the LCD panel is connected), i can still not SSH to the machine.
I don't know how to check the previous boots logs, so I don't know how far it does boot or when it stops.

I've tried different screen settings in grub, with no success.

Also, if I do boot with the LCD panel, disconnect it and connect the PlasmaTV I do get a picture (with overscan, but that is a later problem).

I have tested some resolutions in that mode which work fine, and then tried to set grub to use the very same resolution ( 1024*768 ), but with no success.

Can some one help me? How do I continue to debug this problem?
How can I find out where the bootprocess fails if I don't have a connected screen and have no console access?

// Javier

---

### Post by pycage on 2009-07-18
I too am using a crApple Mac Mini for a HTPC with Ubuntu. It worked fine until the day I purchased an expensive DVI-HDMI cable for connecting the mini to the TV.
The bootcamp firmware tries to emulate a BIOS so that non-OS-X systems can boot. This BIOS emulation is buggy and hangs when it tries to detect a monitor. You get the same effect when you try to boot the mini without any monitor attached.

As a workaround I have the mini connected to the TV via VGA cable when switching it on, and replace the DVI-VGA adapter with the DVI-HDMI cable when the grub bootloader appears. This is tedious, but works fine.

Alternatively you could get a resistor and put it into the VGA connector as described here: [http://www.ilikejam.org/blog/unix/linux-mac-mini.html](http://www.ilikejam.org/blog/unix/linux-mac-mini.html)

---

