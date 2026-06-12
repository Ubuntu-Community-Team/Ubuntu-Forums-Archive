---
title: "List of error messages starting up XFCE"
date: 2006-01-07
forum: Installation &amp; Upgrades
---

### Post by stroopwafel on 2006-01-07
After I type startxfce4 I get a whole list of error messages, but I can't <SHift-PgUP> far enough to see them all.

QUESTION: How can I send them to a file? I would like to post them to have people check if any of the messages are critical

(I tried startfxce4 | filename, but I only got three lines with "starting X server.....agent pid 7043 killed")

---

### Post by 5-HT on 2006-01-07
Sorry for your XFCE issues...

To get a log of the errors, what about trying:
```
 startxfce4 | tee <path to file you want it to go to> 
```

For example, if you want the file on your desktop:

```
 startxfce4 | tee ~/Desktop/xfce_startup_errors.txt 
```
(given that file isn't already present, or else it will be overwritten)

HTH

---

