---
title: "BusbyBox - Ubuntu Start up"
date: 2008-10-03
forum: General Help
---

### Post by gtno on 2008-10-03
Hello,

I started up ubuntu and got the busybox screen, so I cntrl + alt + F1 to the error screen and it says that I need to load windows and do a chkdsk /r. So, I did just that and I restarted into ubuntu and it says the samething.  I need some input as I am new to ubuntu and I don't know where to go from here. Thanks in advanced.

---

### Post by gtno on 2008-10-03
bump

---

### Post by Ryadt on 2008-10-03
Bump your post not before 24 hours.

Try to use the kernel boot options "all_generic_ide" .
Follow this guide as to how to input the parameter: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
substitute the "quiet splash --" and add "all_generic_ide" (without the quotes)

---

### Post by gtno on 2008-10-03
Thanks for the info, I will check it out.

---

