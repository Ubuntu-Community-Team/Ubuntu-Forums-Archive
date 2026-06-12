---
title: "After Upgrade, X won't start"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by PeEllAvaj on 2009-04-26
I upgraded to 9.04 a couple of days ago, and I finally got around to rebooting today.

When the system came back up, it froze at the splash screen, and regardless of what I do, I can't get X to start.

What I have tried so far:
[LIST]
[*]Enter Recovery Mode and check Xorg.0.log (nothing there)
[*]Try resetting all of my xorg.conf settings with (sudo dpkg-reconfigure -phigh xserver-xorg).
[*]Remove and reinstall all xserver related packages (sudo apt-get remove nvidia* xserver*; sudo apt-get install --reinstall kubuntu-dkestop)
[*]Running the "fix broken packages" options from recovery mode.
[*]Make sure to update all packages with apt-get update and apt-get ugprade.
[*]Re-enable ctrl+alt+backspace with DontZap.
[*]I have even tried to run X from the recovery commandline with xstart.  When I do this, my monitors initialize and I get a cursor and a blank screen, but nothing (including ctrl+alt+backspace or ctrl+alt+delete) works or moves.
[/LIST]

I have googled and searched around for the problem and not found anything, so any help or suggestions would be appreciated!

---

### Post by PeEllAvaj on 2009-04-26
X seems to have the same problem when I use the live cd.

I'm a little confused because I have tried both the nvidia and the ubuntu nv drivers, doesn't this mean it isn't a driver issue?  Do I need to go back to 8.10?

I would appreciate any thoughts or recommendations on how to move forward. Is there an easy way to downgrade?

---

### Post by PeEllAvaj on 2009-04-27
I've just received some more confusing results.  It seems I can boot into the live CD as long as I have "acpi=off".  The reason this is confusing is because I have finally gotten back into X on my main installation, but on my main installation the only way to get it to work is to use recovery mode and manually start dbus, acpi, and hal, before attempting to start X.

What is happening, and why won't these services start themselves like they used to?

---

### Post by siyisoy on 2009-04-27
> **PeEllAvaj said:**
> I've just received some more confusing results.  It seems I can boot into the live CD as long as I have "acpi=off".  The reason this is confusing is because I have finally gotten back into X on my main installation, but on my main installation the only way to get it to work is to use recovery mode and manually start dbus, acpi, and hal, before attempting to start X.

What is happening, and why won't these services start themselves like they used to?

did you see this?

[http://ubuntuforums.org/showthread.php?p=7140198](http://ubuntuforums.org/showthread.php?p=7140198)

---

