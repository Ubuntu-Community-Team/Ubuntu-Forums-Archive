---
title: "please help me diagnose error msg (cannot open shared object)"
date: 2005-11-26
forum: General Help
---

### Post by stanwebber on 2005-11-26
i'm trying to migrate my counterstrike server over to linux.  the following error msg was generated while trying to load the metamod plugins

> L 11/26/2005 - 03:31:08: [META] ERROR: dll: Failed query plugin '<podbot_mm_i386.so>'; Couldn't open file '/usr/local/var/hlserver/cstrike/addons/podbot/podbot_mm_i386.so': libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

with my extremely limited experience with linux i'd guess the *podbot_mm_i386.so* binary is dynamically linked to some missing librarys.  my question is do i need to somehow get ahold of the source (not likely) & recompile or if there is a package i can install for the missing librarys, which ones?

---

