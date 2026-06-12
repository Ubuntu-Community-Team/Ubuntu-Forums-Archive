---
title: "Hibernate/Sleep without X"
date: 2011-03-30
forum: Hardware
---

### Post by vopilif on 2011-03-30
I have Ubuntu setup on my thinkpad running mostly in the console. I noticed whenever I don't have X running sleep/hibernate does not happen when I close the lid.

Is there a way to get this to work without X?

EDIT: Or can someone point me to some docs that explain how hibernate/sleep works on ubuntu?

---

### Post by vopilif on 2011-03-30
bump

---

### Post by vopilif on 2011-03-30
Found out how to cause it to sleep from the console here: 
[http://ubuntuforums.org/showthread.php?t=591036](http://ubuntuforums.org/showthread.php?t=591036)

```
sudo /etc/acpi/sleep.sh force
```Question is, how do I catch the lid closed event so I can trigger this?

---

### Post by vopilif on 2011-03-30
Solution found here (second answer):
[http://askubuntu.com/questions/3294/setup-suspend-on-lid-close-fnf4-outside-of-kde-gnome](http://askubuntu.com/questions/3294/setup-suspend-on-lid-close-fnf4-outside-of-kde-gnome)

Instead of using
```
#!/bin/sh\npm-suspend
```I used the command form my previous reply.

---

