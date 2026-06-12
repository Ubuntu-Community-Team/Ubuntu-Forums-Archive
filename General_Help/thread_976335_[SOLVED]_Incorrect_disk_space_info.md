---
title: "[SOLVED] Incorrect disk space info"
date: 2008-11-09
forum: General Help
---

### Post by DoctorBeaver on 2008-11-09
I installed Hardy and put Studio on afterwards. This PC is an old Sony Vaio with a 120Gb hard drive. In the bottom corner of File Manager it said there were 50.2Gb free.

Then I used the Disk Usage Analyser and it told me my disk is 219Gb and I've got 107.6Gb available.

I loaded just over 1Gb of music and now the Disk Usage Analyser says I've got 102.3Gb.

Has anyone else seen this sort of thing? It's not a problem because File Manager seems to be accurate. It just puzzles me.

---

### Post by drs305 on 2008-11-09
> **DoctorBeaver said:**
> 
Has anyone else seen this sort of thing? It's not a problem because File Manager seems to be accurate. It just puzzles me.

DUA/baobab confuses a lot of users because by default it includes the .gvfs files, ubuntu's virtual file system. This essentially doubles the reported size even though those files don't physically exist. You can turn off gvfs reporting by going into Edit, Preferences and deselecting .gvfs

Added:
The command below will give you an accurate reading of disk usage:
```

df -Th | grep '/dev/'

```

---

### Post by DoctorBeaver on 2008-11-09
Ah, that explains it. Thanks.

---

