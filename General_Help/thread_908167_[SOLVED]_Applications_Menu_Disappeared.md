---
title: "[SOLVED] Applications Menu Disappeared"
date: 2008-09-02
forum: General Help
---

### Post by Curbuntu on 2008-09-02
My Applications menu has disappeared in Ubuntu 8.04.1.  That is to say, it is *there*, but won't "pull down."  The Places and System menus (and submenus) are unaffected.

Quick background: this is on a limited-size dual-boot partition.  A misguided Simple Backup to an external drive that wasn't mounted resulted in the partition filling up completely.  Those backup files have been erased and plenty of hard-drive room (at least 10 Gb) has been restored.

I don't know what effect (if any) the temporarily full drive had on the Applications menu problem, but I thought I would report on it, in case there is a cause-and-effect relationship.

Any help in getting my apps menu restored would be appreciated.  Thanks!

---

### Post by quibbler on 2008-09-02
Try removing it from the panel, then adding it again.

Regards quibbler

---

### Post by mc4man on 2008-09-02
The easiest way is to go to /home/<username>/.config/menus and delete the file applications.menu

Note: .config is a hidden file, use Ctrl+h while in home or enable under view

---

### Post by Curbuntu on 2008-09-02
> **quibbler said:**
> Try removing it from the panel, then adding it again.

Regards quibbler

Thanks.  Good thought, but it didn't move the situation along.  Back to the proverbial "Square One"...

---

### Post by Curbuntu on 2008-09-02
> **mc4man said:**
> The easiest way is to go to /home/<username>/.config/menus and delete the file applications.menu

Note: .config is a hidden file, use Ctrl+h while in home or enable under view

This suggestion gives me pause, only because I don't know what will come next.  Before I implement it, I'd like to know: Will the system recreate the file applications.menu and properly populate it?

---

### Post by mc4man on 2008-09-02
> Will the system recreate the file applications.menu 
Yes, 

> and properly populate it? ]

Yes
The moment you click on Applications all will be recreated as it was.

---

### Post by Curbuntu on 2008-09-02
Bingo!  It worked like a charm.  Thanks very much!

---

### Post by palimmo on 2008-10-03
> **mc4man said:**
> The easiest way is to go to /home/<username>/.config/menus and delete the file applications.menu

Note: .config is a hidden file, use Ctrl+h while in home or enable under view

WOW!
Thank you very much from Italy!!

How is this problem possible? And... in particular, where have you learned to solve it?
:guitar:

---

