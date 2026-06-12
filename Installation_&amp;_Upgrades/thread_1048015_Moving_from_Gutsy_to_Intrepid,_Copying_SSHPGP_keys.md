---
title: "Moving from Gutsy to Intrepid, Copying SSH/PGP keys"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by jonthysell on 2009-01-23
I am currently running Gutsy 64bit on my desktop, and just bought a laptop that I'm going to install Intrepid 32bit on, and use as my primary computer. (I'm going to re-purpose the desktop as a media server, maybe).

Is it possible (recommended?) to just copy the home folder contents blindly, or should I only selectively copy the various hidden directories?

I can live with losing most of program and gnome configs (nothing special), but in particular I'm concerned with GnuPGP and SSH keys, and any Bazaar branches.

I assume it's recommended to create new pub/sec SSH keys for a new computer (and just trash the old ones since that machine will be reformatted), but can I just copy the .gnupg folder to the new machine? And the branches?

Thanks.

---

### Post by graingert on 2009-01-23
It's probably safe, but make sure you copy the files when you are using a live environment so that the files are not being edited at the time of copying

---

