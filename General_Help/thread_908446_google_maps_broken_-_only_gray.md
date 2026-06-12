---
title: "google maps broken - only gray"
date: 2008-09-02
forum: General Help
---

### Post by xdevnull on 2008-09-02
I have a similar problem as described here:
[http://ubuntuforums.org/showthread.php?t=739856&highlight=google+maps+gray](http://ubuntuforums.org/showthread.php?t=739856&highlight=google+maps+gray)

However, I can't post to that thread...so here goes.

This seems to have just started one day.  I am not running a skype extension (that I know of).  I have checked the extension add-on and it doesn't show up.  I have also disabled all my extensions, and the box is still gray.  

I did install skype, but I know I have used google maps after that install.  I'm not sure of what else might be causing this problem.

Any ideas of what to check?

---

### Post by faust99 on 2008-11-19
Have a look here [http://support.mozilla.com/tiki-view_forum_thread.php?locale=en-US&forumId=1&comments_threshold=0&comments_parentId=75219&comments_offset=20&comments_per_page=20&thread_style=commentStyle_plain]("http://support.mozilla.com/tiki-view_forum_thread.php?locale=en-US&forumId=1&comments_threshold=0&comments_parentId=75219&comments_offset=20&comments_per_page=20&thread_style=commentStyle_plain") for some ideas. For me it was a matter of changing this line dom.disable_image_src_set in the about:config of firefox to false. Now the maps come up properly.

---

### Post by dvo on 2009-05-22
In my case, the solution was to unset general.useragent.override (on the about:config page).

---

