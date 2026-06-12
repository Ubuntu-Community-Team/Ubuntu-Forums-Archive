---
title: "[SOLVED] too many /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/2"
date: 2008-07-21
forum: General Help
---

### Post by prince_niceguy on 2008-07-21
When I run the following command in the terminal

ps -aef|grep <my user name>

It list the following

user 15648 15646 0 13:05 ? 00:00:00 /usr/bin/gtk-window-decorator
user 15659 1 0 13:05 ? 00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
user 15660 1 0 13:05 ? 00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
user 15668 1 0 13:05 ? 00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
user 15669 1 0 13:05 ? 00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
user 15675 1 0 13:05 ? 00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
user 15677 1 0 13:05 ? 00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
user 15690 1 0 13:05 ? 00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
user 15692 1 0 13:05 ? 00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
user 15699 1 0 13:05 ? 00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
user 15700 1 0 13:05 ? 00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
user 15702 1 0 13:05 ? 00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
user 15704 1 0 13:05 ? 00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
user 15711 1 0 13:05 ? 00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
user 15712 1 0 13:05 ? 00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/1

along with many other processes. Is this normal or is it a bug in gvfs some where?

---

### Post by ibuclaw on 2008-07-21
Yes, that does seem a bit odd...

Have you moved quite a lot of files to the trash recently?

Have you rebooted and checked that it is still there?

Regards
Iain

---

### Post by prince_niceguy on 2008-07-21
Yup this is after reboot. I have noted it some time ago thought would report it too. Have not filed a bug yet.

---

### Post by ibuclaw on 2008-07-21
Be sure to include your hardware stats if you do.

```
sudo lshw -short
```

But first, I recommend that you perhaps should back everything up and try a reinstall. As something has gone wrong in your configuring somewhere.

Regards
Iain

---

### Post by prince_niceguy on 2008-07-21
Reinstall :O ... Well I am not so much worried about the processes to run. I have another box running ubuntu. Will check that too to see if it is happening or not.

---

### Post by prince_niceguy on 2008-07-24
well i found out where the issue is. I reinstalled ubuntu and found that the number of trash processes were reduced. After that I installed avant window navigator from the launch pad and seems it is the culprit ... Now I have disabled it and the number of processes have gone down.

---

### Post by southerngrey on 2009-02-27
As an update to this bug.  I was having the same problem on hardy running as a virtual machine hosted by another hardy box.

After checking my automount drives I found one that had somehow developed multiple trash folders.  After I deleted the additionals the problem went away.  I'm not sure but I suspect it has something to do with trying to reconcile multiple indexes for the gvfsd-trash process.

If you're having the problem I suspect this is the real culprit, search your automount drives and eliminate any additional trash folders.

---

### Post by prince_niceguy on 2009-02-27
well i have now started using kde 4.2... I am exploring new features every day and I am quite impressed by it. I do go to gnome from time to time but some how gnome now feels out of touch with greatest thing and also gnome + compiz is taking more memory compared to kde 4.2 with desktop effects on...

---

