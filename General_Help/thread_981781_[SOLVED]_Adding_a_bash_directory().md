---
title: "[SOLVED] Adding a bash directory(?)"
date: 2008-11-14
forum: General Help
---

### Post by supergrover1981 on 2008-11-14
Hi gang,

I'm just getting started with bash & it looks like it could be very handy. I have a slight problem:

I'm currently storing all of my bash scripts in ~/bashscripts/, and I'm wondering how I can call the scripts in there via (scriptname.sh), as opposed to ~/bashcripts/(scriptname.sh), which is what I have to do now.

Any suggestions most appreciated.

Cheers,
        - SuperGrover

---

### Post by spibou on 2008-11-14
```
PATH="$PATH":~/bashcripts
```

---

### Post by supergrover1981 on 2008-11-14
*grin* Perfect. Many thanks. :-)

---

