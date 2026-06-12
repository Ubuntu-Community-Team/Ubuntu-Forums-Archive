---
title: "Latest Firefox Update Broken"
date: 2008-09-25
forum: General Help
---

### Post by sneilan on 2008-09-25
Today, on Sept 25, 2008 @ 10:18 PM, I upgraded to the latest version of Firefox. (3.0.3) Now, whenever I click the firefox button on my desktop, Firefox no longer loads.

When I run firefox from the command line, it does nothing:
$ firefox
$

I'm not sure what's going on. It wNothing.orked perfectly fine before I upgraded. Also, it worked as root from the command line:
$ sudo firefox -- this loaded Firefox for some reason.

---

### Post by ottocol on 2008-09-26
Same for me. Not even a message telling what's happening. Also, works as root.

---

### Post by Sycron on 2008-09-26
try ```
sudo dpkg --configure -a
``` and ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by heiowge on 2008-09-26
I had the same issue this morning after the update.  I tried all that and no luck.

I rebooted and all was well.  It all worked like a charm.

Try that.

---

### Post by Sycron on 2008-09-26
Yes, this can fix the problem.

---

### Post by ottocol on 2008-09-26
OK, problem solved, I had a .mozilla folder in my home directory but only with root write permissions. Probably I created it when I executed firefox as root, (not sure,creation date doesn't match, but well...)

Simply deleted .mozilla folder as root and now works perfectly. Thanks everybody for your collaboration.

---

### Post by spacedoubtman on 2008-09-26
for me after updating I had to killall firefox - it was still running and must have got confused.

---

### Post by sneilan on 2008-09-26
I had the same problem with the .mozilla folder.

I did 
```
sudo chown sneilan:sneilan .mozilla -R
```
and I fixed the problem! Yay :)

---

