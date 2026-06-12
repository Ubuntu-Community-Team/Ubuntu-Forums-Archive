---
title: "~/bin in PATH, giving Permission denied"
date: 2008-10-28
forum: General Help
---

### Post by notquitehere188 on 2008-10-28
I added ~/bin to my path.  But whenever I try to use a file from there, I get a Permission denied error.

when i am in that directory it gives me no problems.

any idea why?

---

### Post by Gannon8 on 2008-10-28
Just asking, why would you do that?

I think that would be unstable, considering that the ~ directory changes with every user that logs in.

---

### Post by snova on 2008-10-28
Try replacing ~/bin with /home/<username>/bin.

Sometimes setting variables with ~ in them doesn't work.

---

### Post by doas777 on 2008-10-28
Gannons question has merit, 

when you run commands from bin, are you using sudo/gksu? if you were, I think ~ would point to /root .

---

### Post by snova on 2008-10-28
> **Gannon8 said:**
> Just asking, why would you do that?

So that he can write his own programs and run them without using absolute paths. I have a private bin directory myself.

> **Gannon8 said:**
> I think that would be unstable, considering that the ~ directory changes with every user that logs in.

Why would he log in as somebody else? :) And the PATH setting would only apply to himself anyway.

---

