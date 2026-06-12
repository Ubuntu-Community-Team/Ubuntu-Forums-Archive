---
title: "ubuntu displays doesn't display available disk space with NTFS tool"
date: 2008-11-11
forum: General Help
---

### Post by gully on 2008-11-11
Hi, I have a dualboot system (win xp and hardy), I've downloaded a tool called "NTFS configuration tool" from the repositories so I can easily transfer files and it works fine.

I store all my videos and music on the ubuntu partition because linux is more stable and can survive mobo upgrades, etc...
When I checked the properties of my filesystem to see how much disk space on the ubuntu partition I had left on the ubuntu partition, it gave a way too small size of only 22gb left. and said that I had over 200gb of files on my filesystem, while it's actually much less.
Then I saw that my home folder displayed the correct amount of files, but the folder /media/disk contained all of the files from my win xp partition...

Is this normal when using the NTFS tool?
Does this mean that my filesystem will be "full" if I put another 22gb on it (Effectively wasting 150gb or so)?

---

### Post by taurus on 2008-11-11
What happens when you run this command from a terminal?

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by gully on 2008-11-12
When I enter that command it just gives me an error about clonedisk (or something similar) not being installed...

---

