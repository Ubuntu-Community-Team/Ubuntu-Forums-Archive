---
title: "Cannot read Help File"
date: 2008-11-03
forum: General Help
---

### Post by JemW on 2008-11-03
Hi,

I use DeVeDe on Intrepid. When I try to access the Help pages I get the error in the screenshot attached here. Any ideas? The pages are all there.

Thanks

---

### Post by geirha on 2008-11-03
What are the permissions on that file?
```
ls -l /usr/share/doc/devede/html/main.html
```

---

### Post by JemW on 2008-11-03
> **geirha said:**
> What are the permissions on that file?
```
ls -l /usr/share/doc/devede/html/main.html
```
-rw-r--r-- 1 root root 7171 2008-08-27 09:26 /usr/share/doc/devede/html/main.html

---

### Post by geirha on 2008-11-03
Hm, the file is definitely there, and readable to all, so that error message doesn't make sense. I suggest you report this bug on launchpad [https://bugs.launchpad.net/ubuntu/+source/devede](https://bugs.launchpad.net/ubuntu/+source/devede)

---

### Post by JemW on 2008-11-03
> **geirha said:**
> Hm, the file is definitely there, and readable to all, so that error message doesn't make sense. I suggest you report this bug on launchpad [https://bugs.launchpad.net/ubuntu/+source/devede](https://bugs.launchpad.net/ubuntu/+source/devede)

I've reported it. I gather you could reproduce the error?

---

### Post by geirha on 2008-11-03
I'm currently using Hardy, but I installed devede just now in an Intrepid live session, and I got almost the same error message when I tried to select Help -> Help. 

It complained about /usr/share/doc/devede/html/index.html instead of main.html, but otherwise the same error message.

---

