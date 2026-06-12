---
title: "Error 22 on ubunu 9.04 install to windows"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by Givey51 on 2009-07-27
Error (22)Invalid argument while trying to install ubuntu 9.04 in Windows? No experience with ubuntu. Log below:

07-23 21:35 DEBUG  TaskList: ## Finished copy_installation_files
07-23 21:35 DEBUG  TaskList: ## Running get_iso...
07-23 21:35 DEBUG  TaskList: New task copy_file
07-23 21:35 DEBUG  TaskList: ### Running copy_file...
07-23 21:37 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 22] Invalid argument
07-23 21:37 DEBUG  TaskList: # Cancelling tasklist
07-23 21:37 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\appl

---

