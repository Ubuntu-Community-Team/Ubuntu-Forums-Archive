---
title: "NTFStools chkdsk"
date: 2005-11-19
forum: General Help
---

### Post by Trab on 2005-11-19
so a while ago i posted about messing up my partions...
i was able to completely save ubuntu which of course is good...
but windows got screwed over.

when i boot in windows it says to run chkdsk...
when i try to mount in linux it doesnt work....
when i use NTFStools 
```

tedd@raptor:~$ ntfsfix /dev/hda1

Mounting volume... FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Permission denied
Volume is corrupt. You should run chkdsk.

```

so how do i run chkdsk?
thanks
Trab

---

### Post by nille on 2007-07-26
You need to run it with sudo:

**sudo ntfsfix /dev/hda1**

---

### Post by marcewalker87 on 2008-04-11
well despite that thanks to google, ur response helped me

---

