---
title: "&quot;Out of range&quot; black screen solved"
date: 2008-12-17
forum: Hardware
---

### Post by teia on 2008-12-17
YEAAAHHHH!!!!

After about ten giveup's I have finally solved my problem with the black screen containing only the cyan message Out of range when booting for the first time after a fresh install. (Intrepid Ibex).

Tonight I dicided to give it a last try and since my screen and graphics was functioning perfectly in 8.04 I backed up my xorg.conf to one of my partitions and went for it.

As usual the installation went fine, up to the point of the login screen. The the familiar black screen "Out of range" message came as expected.

I then pressed Ctrl + alt + F2. Logged myself in and copied the backed up xorg.conf into the /etc/X11 folder. Then I ran two times around the livingroom table and rebooted the system.

Viola!!

The system booted in low resolution, but it was just a matter of enabeling the nvidia driver and everything was up and running.

Can't say that this is the solution for everyone with the same problem, but it works for me and I am now about to stick a big finger in the eye of everyone that told me it was my hardware that was F****d up.

Blah!!!:guitar::guitar::guitar:


Good luck
brg Teia

---

### Post by jpeddicord on 2008-12-17
Moved to Hardware.

---

