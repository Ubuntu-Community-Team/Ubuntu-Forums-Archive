---
title: "Wubi is interesting but without GUI is useless"
date: 2008-09-27
forum: General Help
---

### Post by sandbird on 2008-09-27
Installed it.
Got a command line prompt when I tried to boot it.

Let me know when this Wubi thing will be able to run X.

---

### Post by davidryder on 2008-09-27
Wubi worked fine for me. No problems at all. There are some problems with that made me switch to an actual install but it definitely worked. 

I know a lot of people are having problems with it though.

---

### Post by gnuvistawouldbecool on 2008-09-27
Did it actually go straight to a command line, or did it give some error messages first?  Because if it went straight to a CLI, that sounds like the server install, unless I'm mistaken.

---

### Post by Orlsend on 2008-09-27
> **gnuvistawouldbecool said:**
> Did it actually go straight to a command line, or did it give some error messages first?  Because if it went straight to a CLI, that sounds like the server install, unless I'm mistaken.
**Agreed**

---

### Post by ago on 2008-09-27
It might be that your video card is not supported. Press esc at boot and select rescue mode or safe graphic mode.

---

### Post by sandbird on 2008-09-28
There's re no error messages, not even on verbose mode.

All the modes have the same result - some console prompt called "BusyBox" or something like that. It has no X stuff installed.

Also:

LiveCD working fine (except for making some graphics setting problems on my Windows XP).

---

### Post by -Zeus- on 2008-09-28
you're sure you have the desktop install?  You could try installing it not with Wubi, I think that's better.

---

### Post by sandbird on 2008-09-28
Somehow the ISO was "amd64" and I have Intel CPU :)

I'll download the 32bit version.

---

### Post by Ptero-4 on 2008-09-28
You say you got intel CPU. Is it a Pentium DualCore/Core2Duo/Core2Quad? If it is then you do have a 64bit CPU. The problem isn't due to the CPU arch it chose (if you had a 32bit CPU it would complain about not supporting long instructions and wouldn't even get as far as busybox). The fact you got busybox means that it probably couldn't detect your HD controller.
BTW: amd64=x86-64. It works both for intel and AMD 64bit CPU's.

---

### Post by sandbird on 2008-09-28
> **Ptero-4 said:**
> You say you got intel CPU. Is it a Pentium DualCore/Core2Duo/Core2Quad? If it is then you do have a 64bit CPU. The problem isn't due to the CPU arch it chose (if you had a 32bit CPU it would complain about not supporting long instructions and wouldn't even get as far as busybox). The fact you got busybox means that it probably couldn't detect your HD controller.
BTW: amd64=x86-64. It works both for intel and AMD 64bit CPU's.

Yes, I have SATA on mode SATA.
Dead end for me.

---

### Post by ago on 2008-09-29
If you have raid or encrypted disks, wubi will not work
Otherwise uninstall, run chkdsk /r and try again, if it stops type

cat /proc/cmdline
cat /proc/partitions
grep err /casper.log
grep mount /casper.log

and post here the output

---

