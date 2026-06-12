---
title: "Fatal: Failed test: texture_from_pixmap support compiz error"
date: 2008-10-22
forum: General Help
---

### Post by shanks129 on 2008-10-22
hey guys i'm just new to linux so id really like it if some one could help me. I had the compiz manager and cube effects etc running before like yesteday but now when i type compiz -- replace to do it again i now have encountered this error: 

thomas@thomas-desktop:~$ compiz -- replace
thomas@thomas-desktop:~$ compiz -- replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.



please help. Many thanks

---

### Post by bwang on 2008-10-23
Post the outputs of:

```
lshw
```
```
lspci
```
```
glxinfo
```

---

### Post by shanks129 on 2008-10-26
i have discovered that i only encounter this error when i enter my restricted drivers manager and enable my ati driver. However i need to get it to run along side my compiz. Any ideas?

---

