---
title: "Cannot install most recent updates"
date: 2008-11-12
forum: General Help
---

### Post by VTshredder on 2008-11-12
Today i get the usual notification that there are 16 updates available. 
Using the update manager, i was unable to install any of the updates.  Actually, once the files were "downloaded" they were unable to be installed and the Update Manager went out of control.

Tried to run the update via the terminal and get the same insanity.

This is the error i get:
```
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6704/task/6704/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6704/cwd' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6704/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6705/task/6705/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6705/task/6705/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6705/task/6705/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6705/task/6705/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6705/task/6705/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6705/task/6705/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6705/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6705/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6705/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6705/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6705/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6705/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6707/task/6707/fd/18: Not a directory
find: /etc/skel/.wine/dosdevices/z:/proc/6707/task/6707/fd/26: Not a directory
find: /etc/skel/.wine/dosdevices/z:/proc/6707/task/6707/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6707/task/6707/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6707/task/6707/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6707/task/6707/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6707/task/6707/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6707/task/6707/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6707/fd/18: Not a directory
find: /etc/skel/.wine/dosdevices/z:/proc/6707/fd/26: Not a directory
find: /etc/skel/.wine/dosdevices/z:/proc/6707/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6707/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6707/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6707/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6707/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6707/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6708/task/6708/fd/17: Not a directory
find: /etc/skel/.wine/dosdevices/z:/proc/6708/task/6708/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6708/task/6708/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6708/task/6708/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6708/task/6708/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6708/task/6708/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6708/task/6708/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6708/task/6814/fd/17: Not a directory
find: /etc/skel/.wine/dosdevices/z:/proc/6708/task/6814/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6708/task/6814/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6708/task/6814/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6708/task/6814/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6708/task/6814/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6708/task/6814/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6708/fd/17: Not a directory
find: /etc/skel/.wine/dosdevices/z:/proc/6708/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6708/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6708/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6708/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6708/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6708/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6715/task/6715/cwd' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6715/task/6715/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6715/task/6718/cwd' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6715/task/6718/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6715/cwd' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6715/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6736/task/6736/fd/5: Not a directory
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6736/task/6736/cwd' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6736/task/6736/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6736/fd/5: Not a directory
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6736/cwd' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6736/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6753/task/6753/cwd' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6753/task/6753/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6753/task/6754/cwd' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6753/task/6754/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6753/task/6755/cwd' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6753/task/6755/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6753/task/6756/cwd' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6753/task/6756/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6753/cwd' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6753/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6774/task/6774/fd/19: Not a directory
find: /etc/skel/.wine/dosdevices/z:/proc/6774/task/6774/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6774/task/6774/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6774/task/6774/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6774/task/6774/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6774/task/6774/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6774/task/6774/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6774/fd/19: Not a directory
find: /etc/skel/.wine/dosdevices/z:/proc/6774/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6774/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6774/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6774/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6774/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6774/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6775/task/6775/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6775/task/6775/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6775/task/6775/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6775/task/6775/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6775/task/6775/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6775/task/6775/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6775/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6775/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6775/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6775/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6775/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6775/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6778/task/6778/fd/16: Not a directory
find: /etc/skel/.wine/dosdevices/z:/proc/6778/task/6778/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6778/task/6778/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6778/task/6778/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6778/task/6778/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6778/task/6778/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6778/task/6778/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6778/fd/16: Not a directory
find: /etc/skel/.wine/dosdevices/z:/proc/6778/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6778/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6778/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6778/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6778/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6778/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6782/task/6782/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6782/task/6782/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6782/task/6782/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6782/task/6782/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6782/task/6782/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6782/task/6782/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6782/task/6805/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6782/task/6805/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6782/task/6805/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6782/task/6805/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6782/task/6805/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6782/task/6805/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6782/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6782/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6782/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6782/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6782/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6782/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6785/task/6785/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6785/task/6785/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6785/task/6785/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6785/task/6785/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6785/task/6785/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6785/task/6785/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6785/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6785/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6785/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6785/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6785/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6785/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6790/task/6790/fd/19: Not a directory
find: /etc/skel/.wine/dosdevices/z:/proc/6790/task/6790/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6790/task/6790/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6790/task/6790/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6790/task/6790/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6790/task/6790/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6790/task/6790/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6790/task/6933/fd/19: Not a directory
find: /etc/skel/.wine/dosdevices/z:/proc/6790/task/6933/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6790/task/6933/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6790/task/6933/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6790/task/6933/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6790/task/6933/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6790/task/6933/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6790/task/6934/fd/19: Not a directory
find: /etc/skel/.wine/dosdevices/z:/proc/6790/task/6934/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6790/task/6934/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6790/task/6934/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6790/task/6934/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6790/task/6934/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6790/task/6934/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6790/fd/19: Not a directory
find: /etc/skel/.wine/dosdevices/z:/proc/6790/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6790/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6790/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6790/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6790/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6790/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6791/task/6791/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6791/task/6791/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6791/task/6791/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6791/task/6791/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6791/task/6791/cwd/.wine/drive_c/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6791/task/6791/root' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: /etc/skel/.wine/dosdevices/z:/proc/6791/cwd/.gvfs: Permission denied
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6791/cwd/.idjc/profiles/default' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6791/cwd/.wine/dosdevices/z:' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
find: Symbolic link `/etc/skel/.wine/dosdevices/z:/proc/6791/cwd/.wine/dosdevices/c:/windows/profiles/eightvirtues/My Documents' is part of a loop in the directory hierarchy; we have already visited the directory to which it points.
dpkg: error processing base-files (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 base-files
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


The above error goes on and on insanely fast and i have to cancel it out each time....

Any ideas? (8.04 HH)

---

### Post by VTshredder on 2008-11-12
Bump since i updated the code i was getting....

---

### Post by VTshredder on 2008-11-12
Bump for the night crew...

:confused:

---

### Post by StephenF on 2008-11-13
/etc/skel/.wine/dosdevices/z

Presumably z is a symbolic link into the proc directory which contains many circular references. I would try deleting this and possibly recreate it afterwards if wine stops working.

---

### Post by hansdown on 2008-11-13
Hi VTshredder.

When the update manager shows you the list of downloads, you can scroll through the list and uncheck the ones you don't want. I'd highly recomend this for the wine downloads, because that particular problem may not be fixed yet. Just going by your previous thread.

---

### Post by stlouisubntu on 2008-11-27
Bump!!  Same problem.

To:  OP:  Were you ever able to solve or workaround this?  If
so, please advise what you did.

I am unable not only to install updates but also am unable to 
install additional software packages.

I would gladly delete the symbolic links if I knew what they
were (I know to sudo rm but what's the problematic link I need
to remove?)

tried sudo dpkg --configure -a
and from full root  # sudo dpkg --configure -a
and get into the same endless loop and the OP.

Please advise.  The only other fix I can think of 
are rather draconian measures of deleting entire folders / directories
(mentioned in the output.)

Thanks in advance for any further thoughts.

---

### Post by stlouisubntu on 2008-11-28
> **StephenF said:**
> /etc/skel/.wine/dosdevices/z

Presumably z is a symbolic link into the proc directory which contains many circular references. I would try deleting this and possibly recreate it afterwards if wine stops working.


Thanks.

What worked was deleting the symbolic links by

sudo rm /etc/skel/.wine/dosdevices/z:

These seemed to be numerous links, so I am not 
going to attempt to recreate them at this time.

It seemed like it had to do with running old dos 
programs under wine (which has never been done
on this PC anyway and problably never will be.)

It might be quite some time before I discover what
the negative impact of this will be, if any.

However, it is still puzzling and disturbing what
caused this in the first place.

Thanks.

---

### Post by hansdown on 2008-11-28
Hi guys.

Please look at the following....

[http://www.google.ca/search?q=viruses+in+wine+in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=viruses+in+wine+in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

I hope you will be helped by these links.

---

### Post by jpeddicord on 2008-11-28
Woah, /etc/skel/.wine should not exist at all unless you specifically put that there. Go ahead and remove it: press Alt+F2 and enter **gksu nautilus /etc/skel** then go to View > Show Hidden Files on the window that opens. Remove the .wine directory, close the window, and you're all set.

---

