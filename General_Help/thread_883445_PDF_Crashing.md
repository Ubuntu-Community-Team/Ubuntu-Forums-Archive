---
title: "PDF Crashing"
date: 2008-08-08
forum: General Help
---

### Post by Cornova on 2008-08-08
I have a PDF file will several hundred pages in it, and use the default Evince Document Viewer. When I typed 100 and pressed enter in the page number box the program crashed and continued to crash whenever I opened the file thereafter. I had to delete the file and redownload it just to view it again. 

This time I tried to just scroll to the 100th page and the program crashed and continued to crash whenever I would try to open that same PDF. This does not happen with free acrobat under WinXP.

Is there a better PDF viewer out there? Never had this trouble before, but then again I do not recall any others being this large.

---

### Post by DagMan on 2008-08-08
xpdf is a lightweight one.  if that also has problems then you can try acroread which is made by adobe.  I don't know if it's in the normal repos but it is in medibuntu for sure.

---

### Post by Cornova on 2008-08-08
Xpdf seems to work quite well, thanks for the tip. Unfortunately it doesn't allow the user to copy text as in Evince. :(

---

### Post by swisscow on 2008-08-08
Try the Adobe one (this command will install the adobe reader and firefox plugin)

```
sudo apt-get remove mozplugger && sudo apt-get install acroread acroread-plugins mozilla-acroread
```

---

