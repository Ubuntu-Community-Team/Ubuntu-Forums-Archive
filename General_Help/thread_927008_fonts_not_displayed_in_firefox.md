---
title: "fonts not displayed in firefox"
date: 2008-09-22
forum: General Help
---

### Post by lucianct on 2008-09-22
on some webpages in firefox and prism (but not in opera) the text is not displayed. i have both the windows fonts and the apple fonts installed. some pages i can't see the text are facebook or the download page for gOS 3.0b

---

### Post by dodle on 2008-09-22
> **dodle said:**
> I was also having the same problem.

[IMG]http://www.freewebs.com/jordansroom/firefox3.png[/IMG]

After running firefox using the terminal, I was able to figure out that this was caused by a font that I had attempted to install.  Deleting the ~/.fonts folder fixed the problem.

I think this was also the cause of firefox crashing.  Every time I tried to log into ubuntuforums it would instantly shut down and give me a 'segmentation fault' error.

___________

---

