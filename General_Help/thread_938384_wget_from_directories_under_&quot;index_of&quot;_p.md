---
title: "wget from directories under &quot;index of&quot; parent"
date: 2008-10-04
forum: General Help
---

### Post by bford16 on 2008-10-04
I need help with wget.  I'm trying to download a large number of zip files from an http directory. When I point my browser to the page, I get a page called, "Index of /Title."  The files I want are in directories listed on the page.  So the page looks like this.```
Index of /Title
Chapter 1
Chapter 2
Chapter 3
 and so forth
```Each chapter has a long random directory name under it, and the archive file is under that.  I tried wget like this.
```
wget -r -l5 -nc -np -nd -A.zip http://12.34.56.78/parent/Title

```
But this did not work.  All I got was the index.html pages, which of course were rejected.

---

