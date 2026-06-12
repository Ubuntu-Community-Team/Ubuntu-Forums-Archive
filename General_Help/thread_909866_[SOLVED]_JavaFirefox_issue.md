---
title: "[SOLVED] Java/Firefox issue"
date: 2008-09-03
forum: General Help
---

### Post by MarshyTheKid on 2008-09-03
I recently had to install 32 bit FireFox and Java on my 64 bit machine. It works fine, except at my school. My school requires you to run java when logging in with your laptop. When I load their page to validate me, firefox freezes on me. Here is the log containing the relevant information:

```
LoadPlugin: failed to initialize shared library /usr/lib32/firefox32/plugins/libnullplugin.so [libxpcom_core.so: cannot open shared object file: No such file or directory]
*** e = [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: chrome://browser/content/utilityOverlay.js :: getShellService :: line 307"  data: no]
```

---

### Post by tuxxy on 2008-09-03
Why did you install 32bit FF & java?

---

### Post by MarshyTheKid on 2008-09-04
> **tuxxy said:**
> Why did you install 32bit FF & java? Because 64 bit ubuntu and 64 bit java has issues and won't work with all applications.

---

### Post by tuxxy on 2008-09-04
Thats unusual, which ones did you have trouble with

---

### Post by MarshyTheKid on 2008-09-04
> **tuxxy said:**
> Thats unusual, which ones did you have trouble with

Not really. its quite common. There is a huge thread on it around here somewhere.

---

### Post by tuxxy on 2008-09-04
Well I never had a problem, can you give an example for me to test?

---

### Post by MarshyTheKid on 2008-09-04
> **tuxxy said:**
> Well I never had a problem, can you give an example for me to test?Certain java applications won't work. For example, my schools validation page and Facebooks Photo adding application. There are quite a few others, but I can't think of any others.

[http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)

I'm going to try installing an older version of Java and see if that works.

---

### Post by MarshyTheKid on 2008-09-04
Oh, and I forgot. Its not Java thats the problem with 64 bit, its the web browser plugin.

---

### Post by MarshyTheKid on 2008-09-04
Okay well, as usual, more searching and trying out other solutions solved this. I had to relink java to Firefox and all is well now.

---

### Post by b_petya on 2008-09-18
How did you solve this? It seems I have the same issue.

---

