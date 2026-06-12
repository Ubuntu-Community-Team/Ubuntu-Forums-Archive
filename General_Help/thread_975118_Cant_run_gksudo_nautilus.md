---
title: "Cant run gksudo nautilus"
date: 2008-11-08
forum: General Help
---

### Post by bossa on 2008-11-08
Hi all 
 Cant run gksudo nautilus get this message in terminal :


steve@steve-desktop:~$ gksudo nautilus
Initializing nautilus-share extension
Initializing nautilus-open-terminal extension

(nautilus:6687): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:6687): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:6687): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:6687): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
steve@steve-desktop:~$

---

### Post by bossa on 2008-11-08
bump

---

### Post by vizualbod on 2008-11-08
I normally use just "sudo nautilus".

---

### Post by Idefix82 on 2008-11-08
> **vizualbod said:**
> I normally use just "sudo nautilus".

This is strongly discouraged. See for example here: [http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

Having said that, I would discourage most people from opening nautilus with root privileges, too. You can mess up things quite easily. What is it that you want to do that requires root privileges?

---

### Post by bossa on 2008-11-08
OK everything is ok now .After restarting a couple of times Ubuntu did a disc check and all is back to normal .Been using nautilus with root privilege for yonks ...I'm careful ;)
Thanks

---

### Post by phantomgunex on 2008-11-08
> **Idefix82 said:**
> This is strongly discouraged. See for example here: [http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

Having said that, I would discourage most people from opening nautilus with root privileges, too. You can mess up things quite easily. What is it that you want to do that requires root privileges?


Well you have to use root privileges to edit some files as all system files belong to root, but you have to be careful as i once accidentally edited some system files to belong to me and could start u, so i had to reinstall ubuntu! With great power comes great responsibility!

---

### Post by Idefix82 on 2008-11-08
> **phantomgunex said:**
> Well you have to use root privileges to edit some files as all system files belong to root

Yes, but you don't need Nautilus for that. If you just want to edit a text file, you can open nano or gedit or your favourite text editor with root privileges directly from the terminal with. If you want to copy or move a file you can also do it directly from the terminal. It's more secure and faster.

---

### Post by Yashiro on 2009-02-21
You can sometimes fix this by closing and restarting the bonobo activation process.

Another odd fix is to remove any cdroms from your drives and retry.
Odd indeed, but it works.

Or try *gksudo dbus-launch nautilus*.

---

