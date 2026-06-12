---
title: "can't find X includes..."
date: 2005-11-10
forum: General Help
---

### Post by k0An on 2005-11-10
hello,

I wrote in the subject window the error I have when i try to install an application (KFTPGrabber) within Ubuntu 5.10.
I can't understand why this happens, I followed a lot of advices here and there, about essential files and usefull commands.
but it still does not fisnih installing.

any1 has an idea how to fix this problem?

Regards,
k0An

---

### Post by Kyral on 2005-11-10
You can't find the X dev files? Is that what you mean?

---

### Post by k0An on 2005-11-10
hmmm... sorry if I did explain things not clearly.

Once ./configure execution in progress, it stops with this error:

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

No more details.
Everything woks fine within Ubuntu, except for comiling some applications...

---

### Post by Kyral on 2005-11-10
I think the package you need to install is xlibs-dev

---

### Post by k0An on 2005-11-10
you were right :)

Qt3 (headers and libraries) were necessary too.
as well as KDE (many) files.

make is in progress while I'm writing these lines... :smile:

---

