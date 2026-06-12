---
title: "can't install 8.10 on intel 80gb SSD"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by neurotopia on 2009-02-11
hi.  i've googled and searched these forums, to no avail.  i just bought an intel x25-m 80gb SSD and cannot install ubuntu 8.10.  ubuntu simply does not detect the SSD, at all.  this is the case on both my desktop (nvidia 680i chipset) and my laptop (intel 965g chipset)

does anyone have any suggestions what i can do to install ubuntu on my SSD?  it is my goal to dual boot xp and ubuntu.  xp installs fine.  i even tried installing ubuntu INSIDE xp, but when i boot into ubuntu i get an error and it drops me to a text screen with some kind of ramfs prompt.  

i've only been using ubuntu for a few months and i've never had a problem like this before.

---

### Post by rusyear04 on 2009-02-17
hi there!

i'm not a real expert, but as far as i've figured you can change the SSD-option in BIOS.
if you change it to "compatible" the system should detect it...

hope it helps ;)

best regards!

---

### Post by Forlornity on 2009-02-17
Generally changing drives to compatibility mode in the BIOS is a good idea for installations, I'd also recommend using ext2 rather than ext3 for the sake of your SSD, as a journaling filesystem writes a lot more often, shortening the life of an SSD.

---

### Post by neurotopia on 2009-02-17
thanks!  yeah, compatibility mode did the trick.  then once i updated i could go back in and change it.

---

### Post by jakethecake on 2009-03-10
Got a Intel X25-E 32GB drive yesterday. Ubuntu 8.10/9.04 Alpha does not detect it. No output from dmesg or fdisk.

I've got the same nVidia 680i SLI motherboard, but I can't find BIOS option to tweak. 
If I boot Windows XP, it will detect the SSD, no problems. :cry:

---

