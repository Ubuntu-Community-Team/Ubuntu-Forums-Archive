---
title: "[SOLVED] Intermittent hardware recognition"
date: 2008-09-05
forum: Hardware
---

### Post by philandstuff on 2008-09-05
Hi there,

I've installed ubuntu on a toshiba satellite pro L300 ([installation log here]("http://www.doc.ic.ac.uk/~pgp/personal/logs/ubuntu-toshiba-satellite-pro-l300-20080813.html")) but I have irritating intermittent problems with hardware.

The three aspects affected particularly are power management, wired networking, and sound.

Power management: I've edited /etc/laptop-mode/laptop-mode.conf to my liking for controlling HDD settings (dirty_ratio, dirty_background_ratio and all that) while for backlight brightness I'm using gnome-power-manager and editing the settings with gconf-editor. Most times I boot up everything works fine, but sometimes it just doesn't respond to such things as putting the power cable in or taking it out. Right now, if I take the cable out or put it in, /proc/sys/vm/{laptop_mode,dirty_ratio,dirty_background_ratio} don't change where normally they would. laptop_mode is stuck on 2 (my setting for off ac power). The icon in the notification area for gnome-power-manager does eventually respond to a change in cable status but it takes longer than it does when things seem to be working. Right now it takes ~10 seconds rather than ~2. However, even though it changes the icon, it doesn't change the LCD backlight brightness - brightness is 100% (on ac power setting). Furthermore, the laptop comes with function keys for changing the brightness which normally work and currently don't: I press <fn>-F6 (reduce brightness) or <fn>-F7 (increase brightness) and nothing happens, where normally the brightness control would appear on the screen the way the volume control does.

Wired networking: Normally this is fine, but sometimes when I boot up (and I'm not entirely sure at the moment if these times are the same times as when the power management breaks) the computer "detects" a wired network even though there's no cable plugged in. This is irritating because it causes the wireless network not to autoconnect to my known networks. The detected wired network means that instead of internet hosts and IP addresses being unreachable to ping or firefox or whatever, they wait for a timeout instead.

Sound: I think I'll leave this for the moment, because it's more reliable than the other two. I don't think it's correlated.

The problems sometimes appear after resume-from-hibernate, even if before hibernate things were working.

Has anyone any ideas?

---

### Post by philandstuff on 2008-10-18
Partial solution of ethernet problem: it seems that r8169 is just plain buggy when used with rtl8101e/rtl8102e hardware. Seemingly there is an official Realtek driver available, but I don't use the wired network enough to justify messing around with that.

More details: [http://ubuntuforums.org/showthread.php?t=843398](http://ubuntuforums.org/showthread.php?t=843398)

Still not much further with power management though.

---

