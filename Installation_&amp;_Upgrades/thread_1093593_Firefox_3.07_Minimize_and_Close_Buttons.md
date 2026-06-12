---
title: "Firefox 3.07 Minimize and Close Buttons"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by GeorgeOrr on 2009-03-11
After I upgraded to Firefox 3.0.7 I noticed that the browser does not show the usual minimize, close, etc. buttons at the upper right of the browser window.  If I use F11 to go to full screen mode and then F11 to go back to the window the buttons are now there.  Has anyone else seen this behavior, and if so have you figured out how to fix it?

Thanks!

---

### Post by Rallg on 2009-03-11
At about the time FF 3.0.7 was released, I noticed some odd window button problems, but they were not only in FF. Since then, they went away. Don't know if I did something funky then corrected it, or whether there has since been an update to something else in the system. All OK now, in FF and others. Ubuntu 8.10 i386.

---

### Post by martrn on 2009-03-11
At    /home/username/.mozilla/firefox/
eg.    /home/GeorgeOrr/.mozilla/firefox/

there is a profile folder (like dkfjhdgh.default) or similar.

If you browse that directory there is a file called localstore.rdf

Delete that file and re-start fire-fox and the problem should **(should)** be corrected.)


Firefox3.0.7
[http://support.mozilla_Id=295624]("http://support.mozilla.com/tiki-view_forum_thread.php?locale=no&forumId=1&comments_parentId=295624")

---

### Post by GeorgeOrr on 2009-03-11
Thanks Martrn -

I tried your suggestion with no result, but during the process discovered that somehow the top of the browser window had gotten hidden behind the toolbar at the top of the Ubuntu screen.  Once I managed to get hold of it and move it down, everything is working fine.

Thanks again for the help!;)

---

