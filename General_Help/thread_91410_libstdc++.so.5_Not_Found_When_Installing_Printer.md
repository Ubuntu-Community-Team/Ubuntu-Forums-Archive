---
title: "libstdc++.so.5 Not Found When Installing Printer"
date: 2005-11-17
forum: General Help
---

### Post by Ubuntist on 2005-11-17
Following [http://www.ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+printer](http://www.ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+printer) to install a driver for my Lexmark Z55, I get the message
[INDENT]
./z55: error while loading shared libraries: libstdc++.so.5: cannot op en shared object file: No such file or directory
[/INDENT]
when I try to test the backend.  Now, I ain't no expert, but I'd guess that what's lacking is some sort of C++ shared-object ("so"?) library.  So in Synaptic I loaded libstdc++6-4.0-pic and, for good measure, libstdc++6-pic.  Then I did "sudo ldconfig" and tried running the backend, /usr/lib/cups/backend/z55, again.  I got the same error message again.

Anybody got any hints for a noob?

Secondary question:  Presumably loading the two packages above wasn't the right thing to do.  When I remove them (so as to avoid cluttering the system), should I do a simple removal in Synaptic or should I do a complete removal?

---

### Post by matthewv on 2005-11-17
Maybe you need libstdc++5 , which is in the main repository??

---

### Post by Ubuntist on 2005-11-17
BINGO!  That did the trick.  Thank you!

---

### Post by nSTKo on 2005-11-17
```
sudo apt-get install libstdc++5
```

---

### Post by Ubuntist on 2005-11-17
Is there some tool that would have allowed me to determine that libstdc++5 was what I needed to load?

---

### Post by matthewv on 2005-11-17
[QUOTE=Ubuntist]Is there some tool that would have allowed me to determine that libstdc++5 was what I needed to load?[/QUOTE]
Not really. I just knew from what you were saying about libstdc++.so.5, i might have read about it before. It may have been listed in the dependancies for whatever you were doing.

---

