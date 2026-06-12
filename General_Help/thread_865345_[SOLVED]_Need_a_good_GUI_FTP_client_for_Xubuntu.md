---
title: "[SOLVED] Need a good GUI FTP client for Xubuntu"
date: 2008-07-20
forum: General Help
---

### Post by Bruce M. on 2008-07-20
Hi Folks,

I'm looking for a good GUI FTP client for Xubuntu 8.04.

I tried **foff** in the repositories but it doesn't want to run. It starts up then closes, so I looked in terminal and see this error:
```
bruloo@bruloo:~$ foff
Python module pymedia missing. Disabling FOFF Audio Player.

/usr/bin/foff:2270: GtkDeprecationWarning: gtk.threads_enter is deprecated, use gtk.gdk.threads_enter instead
  gtk.threads_enter()
Traceback (most recent call last):
  File "/usr/bin/foff", line 2271, in <module>
    mWnd = mainWnd("/usr/share/foff/foff.glade", "mainWnd")
  File "/usr/bin/foff", line 280, in __init__
    self.load_local_dir(self.fcLocalDir.get_filename())
  File "/usr/bin/foff", line 739, in load_local_dir
    file_stat = os.stat(diritem)
OSError: [Errno 2] No such file or directory: 'Examples'
bruloo@bruloo:~$ 
```
I'm not interested in the Audio Player (? in an FTP client ?)

Can anyone steer me to another GUI FTP client that actually works.

Thanks.

Have a nice day.
Bruce

---

### Post by OscarPapa on 2008-07-20
gftp might be what you're looking for.

---

### Post by uberlube on 2008-07-20
Filezilla is one of the best

---

### Post by Bruce M. on 2008-07-20
> **OscarPapa said:**
> gftp might be what you're looking for.

Hi OscarPapa

OK, I'll take a look at it.

Thanks
Bruce

PS: Love your sig, you just called me *ingenious*. :lolflag:

---

### Post by Bruce M. on 2008-07-20
> **uberlube said:**
> Filezilla is one of the best

Hi uberlube

See, now that I didn't know, I thought that was a Windows program and didn't see it when I searched the repositories.

I'll look at that too.

Thanks.
Bruce

---

### Post by Bruce M. on 2008-07-20
**[SIZE="6"][COLOR="Blue"][CENTER]Thanks folks.[/CENTER][/COLOR][/SIZE]**

Both gftp and Filezilla are good choices.

Have a nice day.
Bruce

---

