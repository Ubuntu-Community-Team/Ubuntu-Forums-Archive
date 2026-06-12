---
title: "remastersys is broken temporarily"
date: 2008-08-04
forum: General Help
---

### Post by mdsharp24 on 2008-08-04
If any users of Ubuntu 8.04, who have recently upgraded in the past week, notice that remastersys finishes with the error:

Creating custombackup.iso in /home/remastersys/remastersys

ls: cannot access /home/remastersys/remastersys/custombackup.iso: No such file or directory

[: 676: Illegal number: 

Creating custombackup.iso.md5 in /home/remastersys/remastersys

md5sum: /home/remastersys/remastersys/custombackup.iso: No such file or directory

ls: cannot access /home/remastersys/remastersys/custombackup.iso: No such file or directory

 

**This issue is a temporary problem that is being addressed**

---

### Post by tamoneya on 2008-08-04
ive been meaning to make a backup of my system with remastersys.  Please keep us updated.  Do you have any estimates?

---

### Post by mdsharp24 on 2008-08-04
I really don't know, the remastersys people say it's an Ubuntu issue, you can follow this thread.

[http://loscompanion.com/forums/index.php?PHPSESSID=23d5b5c9597f38cbab71a48da23299f8&topic=4429.0](http://loscompanion.com/forums/index.php?PHPSESSID=23d5b5c9597f38cbab71a48da23299f8&topic=4429.0)

---

### Post by darthchaosofrspw on 2008-11-01
> **mdsharp24 said:**
> I really don't know, the remastersys people say it's an Ubuntu issue, you can follow this thread.

[http://loscompanion.com/forums/index.php?PHPSESSID=23d5b5c9597f38cbab71a48da23299f8&topic=4429.0](http://loscompanion.com/forums/index.php?PHPSESSID=23d5b5c9597f38cbab71a48da23299f8&topic=4429.0)

I would look for a Remastersys 2.0.5 Debian package and install that instead.

Or it might be better to just install Reconstructor.

---

### Post by Fragadelic on 2008-11-02
This is a very old topic - I just released version 2.0-9 which supports 8.10 Ubuntu/Kubuntu,etc.

---

### Post by red_team316 on 2008-11-03
> **Fragadelic said:**
> This is a very old topic - I just released version 2.0-9 which supports 8.10 Ubuntu/Kubuntu,etc.

True, but squashfs is still in development so dont be suprised if they throw more wrenches our way :P The hardy repos don't include the 1:3.3-7 yet :(

Reconstructor 2.8.1 also supports 8.10.


Keep up the good work Frag.

---

### Post by Fragadelic on 2008-11-23
Thanks.  I strangely didn't get notified of your reply.

---

