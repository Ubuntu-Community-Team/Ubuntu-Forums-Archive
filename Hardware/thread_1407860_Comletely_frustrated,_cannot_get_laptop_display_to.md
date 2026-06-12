---
title: "Comletely frustrated, cannot get laptop display to shut down"
date: 2010-02-15
forum: Hardware
---

### Post by MrNatewood on 2010-02-15
Laptop: Dell Studio 1555

Closing the lid doesn't do anything. Display stays fully ON.
Locking the screen only makes it show black, display still on.
Tried with AC and without.

In Preferences->Power Management chose "blank screen" when lid is closed, doesn't work.

Set put display to sleep when inactive for 1 minute. doesn't work.

tried command
gnome-screensaver-command --lock && sleep 1 && xset dpms force off

Works, but screen wakes up after a few seconds no matter what. Not touching it at all. No freaking wind in room. Disconnected USB mouse so no external input device.

Using Karmic 64-bit.

---

### Post by lidex on 2010-02-15
WOL. Wireless running?

---

### Post by MrNatewood on 2010-02-16
Wired is. (Whole point is leaving the laptop on at night for downloads, without leaving the display on)

How can I stop this WOL?

---

