---
title: "Permissin denied during wupi install into Vista"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by Thulemanden on 2009-10-19
The Ubuntu 9.04 stops during the wupi install into Vista Home Basic with some permission errors.

The basic dual boot install also failed, as Grub and the choice of OS didn't pop up.

Also PCLinuxOS failed as Mint Linux. There is plenty of space avilable som 30 GB,

10-19 19:13 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
10-19 19:13 DEBUG  TaskList: # Cancelling tasklist
10-19 19:13 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied

---

### Post by Mark Phelps on 2009-10-21
When you run the .exe file, right-click it and select "Run as Administrator".  That will elevate permissions for the Wubi file to Trusted Installer and should work after that.

---

