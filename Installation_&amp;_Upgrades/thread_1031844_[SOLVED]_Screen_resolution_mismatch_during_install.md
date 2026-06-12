---
title: "[SOLVED] Screen resolution mismatch during install"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by pmulgaonkar on 2009-01-05
I am trying to install 8.10 on a computer that is connected to a Kogi 17 inch monitor. There are multiple posts on this finicky monitor and how it cannot tolerate a screen resolution of greater than 1024x768. My problem is that when I boot from a live CD, right after the ubuntu loading screen with the horizontal bouncing bar, the monitor goes black and I can no longer interact with the system.

In the past, I have had similar problems installing 8.04, but in that install, repeatedly hitting CTRL-ALT-PLUS got the screen back into a mode that I could see and interact with to complete the installation process. That no longer seems to work in 8.10. Also other tips such as vga=xxx on the options line during booting, and going to the interactive grub menu by hitting escape and then typing live vga=xxx doesnt seem to do the trick. The resolution I need on the vga=xxx line seems to be 791, but I get a "no such resolution" error message when I try it. 

Any hints?

Thanks --prasanna

---

### Post by pmulgaonkar on 2009-01-06
No hints from anyone? Help!

---

### Post by pmulgaonkar on 2009-01-09
OK. I solved it after much googling...

When the screen goes blank, hit CTRL-F1. This puts you into the command line window. 

do: sudo nano /etc/X11/xorg.conf

At the bottom of the "Screen" section, add:
SubSection "Display"
     Depth  24
     Modes  "1024x768"
EndSubSection

Save (control-X, y)

Return to the GDM window with Ctrl-F7
Restart the X server with Ctrl-backspace

And then you can see the login screen.

---

