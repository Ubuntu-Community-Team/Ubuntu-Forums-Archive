---
title: "VisTablet PenPad Has Akward Cursor Movement?"
date: 2013-12-25
forum: Hardware
---

### Post by Espionage724 on 2013-12-25
Lets say I tap the top-left of my tablet, lift the pen, and then tap the bottom-right of the tablet. The expected behavior is for the cursor on-screen to teleport from the top-left to the bottom-right.

Under Ubuntu (and variants), and other distros of Linux (openSUSE and Debian), the cursor moves from top-left to bottom-right; it's a quick movement, but definitely not instantaneous as expected. I can also notice a bit of delay behind the movement also (I only use the tablet for osu! mainly, and any added latency is both noticeable and unwanted).

Under Windows (with and without drivers), the cursor teleports as-expected. Last I recall, SteamOS (being a distro of Linux) also had the cursor teleport (maybe I could grab some info from SteamOS?).

So, I'm wondering what I could do to get the cursor to instantly update to its new location, instead of always moving to the new location? I would really like to get this figured out, but have no idea what to even try at this point.

Other links for reference:
Ubuntu Forums (more specific tablet info): [http://ubuntuforums.org/showthread.php?t=1946486&page=9&p=12874395#post12874395](http://ubuntuforums.org/showthread.php?t=1946486&page=9&p=12874395#post12874395)
SteamOS Forums: [http://steamcommunity.com/groups/steamuniverse/discussions/1/648814738434386345/](http://steamcommunity.com/groups/steamuniverse/discussions/1/648814738434386345/)
openSUSE Forums: [https://forums.opensuse.org/english/get-technical-help-here/hardware/492331-make-graphics-drawing-tablet-update-cursor-location-instantly-instead-moving.html](https://forums.opensuse.org/english/get-technical-help-here/hardware/492331-make-graphics-drawing-tablet-update-cursor-location-instantly-instead-moving.html)
Video of the issue (also showing a Wacom tablet working fine): [https://www.youtube.com/watch?v=NJgLeTG-R5k](https://www.youtube.com/watch?v=NJgLeTG-R5k)

---

### Post by Espionage724 on 2013-12-30
Fixed this problem finally... removing **xserver-xorg-input-wacom** (and it's dependency **xserver-xorg-input-all**), prevents the wacom driver from loading, and allows the tablet to work as-expected. I'm not aware of any adverse reactions from doing so so far.

---

### Post by icanhardly on 2014-01-12
> **Espionage724 said:**
> Fixed this problem finally... removing **xserver-xorg-input-wacom** (and it's dependency **xserver-xorg-input-all**), prevents the wacom driver from loading, and allows the tablet to work as-expected. I'm not aware of any adverse reactions from doing so so far.

for new users' setup what in your experience should be done step by step for identical [**VisTablet 172F:0037**]("http://ubuntuforums.org/showthread.php?t=1946486&p=12874395#post12874395") ?

---

### Post by Espionage724 on 2014-01-12
Type **sudo apt-get remove xserver-xorg-input-wacom** into a Terminal (or use a GUI or something), let it remove that package along with **xserver-xorg-input-all** (those should be the only two packages removed), reboot, and then try the tablet out. I had working input still with both the tablet and a USB mouse, and PS/2 Keyboard, so removing that last package won't nuke all input as it might seem.

I recall seeing some driver thing in a Wacom tablet 50 config somewhere that also mentioned Waltop tablets and what driver to load. I haven't tried it, but perhaps just removing that driver line could also work.

---

