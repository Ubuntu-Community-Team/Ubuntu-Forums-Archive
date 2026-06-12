---
title: "Am I running x86 or amd_64?"
date: 2008-08-22
forum: General Help
---

### Post by Deten on 2008-08-22
I have swapped a few times between 32 and 64 bit ubuntu, trying to find what I like, and whatever I have now I have stuck with...

How do I find out which one it is, I know its a stupid question, but I cannot remember :(

Thanks

---

### Post by adult swim on 2008-08-22
i think that if you had an x86 you could not run ubuntu 64-bit.  so if you could run both then you must have the 64

---

### Post by Deten on 2008-08-22
> **adult swim said:**
> i think that if you had an x86 you could not run ubuntu 64-bit.  so if you could run both then you must have the 64

Well I would reformat between uses... lets be honest, my first few months with ubuntu saw alot of critical errors while getting used to the power of sudo and the ease of people giving me commands through forums :)

Is there no system information place which has it? I cannot find it in system monitor :(

---

### Post by k8bopibu on 2008-08-22
> **adult swim said:**
> i think that if you had an x86 you could not run ubuntu 64-bit.  so if you could run both then you must have the 64

I believe that he is asking which he is running at the moment.

Run ```
uname -a
``` in a terminal. You should see x86_64 if you are a 64-bit user. if not then you will see something such as i386, i686 or such. Refer to this thread for more: [894044](http://ubuntuforums.org/showthread.php?t=894044)

~k8

---

### Post by adult swim on 2008-08-22
from terminal ```
uname -a
```
it will tell you

---

### Post by Deten on 2008-08-22
> Linux deten-laptop 2.6.24-20-generic #1 SMP Mon Jul 28 13:49:52 UTC 2008 i686 GNU/Linux


Looks like 32 bit

I appreciate the help!

---

