---
title: "Problem with Emacs"
date: 2008-09-08
forum: General Help
---

### Post by wtfitsRICK on 2008-09-08
Erp.  I doubt this is the right place for this post, but I wasn't sure where else to go.

So, I got Emacs installed properly.  In the terminal, I'm logging into my UNIX account with SSH.  All that is going fine and well.  But when I try to open a java file with Emacs, rather than opening Emacs in a new window, it just displays the text of the file in the terminal.  I can edit it, but I haven't a clue how to save/compile it.

Any help?  I just want Emacs to open right.  haha.

---

### Post by gaussian on 2008-09-08
> **wtfitsRICK said:**
> Erp.  I doubt this is the right place for this post, but I wasn't sure where else to go.

So, I got Emacs installed properly.  In the terminal, I'm logging into my UNIX account with SSH.  All that is going fine and well.  But when I try to open a java file with Emacs, rather than opening Emacs in a new window, it just displays the text of the file in the terminal.  I can edit it, but I haven't a clue how to save/compile it.

Any help?  I just want Emacs to open right.  haha.

If I understand correctly you want to emacs to open new X-Window (GUI-window) with all the goodness associated.

To do this, you'll probably need to enable X-forwarding in ssh. Warning: this can be really slow over slow network.

To do so: ```
ssh -X myaccount@unixserver.edu
```

Now try starting emacs

---

### Post by wtfitsRICK on 2008-09-09
Thanks so much. That worked just fine!

---

