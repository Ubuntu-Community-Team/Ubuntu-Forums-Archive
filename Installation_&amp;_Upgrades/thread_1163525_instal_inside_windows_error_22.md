---
title: "instal inside windows error 22"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by myschief on 2009-05-18
i've tried to install ubuntu inside windows a few times, and i keep getting this error:

> 05-18 14:53 DEBUG  TaskList: ### Running copy_file...
05-18 14:58 DEBUG  TaskList: ### Finished copy_file
05-18 14:58 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 22] Invalid argument
05-18 14:58 DEBUG  TaskList: # Cancelling tasklist
05-18 14:58 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 22] Invalid argument
05-18 14:58 DEBUG  TaskList: New task check_iso
05-18 14:58 DEBUG  CommonBackend: Searching for local ISO
05-18 14:58 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-18 14:58 DEBUG  TaskList: New task get_metalink
05-18 14:58 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-18 14:58 DEBUG  TaskList: # Cancelling tasklist
05-18 14:58 DEBUG  TaskList: # Finished tasklist
05-18 15:02 INFO   root: === wubi 9.04 rev128 ===i have also gotten errors saying no CD when there is one in my only cd/dvd drive.

help!

---

