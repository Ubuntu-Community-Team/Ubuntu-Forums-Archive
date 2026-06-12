---
title: "login window"
date: 2008-10-12
forum: General Help
---

### Post by Flynn555 on 2008-10-12
hmmm for some reason whenever i open System>Administration>Login Window

the window opens and then immediately closes. so i am unable to change my GDM screen...i have no idea why it is doing this ... worked fine on 7.10

im currently running hardy.

---

### Post by aysiu on 2008-10-12
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here: ```
gksu gdmsetup &
```

---

### Post by Flynn555 on 2008-10-16
hmmm when i entered that command the window opened up fine....i guess the shortcut in the menu is messed up ... weird

---

### Post by Archanjil on 2008-11-24
actually the same exact thing happend to me, but it didn't work when i typed it in. Here is what i got typing that in terminal.

archanjil@Azrael:~$ gksu gdmsetup &
[1] 6251
archanjil@Azrael:~$ gdmsetup[6255]: GLib-CRITICAL: g_error_free: assertion `error != NULL' failed
gdmsetup[6255]: GLib-GIO-CRITICAL: g_simple_async_result_set_from_error: assertion `error != NULL' failed
gdmsetup[6255]: GLib-GIO-WARNING: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)

---

### Post by Yashiro on 2009-02-21
You can sometimes fix this by closing and restarting the bonobo activation process. Just restart if you're unsure what this means.

Another odd fix is to remove any cdroms from your drives and retry.
Odd indeed, but it works.

---

