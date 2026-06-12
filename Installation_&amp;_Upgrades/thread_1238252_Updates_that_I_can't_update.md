---
title: "Updates that I can't update?"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by vaxman- on 2009-08-12
Why do I get notification of updates that I can't update?  For example, today there was an update notification in the panel.  I clicked on it and it showed me two updates for Firefox:

firefox 
  meta package for popular ... (Size:69KB)
firefox-gnome-support
  meta package pointing to ... (Size:69KB)

But both are greyed out and I cannot click in the [_] selection box.

---

### Post by jerrrys on 2009-08-12
do this in terminal (**Alt **plus **F2 **key); there will not be any visual display of password.

**sudo apt-get update  **then  [B]sudo apt-get upgrade

[/B]this is what you have done

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/apt-get.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/apt-get.html)

this may also help you

[https://help.ubuntu.com/9.04/index.html](https://help.ubuntu.com/9.04/index.html)

and if you find that a bit dry

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  :)

---

### Post by vaxman- on 2009-08-13
> **jerrrys said:**
> do this in terminal (**Alt **plus **F2 **key); there will not be any visual display of password.

**sudo apt-get update  **then  [B]sudo apt-get upgrade

[/B]this is what you have done

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/apt-get.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/apt-get.html)

this may also help you

[https://help.ubuntu.com/9.04/index.html](https://help.ubuntu.com/9.04/index.html)

and if you find that a bit dry

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  :)

Yeah, I know all about apt-get; that doesn't answer _my_ question.

Why does the "update manager" icon appear in the panel informing me of updates that I cannot update?  I just find it every annoying.

AND...

And after executing the apt-get commands you've suggested and running then launching the "update manager", I still see the two greyed out Firefox updates.

---

### Post by wojox on 2009-08-13
What version of Firefox do you have and where did you download it from?

---

### Post by Partyboi2 on 2009-08-13
> **vaxman- said:**
> Yeah, I know all about apt-get; that doesn't answer _my_ question.

Why does the "update manager" icon appear in the panel informing me of updates that I cannot update?  I just find it every annoying.

AND...

And after executing the apt-get commands you've suggested and running then launching the "update manager", I still see the two greyed out Firefox updates.
The packages are greyed normally  because they lack some dependencies. Open a terminal and try
```
sudo apt-get dist-upgrade
```

---

### Post by vaxman- on 2009-08-14
> **wojox said:**
> What version of Firefox do you have and where did you download it from?
Ubuntu 8.10 and Firefox 3.0.13 which is, IIAC, the most recent version of FF that will run on Ubuntu 8.10.

---

