---
title: "[OOo] Write error"
date: 2008-07-26
forum: General Help
---

### Post by tom-ubuntu on 2008-07-26
Dear all,

Having a problem with OpenOffice in Ubuntu (not only on one machine). I am not able to save files sometimes. This is the error message I am getting:

```
Error saving the document xxxx.xxx
The file could not be written.
```

You can not save the same document (using save), but also not as another (save as). If you use 'save as' it just writes a new 0byte file.

It mostly happens when you double click a document to edit, without having OOo already running. If you close the document and use the filedialog, it works fine. 
Error occurs also via filedialog, so I can not exactly define what is causing the issue.

Anyone having the same problem?
Is there a log file for OOo?
Any way to debug it?
Or better: a solution?  :-)

Any help is very much appreciated.

Thanks,
Tom

---

### Post by tom-ubuntu on 2008-07-28
Still have not found any solution...

---

### Post by Hagar Delest on 2008-07-28
You can try the official version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by tom-ubuntu on 2008-07-31
> **Hagar de l'Est said:**
> You can try the official version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Thanks, Hagar. Will give it a try.

For myself this would be a working solution. But for an average user I doubt, this would work. Removing ubuntu-desktop meta-package can not be that good...

Will report back, if it worked.

---

### Post by Sahas on 2008-09-03
Hello!

I have the same problem. The error appears when I try to save big document (approximately 30 Mb).

Update.

It seems, I've found an origin of the problem (in my case).
The error appears when the number of files in temporary directory (e.g. in /tmp/sv3a2.tmp/ - the name is vary) becomes greater than approximately 1000. The number is connected with the values of parameters in Tools->Preferences->Memory. As I understand, files *.tmp in /tmp/sv3a2.tmp/ are nothing more than cached objects written to the disk (these files are created during save process). I think, there is a limitation of maximum open temporary files in OpenOffice or problem with 256Mb limit in Memory.

---

