---
title: "[SOLVED] System - Administration - Login Window"
date: 2008-09-14
forum: General Help
---

### Post by Tepear on 2008-09-14
I recently reinstalled Ubuntu (I missed it to much to not have it) and was going to change some settings in the Login Window. However, when I open it it stays open for a split second and then crashes.

Any ideas on how to fix this?

---

### Post by rraj.be on 2008-09-14
Try with recovery mode during startup to check what is happening.

---

### Post by -Zeus- on 2008-09-14
> **rraj.be said:**
> Try with recovery mode during startup to check what is happening.

huh?  how would that help?

OP: try running "sudo gdmsetup" from the terminal and post any output.

---

### Post by Tepear on 2008-09-14
Actually, the problem seems to have fixed it self... Kind of weird, but thanks for the quick responces!

---

### Post by csaga on 2008-11-04
When I try to open System>Administration>Login Window is dissapear and when try to run in Terminal sudo gdmsetup the followed error occur:

gdmsetup[7481]: GLib-GIO-CRITICAL: g_simple_async_result_set_from_error: assertion `error != NULL' failed
gdmsetup[7481]: GLib-CRITICAL: g_error_free: assertion `error != NULL' failed
gdmsetup[7481]: GLib-GIO-CRITICAL: g_simple_async_result_set_from_error: assertion `error != NULL' failed
gdmsetup[7481]: GLib-GIO-WARNING: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault

Thanks for help!

---

### Post by Yashiro on 2009-02-21
If you have a blank cdrom in your disk drive this happens every time.

---

### Post by csaga on 2009-02-21
OK! Thanks, worked.

---

