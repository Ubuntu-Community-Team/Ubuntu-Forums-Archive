---
title: "Toshiba satellite P105-S6147 installation issues"
date: 2007-04-05
forum: Hardware &amp; Laptops
---

### Post by koenig on 2007-04-05
hey everyone, i just recently got a Toshiba p105-s6147 laptop and i tried installing ubuntu and ran into a few problems.

when trying to boot the GUI i get a cannot start Xserver error message.
i searched around and tried reconfiguring the xserver with

sudo dpkg-reconfigure xserver-xorg

...followed through the process as accurate as possible because it couldn't auto detect my video card (which is a intel945 gm based accelerator)

then i typed in 

sudo /etc/init.d/gdm start

and get (something like this)

Starting GNOME manager...                    [FAILED]


so. what to do? any ideas?
ive tried pressing CTRL + ALT + F7 to go into the gui mode after i reconfigured xserver but i get a messege saying "xserver is not configured properly. reconfigure and restard GDM."

if you need any clarification or if i'm leaving something out just let me know =)
thanks.

---

