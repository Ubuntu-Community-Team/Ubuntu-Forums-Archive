---
title: "haveing trouble downloading"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by invitingdopeman on 2009-08-12
whats up peeps im havein trouble with installing msn messenger live beta it tells me End-of-central-directory signature not found. i have also attached a screen shot is it becuse its microsoft thanks INVITINGDOPEMAN

---

### Post by Partyboi2 on 2009-08-12
Hi, looks like you you are trying to extract a .exe file. The .exe files are used by windows and not native to linux. I would recommend using something like amsn which is similar to msn. 
You can install amsn by opening a terminal (Applications>Accessories>Terminal) and typing
```
sudo apt-get install amsn
```

---

### Post by 3rdalbum on 2009-08-12
> **invitingdopeman said:**
> whats up peeps im havein trouble with installing msn messenger live beta it tells me End-of-central-directory signature not found. i have also attached a screen shot is it becuse its microsoft thanks INVITINGDOPEMAN

Whoa, this isn't a compressed archive, this is a Windows program. Anything with ".exe" at the end is a Windows program and can't be used on Linux except possibly with Wine. And I don't think MSN Messenger works in Wine.

Your system comes with Pidgin (Applications > Internet > Pidgin Internet Messenger), which can connect to the MSN messenger network.

---

