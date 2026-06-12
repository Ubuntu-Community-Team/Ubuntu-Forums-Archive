---
title: "Sudo Nautilus (UbuntuStudio)"
date: 2008-11-11
forum: General Help
---

### Post by Shaby on 2008-11-11
ok ive been reading and this may be a bug but i dont know.  And dont tell me not to use sudo for gui applications because it works fine, and ive tried lots of others like "sudo su" "sudo -s" "gksu" and "gksudo" with no success...

Here is what shows up when in try to gain accesss as root into nautilus:
seahorse nautilus module initialized

(nautilus:9233): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:9233): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:9233): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:9233): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault

I really want this bloody thing to work!
Help is required if you just read this sentence. ;D

Thanks..?

---

### Post by Yellow Pasque on 2008-11-11
The only thing I found was the suggestion on this page to force the version of libglib2.0-0 to the one found in the hardy repo (you have the hardy-updates version installed)
[http://www.twotoasts.de/bugs/index.php?do=details&task_id=97](http://www.twotoasts.de/bugs/index.php?do=details&task_id=97)

BTW, the correct way is to start it with gksudo or gksu, even if it doesn't make the error disappear.

---

