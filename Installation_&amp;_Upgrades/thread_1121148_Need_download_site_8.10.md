---
title: "Need download site 8.10"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by p2cd3 on 2009-04-09
My system did a update last night, when I rebooted it said I had bad data in my /etc/fstab line 13 - so I deleted that line - rebooted - now I was able to get into safemode

I will upgrade into 9.04 - how do I get my Bookmarks out of Firefox & my mail from Thunderbird - I went through the directories bur did not have any luck

TIA

---

### Post by knattlhuber on 2009-04-09
The files are in hidden folders. Open a Nautilus window and press Ctrl-H to view the hidden files and folders.

Firefox
~/.mozilla/firefox

Thunderbird
~/.mozilla-thunderbird


In order to avoid having to copy all your personal data before upgrading, you may want to consider creating a separate partition for the /home directory. That is, you would create 3 partitions: "/" (root, ext3), swap, and "/home" (ext3)

---

### Post by p2cd3 on 2009-04-09
Thank you knattlhuber

---

