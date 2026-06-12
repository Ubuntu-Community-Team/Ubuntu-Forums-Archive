---
title: "Inspiron 2600 Intel driver"
date: 2009-12-30
forum: Hardware
---

### Post by kcghost on 2009-12-30
Hello, I am trying to set up Ubuntu 9.10 on an Inspiron 2600 laptop. I could not use the standard installation due to graphical problems (which I am now experiencing again) - I used the alternate install with acpi off. Xorg only works with vesa drivers. The "intel" driver gives a white screen. Researching I found many are having these types of problems with these drivers, so I tried some fixes, with these results:

intel : white screen
intel(2.4) : "no valid FB address" error
i810(2.4) : "no device" error
intel(patched fix "intel driver fix.tar.gz") : could not install properly due to xserver-xorg-core conflicts with xserver-xorg-video-4 that is provided by xserver-xorg-video-intel.
I forced the install anyway and X would not start with intel driver.

Has anyone come out with an updated fix to this problem? This is my mothers laptop and I just convinced her to try out linux...so its either this works or XP. (Sweet jesus no!) Any help will be greatly appreciated.

BTW, if I can get drivers that work I might switch distros anyway (but use the same drivers of course) - any recommendations for a very lightweight yet easy to use distro that might run well on this laptop (not much memory). Xubuntu is abit more lightweight ,right?

---

