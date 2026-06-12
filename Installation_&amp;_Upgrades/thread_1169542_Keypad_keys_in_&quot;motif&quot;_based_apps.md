---
title: "Keypad keys in &quot;motif&quot; based apps"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by edadasiewicz on 2009-05-25
I have clean installations of 9.04 on a laptop (hp zd7000A) and several desktops (Dell and Monarch) and in all cases I am having problems with the positioning keys (arrows, scroll, del, ...) in the keypad section, but only in "motif" based apps (e.g. nedit, ddd).  This problem does not occur in non-motif based apps and did not occur in 8.10.  The work around seems to be to capture "xmodmap -pke" output to a file, edit all KP_ positioning keysyms to remove the KP_ (e.g. KP_Home changes to Home) and then merge the file back in with xmodmap.  I have also noticed the same behavior if I install a version of nedit that is statically linked with motif even after removing lesstif2.  Any ideas?

---

