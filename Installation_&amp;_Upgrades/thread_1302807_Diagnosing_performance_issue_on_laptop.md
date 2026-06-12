---
title: "Diagnosing performance issue on laptop"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by chathamsq on 2009-10-27
I'm experiencing unexpectedly slow general performance on an older laptop & would greatly appreciate help in diagnosing.

I had previously been running a standard Hardy install with the gnome desktop & acceptable performance.  I decided to wipe the slate clean & did a new install with the Jaunty Minimal CD and OpenBox window manager.  I was shocked to find substantially *worse* performance than I was getting on Hardy with gnome.

The slow performance seems pervasive, but here are some examples:
[LIST]
[*]slow application switching in Openbox
[*]sluggish usability in various applications, including thunar, swiftweasel, keepassx
[*]delays in typed keys appearing on the screen in some apps
[*]also - I could be wrong about this - but it seems like password verification (on login and sudo commands) is slow (6 sec) at the CLI, even with X not running
[/LIST]

**System:** IBM ThinkPad X31... Intel Pentium M 1400MHz... 1GB RAM... ATI Radeon Mobility M6... Ubuntu 9.04 Jaunty 32-bit Minimal... Openbox WM

Here's what I've looked at:
[LIST]
[*][FONT="Courier New"]top [/FONT]shows CPU utilization 1% and memory 30% at idle.
[*]When I switch apps, resize windows, or perform certain application actions, Xorg jumps to 50%-80% CPU.
[*]I've checked dmseg & /var/log/syslog and don't see anything obviously wrong, but most of the entries don't mean much to me
[/LIST]

I made a couple other changes on the new install, which may or may not have anything to do with the problem:
[LIST]
[*]ext4 file system (previously ext3)
[*]encrypted home directory
[/LIST]

Appreciate any ideas or guidance on how to diagnose.

---

### Post by chathamsq on 2009-11-06
Still don't know what caused this, but the upgrade to Karmic solved it 100%.

---

