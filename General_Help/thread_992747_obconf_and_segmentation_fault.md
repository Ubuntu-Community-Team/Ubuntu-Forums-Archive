---
title: "obconf and segmentation fault"
date: 2008-11-25
forum: General Help
---

### Post by jdinosaurus on 2008-11-25
Hey guys, maybe you can help me to fix the following problem. I cannot run obconf after i have upgraded to intrepid. I think I have already tried everything: all versions of openbox and obconf in different combinations - but still obconf ends up with segmentation fault. I don't have any hope already to fix it. Please help!
Thank you very much in advance!

---

### Post by jdinosaurus on 2008-11-28
I have found the solution. What i did is:
- i made sure that i don't have any files from previous installations of obconf (especially in /usr/local/...)
```
sudo dpkg -L obconf
``` - and check do i have the same folder in /usr/local - if yes - then delete it. And the same for openbox
- i deleted all openbox themes in .themes folder using : 
```
find ~/.themes name openbox* | xargs rm -r 
```
After that the problem disappear

---

