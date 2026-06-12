---
title: "&quot;Open as root&quot; script and nautilus-gksu not working in Hardy"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by stepheny on 2008-12-24
Hi I recently upgraded to hardy without any problems....until now. I have discovered that the script I have used for years with Ubuntu to open Nautilus as root has now stopped working. The script was:

```
#!/bin/sh
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gksudo "gnome-open $uri" &
done 
```

I tried simply doing sudo Nautilus and gksudo Nautilus and got the following

```
steve@x-desktop:~$ sudo nautilus
[sudo] password for steve: 
seahorse nautilus module initialized
Initializing nautilus-share extension

(nautilus:6653): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:6653): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:6653): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:6653): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault
```

Finally I installed nautilus-gksu but that also doesn't do anything now.

Any ideas?

Merry Christmas everyone.

---

### Post by stepheny on 2008-12-24
The problem was that I had a blank CD in the drive. I removed it and the script etc. all work now.

---

### Post by getglenn on 2009-07-02
this is solved my problem also...

i will check if this is a bug as it still happens and the date is now july 2009

---

