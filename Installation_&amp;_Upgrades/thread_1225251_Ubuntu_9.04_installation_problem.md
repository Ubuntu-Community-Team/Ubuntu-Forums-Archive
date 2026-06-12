---
title: "Ubuntu 9.04 installation problem"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by anuj27 on 2009-07-28
I am trying to install Ubuntu 9.04 inside Windows XP and getting the following errors in the log file.

07-28 19:26 DEBUG  TaskList: ## Running get_iso...
07-28 19:26 DEBUG  TaskList: New task copy_file
07-28 19:26 DEBUG  TaskList: ### Running copy_file...
07-28 19:30 DEBUG  TaskList: ### Finished copy_file
07-28 19:30 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
07-28 19:30 DEBUG  TaskList: # Cancelling tasklist
07-28 19:30 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
07-28 19:30 DEBUG  TaskList: New task check_iso
07-28 19:30 DEBUG  CommonBackend: Searching for local ISO
07-28 19:30 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-28 19:30 DEBUG  TaskList: New task get_metalink
07-28 19:30 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-28 19:30 DEBUG  TaskList: # Cancelling tasklist

---

### Post by dstew on 2009-07-28
Are you running with administrator privileges in Windows? It looks like you need to be.

---

### Post by anuj27 on 2009-07-29
Yes i am the administrator

---

### Post by dstew on 2009-07-29
It looks like it is failing with permission denied to copy a file. I don't know much about Windows 7. Are there file permissions that you have to change, like Linux? Is there a "superuser" equivalent?

Do you have an encrypted filesystem, or a RAID that might cause problems with a file copy routine? I don't have too many other ideas for you.

---

### Post by anuj27 on 2009-07-29
i am using Windows Xp, not Windows 7

---

### Post by dstew on 2009-07-30
In that case, I don't think file permissions is the problem. Could disk space be an issue?

---

### Post by RMD94 on 2009-07-31
> **dstew said:**
> In that case, I don't think file permissions is the problem. Could disk space be an issue?

i'm having the same problem and i have xp and i don't have any space problems...

---

### Post by dstew on 2009-07-31
Is the problem only with 9.04? Try installing 8.04 instead. Maybe there is a bug in the installer.

---

### Post by RMD94 on 2009-07-31
i had some problems with my driver so i had to restore my computer and b4 restoring my comp i had installed wubi 9.04 and it was a sucessful installation. now after restoring my comp it keep's giving me errors...

---

### Post by anuj27 on 2009-09-21
Instead of the Ubuntu installation CD, i mounted the image in my virtual drive and tried installing through it and it worked fine. When computer had to restart, then i used the CD and installation was successful.
There was no error in the disc as i tried even with a newly writted CD from the same CD image. So it must be an error with the Ubuntu installer (i dont know anything about it, just guessing.)
Anyways my problem is solved and i am fine with it :).

---

