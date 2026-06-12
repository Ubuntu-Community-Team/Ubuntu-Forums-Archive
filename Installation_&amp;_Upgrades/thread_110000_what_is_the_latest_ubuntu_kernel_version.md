---
title: "what is the latest ubuntu kernel version?"
date: 2005-12-29
forum: Installation &amp; Upgrades
---

### Post by yioan on 2005-12-29
just wanna ask what is the latest ubuntu kernel version? I think that I have seen an update of the kernel today but after the update I have not seen any difference. I have/had a kernel of version 2.6.12-10-386. Finally, was there an update of the kernel or not?:confused:

---

### Post by Sef on 2005-12-29
Your kernel is the most recent one for Ubuntu.  It was updated to it when you clicked on updates after  logging in.

---

### Post by az on 2005-12-29
[QUOTE=yioan] but after the update I have not seen any difference. I[/QUOTE]

Well, it's not like everything on your screen is a little greener or with a new kernel :)

...but seriously, do you have some performance issues that you think could be addressed?

---

### Post by yioan on 2005-12-30
Thanks. Now I feel better :) 

> but after the update I have not seen any difference

With this I just mean that I (think)have not seen any differences in the kernel version numbers(in the grub menu) and that no entry was inserted for a new kernel as usual. That's why I was wondering if there was a kernel update. What was the previous version of kernel(for ubuntu) and when was it released?

As for the performance issues: no, no at all :) . It is the first time in this linux world (of my laptop) that everythink works

---

### Post by az on 2005-12-30
[QUOTE=yioan]
With this I just mean that I (think)have not seen any differences in the kernel version numbers(in the grub menu) and that no entry was inserted for a new kernel as usual. That's why I was wondering if there was a kernel update. What was the previous version of kernel(for ubuntu) and when was it released?
[/QUOTE]
Well, updates are realy a grouping of updates and upgrades.

For example, an app can be released as foobar version 2.2 from the author.  The debian package maintainer turns it into a debian package names foobar-2.2_1

If the package maintainer finds a bug in the package, she can patch it and upload an update

foobar-2.2_1 becomes foobar-2.2_1.1

If the author of the package releases foobar-2.3, then the package maintainer has to start over and repackage the app into

foobar-2.3_1


All that to say that if the kernel goes from inux-image-2.6.12-10-386_2.6.12-10.25_i386.deb to inux-image-2.6.12-10-386_2.6.12-10.26_i386.deb, you will not see a seperate entry in your grub menu.  If there is a severe enough bug and the kernel version has to get bumped, you will get inux-image-2.6.12-11-386_2.6.12-11_i386.deb.


Both of these have already happened since release.  Breezy was released with linux-image-2.6.12-9 and we are now at 2.6.12-10.

---

### Post by yioan on 2006-01-01
thanks. it's good to know all these for the next time.

---

