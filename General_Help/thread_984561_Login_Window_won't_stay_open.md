---
title: "Login Window won't stay open"
date: 2008-11-16
forum: General Help
---

### Post by ichiban-2k7 on 2008-11-16
I found a cool new login that I want to use for my ubuntu 8.04, but every time I select the login window (system\administration\login window) it prompts for my password. I type it in, and the window opens, but then closes almost immediately after opening. I've tried rebooting several times, but it still behaves weirdly. Is there a known solution?

Thanks

---

### Post by ichiban-2k7 on 2008-11-16
bump

---

### Post by binbash on 2008-11-16
sudo gdmsetup

Paste the output when it crashes.

---

### Post by ichiban-2k7 on 2008-11-16
Hi, it says:
segmentation fault

---

### Post by ichiban-2k7 on 2008-11-16
I read on wikipedia that segmentation faults occur because the program (i.e. gdm setup) isn't allowed to access or use system memory. Is there a way to fix that?

---

### Post by ichiban-2k7 on 2008-11-16
bump

---

### Post by Monotoko on 2008-11-16
How much system memory have you got?

---

### Post by ichiban-2k7 on 2008-11-16
512mb ram, DDR2

---

### Post by Monotoko on 2008-11-16
at the terminal, use:
```
sudo free -t -m
```
and post the output here

---

### Post by ichiban-2k7 on 2008-11-16
Hi, it says:

          total       used       free     shared    buffers     cached
Mem:           495        487          8          0         39        116
-/+ buffers/cache:        331        164
Swap:          953         38        915
Total:        1449        525        923

---

### Post by ichiban-2k7 on 2008-11-16
or a more morganised version:
          total          used       free     shared    buffers     cached
Mem:           495           487          8          0         39        116
-/+ buffers/cache:           331        164
Swap:          953            38        915
Total:        1449           525        923

---

