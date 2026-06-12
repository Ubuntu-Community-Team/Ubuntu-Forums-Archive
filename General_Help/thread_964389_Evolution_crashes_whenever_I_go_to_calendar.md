---
title: "Evolution crashes whenever I go to calendar"
date: 2008-10-30
forum: General Help
---

### Post by wersdaluv on 2008-10-30
I'm on a fresh Intrepid install. I'm still using my old configuration files because I have a separate /home partition. When I started Evolution here for the first time, and a dialog popped out saying that it was converting my config files to be compatible with the new version. However, even after that step, whenever I go to the calendar part of Evolution, it crashes.

Any idea? :)

---

### Post by Psukez on 2008-10-31
The same problem here, every time  i go to calendar mode it crash with a segmentation fault. I'm using intrepid upgraded from hardy (since then got the problem) all the others sections of evolution work without problem i try to uninstall and reinstall it but this don't fix the problem :confused:

---

### Post by wersdaluv on 2008-10-31
Same here. I tried removing my old config files but it didnt make a difference.

---

### Post by Aenima99x on 2008-10-31
+1

---

### Post by Aksu on 2008-11-02
Me too am having this very same problem. :-(

---

### Post by hamidaddin on 2008-11-02
I am having the problem.

The messages that I get before the crash is:
```
(evolution:12911): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed
Changing the queries (contains? "summary" "") 
Segmentation fault

```

---

### Post by blakaxe on 2008-11-02
Me too. I get the following error message.


(evolution:11020): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed
Segmentation fault


Hope someone comes up with a fix.

---

### Post by wersdaluv on 2008-11-02
It works fine on KDE4 :D. haha

---

### Post by wersdaluv on 2008-11-04
The fix is to disable assitive technologies.

System->Preferences->Assistive Technologies, uncheck "Enable assistive technologies."

---

### Post by Aksu on 2008-11-04
How can you know it, if it's not broken in your machine???

---

### Post by Psukez on 2008-11-04
It work 
Thanks wersdaluv !!

---

### Post by wersdaluv on 2008-11-04
> **Aksu said:**
> How can you know it, if it's not broken in your machine???
Because I'm not on KDE all the time :)

---

### Post by Aksu on 2008-11-05
Yes. That really did the trick. First when I tried it, i didn't log out, and it did nothing. But after logging out, it really fixed that.

Thanks.


BTW. This Ubuntu 8.10 seems quite spooky. If something gets fixed this way, so what's next...

---

### Post by smen on 2008-11-19
That worked! When I tried to disable Assistive Technologies I received the message "Could Not launch Menu Item". I uninstalled thru Synaptic. Fixed the problem.

---

### Post by hamidaddin on 2008-11-24
Disabling Assistive Technologies fixed the problem for me.

Thanks wersdaluv...

---

### Post by wersdaluv on 2008-11-24
You're welcome :)

---

