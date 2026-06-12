---
title: "gdmsetup fails"
date: 2008-10-23
forum: General Help
---

### Post by mikepac69 on 2008-10-23
Hi all,

I am having problems with gdmsetup.  When I try and start it through gksudo, i get the following:

[I]gdmsetup[3530]: GLib-CRITICAL: g_error_free: assertion `error != NULL' failed
gdmsetup[3530]: GLib-GIO-CRITICAL: g_simple_async_result_set_from_error: assertion `error != NULL' failed
gdmsetup[3530]: GLib-GIO-WARNING: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)[/I]

Any idea what the problem can be?

Thanks in advance.

Mike

---

### Post by Yashiro on 2009-02-21
Remove any cd/dvd's from their drives and retry.

---

