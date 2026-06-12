---
title: "hardy really long boot"
date: 2008-07-11
forum: General Help
---

### Post by mewho on 2008-07-11
hi all,
i just got a fujitsu amilo xi2428...i wiped the hdd of stupid vista and installed ubuntu.  the install would hang until i moved the mouse, and then things would speed up.  after a few seconds, the install would hang again, so i had to just keep on moving the mouse throughout the entire install. after boot, i had the same problem in gnome.  someone in the forums suggested i try text based installer, so i did, but had the same problem during the install, but in gnome the problem seemed to resolve itself.  my issue now is that when booting, the computer hangs until i press enter at a few different points, then things move smoothly.  i installed bootchart to see what's going on, but can't figure out why it is happening. i know it hangs on loading restricted drivers as well as a few more places.  the only restricted driver listed in hardware drivers is the nvidia driver for the geforce 8600m gs, but i used envy to install driver, so restricted driver is not in use.  the computer also has a few hardware devices that are not recognized such as the webcam (ALi webcam m5602) and media remote control (ite8709) as well as an e-sata and firewire port that i have not tested.  any help with my boot problems would be much appreciated, as i am pulling my hair out.  if any logs are needed, i can post.  thanks.
mewho

bootchart report:

[[IMG]http://s2d2.turboimagehost.com/t/508179_hardy-20080711-2.png[/IMG]](http://www.turboimagehost.com/p/508179/hardy-20080711-2.png.html)

---

### Post by DagMan on 2008-07-12
2 small suggestions

try hitting alt-f4 during the splash screen to see what's happening at boot time a bit more.

You can use a prgram in the repos called bum to possibly disable the restricted module loading at boot, and if not then sysv-rc-conf which is explained here how to use [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

