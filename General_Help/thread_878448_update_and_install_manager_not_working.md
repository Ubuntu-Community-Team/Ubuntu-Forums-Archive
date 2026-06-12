---
title: "update and install manager not working"
date: 2008-08-02
forum: General Help
---

### Post by amado738 on 2008-08-02
I am relatively new to linux and still struggling. 

I got this message today and cant run update manager or install manager!

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

please give me a step by step guide on how I can fix this!

---

### Post by weweboom on 2008-08-02
open up applications>accessories>Terminal, then enter in: 
```
sudo dpkg --configure -a
``` that should do it

---

### Post by amado738 on 2008-08-02
thanks it seems to have worked. what exactly caused this problem in the first place so i know what to avoid doing so it doesnt happen again?

---

### Post by weweboom on 2008-08-03
Maybe you disconnected from your internet connection while you were downloading an update other than that I wouldn't know
also when you see a message that says manually run...  copy and paste the code into terminal and hit enter that's what that notification means

---

### Post by hansdown on 2008-08-03
Excellant advice weweboom. I wish I had known that when I first started. It is a common problem. Nice response.

---

### Post by Sef on 2008-08-03
> Maybe you disconnected from your internet connection while you were downloading an update other than that I wouldn't know
also when you see a message that says manually run... copy and paste the code into terminal and hit enter that's what that notification means

Or sometimes there is a problem with the download.

---

