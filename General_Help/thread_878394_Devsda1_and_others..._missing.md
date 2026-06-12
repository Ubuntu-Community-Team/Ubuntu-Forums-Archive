---
title: "Dev/sda1 and others... missing?"
date: 2008-08-02
forum: General Help
---

### Post by alisiacam on 2008-08-02
For the last couple weeks whenever the little orange words at the bottom of the ubuntu start up logo pop up, I have had to click 'esc' before it reached 4%.
When I go to my dev folder, a lot of the items in it have 'x's on the top corner of them. 
I have Hardy, on an lenovo x61
other than that, I'm not entirely sure what other information I can share with you...
Any insight as to whats going on/ how to fix it would be very much appreciated :)

---

### Post by alisiacam on 2008-08-03
When I start my computer, and don't hit 'esc' at the appropriate time, this comes up:
dev/sda1: UNEXPECTED INCONSISTENCY;
RUN fsck MANUALLY

---

### Post by bodhi.zazen on 2008-08-03
Looks like you have hard drive problems. You may or may not be able to recover :

Boot a live CD and run :

```
sudo fsck -rfv /dev/sda1
```

---

