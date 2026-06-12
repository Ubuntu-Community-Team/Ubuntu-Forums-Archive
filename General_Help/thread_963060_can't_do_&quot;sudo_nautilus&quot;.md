---
title: "can't do &quot;sudo nautilus&quot;"
date: 2008-10-29
forum: General Help
---

### Post by sakul07 on 2008-10-29
This is the error i get:

```

user@desktop:~$ sudo nautilus
[sudo] password for user: 
Initializing nautilus-open-terminal extension
seahorse nautilus module initialized
Initializing nautilus-share extension

(nautilus:6660): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:6660): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:6660): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:6660): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Fallo de segmentación


```

any help??

----------

after a little gogle search.. i found it was all about the "blank dvd mistery"... ejected the DVD and VOILA!

---

### Post by ardchoille42 on 2008-10-29
You should use gksudo (or kdesudo if you're in kde) with gui apps. Sudo is for command line apps, gksudo is for gui apps.

---

### Post by alienprdkt on 2008-10-29
maybe its a typo 
**#gksudo nautilus**

---

### Post by sakul07 on 2008-10-29
nope... it didn't work:

```

user@desktop:~$ gksudo nautilus
Initializing nautilus-open-terminal extension
Initializing nautilus-share extension

(nautilus:6889): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:6889): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
(nautilus:6889): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:6889): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)


```

---

### Post by Free Hugs on 2008-10-29
Ok...I got this same error for sudo Kino and sudo Nautilus earlier today. Even after a reboot, and a complete reinstall of kino. I figured something was wrong with the sudo command (gksudo didn't work either, it just didn't display any output errors). 

Either way...several hours later, I tried again and viola! It suddenly works again. Still...very perplexing.

---

### Post by snowhuouV on 2008-11-01
I've been having similar issues with progams crashing when Open/Save file dialogs opened. It appears to only happen when programs are run with sudo. A post an an [Arch linux forum]("http://bbs.archlinux.org/viewtopic.php?id=54596") mention something about Nautilus crashing when a blank CD was in the drive. Sure enough, I had a blank disc in my drive, but it was a DVD. Upon removing it, the crashes stopped.

It would seem the problem has to do with Nautilus and how it mounts blank discs.

/EDIT
I just noticed the small edit on the original post mentioning having a blank DVD inserted. :D

I also found this article: [http://www.hightechsister.com/559/nautilus-segmentation-fault-with-blank-cd/](http://www.hightechsister.com/559/nautilus-segmentation-fault-with-blank-cd/) 
Excerpt: > Without removing the cd, nautilus can be ran as root from the terminal using the command sudo dbus-launch nautilus.

This will to work for other programs too. Just replace nautilus with the program name.

---

### Post by cpriyantha on 2008-12-06
Me too faced to the same issue and struggled for some time. In some pages they are mentioning that they had to re-install the OS inorder to fix this issue. What you guys mentioned is exactly correct. The problem is having a blank dvd inside my burner. Thanks a lot for saving me from re-installing the OS :).

---

### Post by AmberG on 2008-12-06
I had the same problem and elsewhere on here (searched) I found this advice
```

gksudo dbus-launch nautilus
```
and that worked for me
don't know it will help - I'm still a novice myself.

---

### Post by warrior24 on 2009-05-15
I had a cdrw in my drive took it out and now the command works.

---

### Post by MainCore on 2009-12-03
I can confirm that errors with GLib on several Gnome programs are somewhat related to a blank CD/DVD inside the unit.

In my case the "Login Window" application to configure the GDM login window crashed when I inserted a blank DVD. No idea of the reason of this behaviour.

Also the sequence: "Synaptic -> Settings -> Repositories -> Authentication -> Import Key File" crashed with a blank DVD inserted.

By the way, I use Ubuntu 8.04 LTS Server (64 bits) with Gnome installed as graphical environment.

---

