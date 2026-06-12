---
title: "firefox weirdness"
date: 2008-11-04
forum: General Help
---

### Post by Olivier Lec on 2008-11-04
Hello,

Since I have upgraded to Intrepid, my firefox keep closing itself all by itself. I even tried to start it from a terminal to see if it output some information when closing, it turns out it only print "Aborted" on the terminal. 

Anyone have the same problem or some fix idea ?

---

### Post by Ryadt on 2008-11-04
You can try reinstalling firefox.
First delete firefox and the .mozilla folder (it's hidden).
Then reinstall.

---

### Post by Olivier Lec on 2008-11-04
I will try right now 

Thanks

---

### Post by Olivier Lec on 2008-11-04
> **Olivier Lec said:**
> I will try right now 

Thanks

No after an mv .mozilla mozillaold
aptitude remove firefox && aptitude purge firefox && aptitude install firefox

still the same problem, I forgot to mention my firefox start whitout title bar, I have to press F11 twice to make it reappear, from I have read it seem to be a compiz vs firefox incompability. Wondering if it's also creating those sudden crash....

---

### Post by Olivier Lec on 2008-11-04
> **Olivier Lec said:**
> No after an mv .mozilla mozillaold
aptitude remove firefox && aptitude purge firefox && aptitude install firefox

still the same problem, I forgot to mention my firefox start whitout title bar, I have to press F11 twice to make it reappear, from I have read it seem to be a compiz vs firefox incompability. Wondering if it's also creating those sudden crash....

OK just disable my compiz the title bar come clean but still the crahes. Could be related with flash ?

---

### Post by Olivier Lec on 2008-11-04
Digging a bit more I get this error

terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check
Aborted

any hint ?

---

### Post by cjlindem on 2008-11-12
The instructions in this bug report seem to have fixed it for me.

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/286119]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/286119")

Basically, uninstall winbind package if you have it installed.

---

