---
title: "CF/IDE &amp; Journalled Filesystems"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by ACSial on 2009-04-24
I'm not sure about where to put this, but the 'Installation & Upgrades' section seemed like a good place...

I'm planning to instal Xubuntu 9.04 on a 2GB CF/IDE card. The CF card will hold the OS & software, while a MECHANICAL IDE drive holds my files. Being a complete simpleton, I'd like advice on the following:

*Does anyone have experience with this sort of setup?

*I don't want to use the ext2 file system, but which OTHER (journalled) one (ext3, 4? JFS? &c.) will do the least violence to the flash card?

Thanks,
Adam

---

### Post by mkoonstra on 2009-04-24
You should consider whatever you find acceptable for writes. I have a server on a 4gb CF. I have chosen for ext3 for increased stability in case there is a power outage. It seems these flash discs can nowadays support nearly 50000 rewrites. I have paid about 25 euro's for this device, so if it fails at any time. I will just replace it with another one, as it is just the OS disc. Make frequent backups (which is always important) and you shouldn't have to bother to much.

---

