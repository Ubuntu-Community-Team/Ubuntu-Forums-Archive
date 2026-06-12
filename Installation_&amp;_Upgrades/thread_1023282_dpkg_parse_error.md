---
title: "dpkg: parse error"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by jmetric on 2008-12-27
I've finished installing Intrepid Ibex.  About half of the updates downloaded and installed successfully, but the others failed.  Now, when I retry to download them I get the message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I run 'dpkg --configure -a' I get the message:

dpkg: parse error, in file `/var/lib/dpkg/updates/0143' near line 1:
 newline in field name `#padding'


Any suggestions as to what I should do?

Thanks for any help!

---

### Post by hansdown on 2008-12-27
Hi jmetric.
You may find a good solution here.

[https://answers.launchpad.net/ubuntu/+question/10265](https://answers.launchpad.net/ubuntu/+question/10265)

---

### Post by jmetric on 2008-12-28
Thanks, hansdown.

I tried all the suggestions that you directed me to, but none of them have solved the problem.

First I get this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Then, when I run 'dpkg --configure -a' I get the original error message:

dpkg: parse error, in file `/var/lib/dpkg/updates/0143' near line 1:
 newline in field name `#padding'

Kind of an infinite loop problem.  

Anyone else have some idea as to what I can do?

---

### Post by howefield on 2008-12-28
Have you run the command with sudo ?


```
sudo dpkg --configure -a
```

---

### Post by jmetric on 2008-12-28
Yes, I used sudo, but got the same results.

---

### Post by Partyboi2 on 2008-12-28
Have you tried moving the file out of the way?
```
sudo mv var/lib/dpkg/updates/0143 var/lib/dpkg/updates/0143.old
```
then
```
sudo dpkg --configure -a
```

---

