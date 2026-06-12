---
title: "Not reconizing all USB devices"
date: 2008-08-12
forum: General Help
---

### Post by jsblackmaro on 2008-08-12
Hello.
I have several USB devices plugged into my PC that I use in Ubuntu.  Just recently, it no longer wants to let me see my camera.  It used to come up no problem.  But no matter what port I plug it into, it wont read it.  IT does read my external drive though.  Any ideas?

Josh

---

### Post by tamoneya on 2008-08-13
try plugging in just your camera and then checking the output of this command:```
dmesg | tail
```

---

### Post by jsblackmaro on 2008-08-13
I actually got this to work finally this morning.  I guess it wasnt unplugged from my Widows machine correctly. I plugged it in there, and safely removed it, and it worked.  I will keep that command for future reference!

Thanks for the help!

---

