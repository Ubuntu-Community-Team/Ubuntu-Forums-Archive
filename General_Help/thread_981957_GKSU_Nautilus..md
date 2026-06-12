---
title: "GKSU Nautilus."
date: 2008-11-14
forum: General Help
---

### Post by garfilth on 2008-11-14
Having a prob with nautilus.

It works great as a normal user no probs there. But when i try to open with GKSU in a terminal it crashes. 

here is the report from therminal:-

Initializing nautilus-share extension
Initializing nautilus-open-terminal extension

(nautilus:6174): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
(nautilus:6174): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:6174): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:6174): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)



strange thing is it works under XFCE.

im running Ubuntu 8.04, Gnome 2.22.3 and nautilus 1:2.22.5.1-0obuntu1.
nautilus-GKSU 2.0.0-5ubuntu3.
thanks in advance.

if this is wrong the wrong section, sorry.

---

### Post by renzokuken on 2008-11-14
have you tried

```
gksudo nautilus
```

---

### Post by garfilth on 2008-11-14
Hi, yes i have and i get the same prob. thanks for the replay.

---

### Post by philinux on 2008-11-14
I believe this is caused because you are out of temporary space. Try emptying trash and deleting stuff in /tmp.

---

### Post by garfilth on 2008-11-14
thanks. wastebin is empty and ./tmp is only 122kb.

still no joy though.

---

### Post by nikgare on 2008-11-14
MAybe something is wrong with nautilus' prefences for root.
You could try moving/renaming (not deleting) the /root/.nautilus folder to see if that makes a diffence

---

### Post by LowSky on 2008-11-14
does nautilus have any error if you run it from terminal without sudo?

have you tried

```
sudo -i
nautilus
```

---

### Post by garfilth on 2008-11-14
thanks. tried that but no joy. i will use thunar for now till i can fix it. 
i sent a bug report to launchpad. 

this is strange.

Ubuntu still rocks.

thanks for the help and suggestions.

---

### Post by garfilth on 2008-11-14
thanks lowsky, still no joy.

output from terminal is;-


root@garfilth-desktop:~# nautilus
seahorse nautilus module initialized
Initializing nautilus-share extension
Initializing nautilus-open-terminal extension

(nautilus:8009): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:8009): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:8009): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:8009): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault (core dumped)


:guitar:

---

### Post by LowSky on 2008-11-14
Do you happen to have a blank CD or DVD in your computer. Take it out and now try starting up gksu nautilus.

seems that others have had this issue

[http://ge.ubuntuforums.com/showthread.php?t=927195&page=3](http://ge.ubuntuforums.com/showthread.php?t=927195&page=3)

---

### Post by garfilth on 2008-11-14
you are a genius. sorted.


thanks dude.

:guitar:

---

