---
title: "[SOLVED] Brasero &amp;quot;segmentation fault&amp;quot; error"
date: 2008-10-11
forum: General Help
---

### Post by xjgnsdof on 2008-10-11
when I run Brasero in the shell, I get "segmentation fault" as the output, and the program doesn't load. What's wrong with Brasero? It has worked fine before.

---

### Post by xjgnsdof on 2008-10-14
up

---

### Post by xjgnsdof on 2008-10-17
up

---

### Post by xjgnsdof on 2008-10-22
Up

---

### Post by Vadi on 2008-10-22
It means the program is crashing. 

Try installing a newer version from getdeb: [http://www.getdeb.net/search.php?keywords=brasero](http://www.getdeb.net/search.php?keywords=brasero) maybe it'll help.

---

### Post by xjgnsdof on 2008-10-22
Installing Brasero 0.8.2 from getdeb solved the problem. Thanks.

---

### Post by Vadi on 2008-10-22
you're welcome. click on thread tools -> mark thread as solved to help others later on.

---

### Post by RadiusXE on 2009-03-02
same problem, 0.8.4 does not work too

I deleted config, but does not work too :(

Xubuntu 8.0.4.2, LXDE

this is all what I get from xterm


I/O warning : failed to load external entity "/home/buk/.config/brasero/brasero.session"

(brasero:9738): GLib-GIO-CRITICAL **: g_file_info_get_is_symlink: assertion `G_IS_FILE_INFO (info)' failed

(brasero:9738): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

---

### Post by donpaolo on 2011-05-20
The bug happened to me, in a weird way: I burnt a cd with brasero 2.32.0, and then, when trying to burn the following cd, it gave the seg fault.

I didnt' reboot nor I exited the session. The day after brasero worked again.

It's kind of a mistery...

---

### Post by Mr.Carramba on 2011-10-21
same here, after the seg fault I cant burn or find anything on cdrom... the bug was reintroduces...

---

### Post by techvish81 on 2011-10-21
> **Mr.Carramba said:**
> same here, after the seg fault I cant burn or find anything on cdrom... the bug was reintroduces...

brasero is not reliable at all . I've lost two blank dvds . 
imo ditch it &use k3b

---

