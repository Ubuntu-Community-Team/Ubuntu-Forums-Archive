---
title: "Anjuta won't let me create new C++ classes"
date: 2008-11-15
forum: General Help
---

### Post by strigare on 2008-11-15
If I try to create a new class anjuta will tell me:

```
Failed to execute autogen: Could not open file "/home/strigare/file:///home/strigare/master/src/hello-world.hpp": No such file or directory
``` 

Anyone had the same problem?

---

### Post by strigare on 2008-11-16
Ok, I officially hate anjuta :P

I'll try to work with something else...

---

### Post by Mentalbug on 2008-12-11
Same problem here...

There's a problem in the path of the file, which is obvious but took  me time to figure out... 

> "[COLOR="Red"]/home/strigare/file:///home[/COLOR]/strigare/master/src/hello-world.hpp"

A useless $HOME variable (or something alike) must have magically appeared somewhere right before the actual path...

Anyone has any idea about that "slightly annoying" problem?  Cheers



*edit:* By the way, I have the problem on anjuta 2.24.1.

---

### Post by leonbnu on 2008-12-12
same problem here. Any solutions?

---

