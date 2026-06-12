---
title: "Listing installed applications"
date: 2008-08-02
forum: General Help
---

### Post by Midahed on 2008-08-02
In 8.04 Hardy (and earlier Ubuntu releases) selecting 'Applications' from the menu and then 'Add/Remove' allows you to see a list of installed applications.

Is there a way to access this data via a terminal window and the command like?  Or is it available somewhere in readable form in a file?

I want to extract a list of installed applications in text form that I can retain for future reference.

Thanks,

Mike

---

### Post by sisco311 on 2008-08-02
```
dpkg --get-selections > installed-packages.txt
```

---

### Post by Midahed on 2008-08-02
Thanks.  That's useful and it's almost what I was after, but it's a list of _all_ packages rather than the simpler (and much smaller) applications list that's available under the 'add/remove' option.

Also, I'd need to run dpkg on a running system.  I'm actually after a list of applications that _were_ in use on my old Ubuntu 7.04 machine.  It won't run any longer, but I can mount it's root partition read-only and examine files on the old system disk.

Is there a way of easily extracting an application list in those circumstances?

---

