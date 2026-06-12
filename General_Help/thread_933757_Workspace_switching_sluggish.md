---
title: "Workspace switching sluggish"
date: 2008-09-29
forum: General Help
---

### Post by rugbert on 2008-09-29
So the keypad commands *ctrl alt direction key* that would slide over to other workspaces is reaaaaaaallly sluggish and sometimes non responsive.  What information would I need to supply to troubleshoot this problem?

I guess the slide workspaces thing is set in the desktop wall. I also expo up and that is very quick and smooth.

---

### Post by zzzzz1 on 2008-09-30
when I had this problem, restarting compiz usually worked.

try, alt + F2 > 
```

compiz --replace
```

---

### Post by rugbert on 2008-09-30
> **zzzzz1 said:**
> when I had this problem, restarting compiz usually worked.

try, alt + F2 > 
```

compiz --replace
```

nope that didnt work, but it DID remove my ability to have more than one work spaces....


IDK, this feature was perfect in fedora 8

---

### Post by zzzzz1 on 2008-09-30
copizconfig setting manager > general options > Desktop size > horizontal Virtual size 

should give you your workspace's back.

---

### Post by rugbert on 2008-10-07
> **zzzzz1 said:**
> copizconfig setting manager > general options > Desktop size > horizontal Virtual size 

should give you your workspace's back.

Ok, got my workspaces back. So yea, any more ideas? The compiz manager seems a little different than when I was using FC8 so is there a different way to slide between workspaces?

---

### Post by rugbert on 2009-02-08
OK I got it. in Compiz manager I enabled desktop wall and set move left and right to super+corresponding arrow key, and turned on "Allow Wrap around".

then I turned off viewport switcher. so the only desktop effects I have on are expo and desktop wall

---

