---
title: "linux-copying-with-middle-mouse-button"
date: 2008-10-27
forum: General Help
---

### Post by sulekha on 2008-10-27
Hi all,
i was going through this how to:

[http://www.cyberciti.biz/faq/linux-copying-with-middle-mouse-button/print/]("http://www.cyberciti.biz/faq/linux-copying-with-middle-mouse-button/print/")


How valid is this how to w.r.t to ubuntu linux, is there any changes that needs to be made ?

NB: i use **ubuntu hardy heron**

---

### Post by kaibob on 2008-10-27
> **sulekha said:**
> Hi all,
i was going through this how to:

[http://www.cyberciti.biz/faq/linux-copying-with-middle-mouse-button/print/]("http://www.cyberciti.biz/faq/linux-copying-with-middle-mouse-button/print/")


How valid is this how to w.r.t to ubuntu linux, is there any changes that needs to be made ?

NB: i use **ubuntu hardy heron**
It works fine for me--no changes are needed.

---

### Post by jpkotta on 2008-10-27
I've never had a mouse+Linux combination that didn't work with middle-click-paste out of the box, with no extra effort.  Did you try it?  

You can see if your middle button is working by running```
xev
```, middle clicking in the little window, and check for something like```
ButtonPress event, serial 32, synthetic NO, window 0x3800001,
    root 0x1a6, subw 0x0, time 31409961, (56,127), root:(1340,154),
    state 0x10, **button 2**, same_screen YES

ButtonRelease event, serial 32, synthetic NO, window 0x3800001,
    root 0x1a6, subw 0x0, time 31410057, (56,127), root:(1340,154),
    state 0x210, **button 2**, same_screen YES
```

---

