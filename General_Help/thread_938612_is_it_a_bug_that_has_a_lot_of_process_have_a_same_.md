---
title: "is it a bug that has a lot of process have a same name?"
date: 2008-10-05
forum: General Help
---

### Post by Kelen.Chang on 2008-10-05
sometimes i finds a lot of process have a same name, special after restart X servers. is it a bug or something wrong with me? How to fix it?:(

---

### Post by tonybaqain on 2008-10-05
can you paste an example ?

---

### Post by Calmatory on 2008-10-05
They might be child processes. The way Linux handles them and threads is somewhat different from Windows.

As far as I know, in Linux, the every child process is listed as their own entry, in top for example. In Windows the parent process is only shown in Task Manager.

---

### Post by wdaniels on 2008-10-05
I seem to remember that nautilus preloads a couple of instances and you may well see multiple shell processes (e.g. sh, bash) at times, or even things like the python interpreter, so no, it's probably not a bug, but you need to post examples to be sure.

---

### Post by Kelen.Chang on 2008-10-06
okay, after twice restart X. i finds some processes as follow. 
is that a bug for hardy or some wrong with me?  
```
firefox@ubuntu:~$ ps -e |grep bash && ps -e |grep dbus-daemon && ps -e |gre
p gvfsd && ps -e |grep gvfsd-burn && ps -e |grep gvfsd-trash && ps -e |grep
 scim-launcher && ps -e |grep trackerd
 6594 pts/1    00:00:00 bash
 9105 pts/0    00:00:00 bash
 5297 ?        00:00:01 dbus-daemon
 6021 ?        00:00:00 dbus-daemon
 7703 ?        00:00:00 dbus-daemon
 8765 ?        00:00:00 dbus-daemon
 6103 ?        00:00:00 gvfsd
 6202 ?        00:00:00 gvfsd-burn
 6272 ?        00:00:00 gvfsd-trash
 7748 ?        00:00:00 gvfsd
 7820 ?        00:00:00 gvfsd-trash
 7953 ?        00:00:00 gvfsd-burn
 8811 ?        00:00:00 gvfsd
 8864 ?        00:00:00 gvfsd-trash
 8969 ?        00:00:00 gvfsd-burn
 6202 ?        00:00:00 gvfsd-burn
 7953 ?        00:00:00 gvfsd-burn
 8969 ?        00:00:00 gvfsd-burn
 6272 ?        00:00:00 gvfsd-trash
 7820 ?        00:00:00 gvfsd-trash
 8864 ?        00:00:00 gvfsd-trash
 8778 ?        00:00:00 scim-launcher
 8835 ?        00:00:00 scim-launcher
 6152 ?        00:00:00 trackerd
 7844 ?        00:00:00 trackerd
 8907 ?        00:00:00 trackerd
firefox@ubuntu:~$ 

```

---

### Post by Calmatory on 2008-10-06
There is something wrong there, at least if mine is correct:
```

asdman@asdman-laptop:~$ ps -e |grep bash && ps -e |grep dbus-daemon && ps -e |grep gvfsd && ps -e |grep gvfsd-burn && ps -e |grep gvfsd-trash && ps -e |grep scim-launcher && ps -e |grep trackerd
23612 pts/0    00:00:00 bash
 4911 ?        00:00:04 dbus-daemon
 5776 ?        00:00:09 dbus-daemon
 5824 ?        00:00:00 gvfsd
 5913 ?        00:00:14 gvfsd-trash
 5928 ?        00:00:00 gvfsd-burn
 9026 ?        00:00:00 gvfsd-computer
 5928 ?        00:00:00 gvfsd-burn
 5913 ?        00:00:14 gvfsd-trash

```
However, system configurations might have great influences in this, but still that many multiple processes is abnormal(if not, someone correct me. ;)).

---

### Post by Kelen.Chang on 2008-10-06
so, this is a big bug for hardy. right?

---

