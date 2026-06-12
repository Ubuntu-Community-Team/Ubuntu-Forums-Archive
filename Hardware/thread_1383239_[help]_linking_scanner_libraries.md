---
title: "[help] linking scanner libraries"
date: 2010-01-17
forum: Hardware
---

### Post by Curvature_Tensor on 2010-01-17
+Problem:
iscan (official epson drivers) installs the epkowa files in the wrong directory.  What I mean is,

the iscan package installs

/usr/lib/sane/libsane-epkowa.so.1.0.15
/usr/lib/sane/libsane-epkowa.so.1
/usr/lib/sane/libsane-epkowa.la

But when I run "sudo strace -Ff -tt iscan  2>&1 | tee iscan_info.txt" I see iscan is trying to call

/usr/local/lib/sane/libsane-epkowa.so.1

Is there a way to tell iscan to look in /usr/lib/sane?

+Background Info:
Ubuntu 9.10
scanner: Epson NX400 all-in-one
iscan package used: iscan_2.23.0-3.ltdl7_i386.deb

I have already edited the epkowa.conf, dll.conf, and 45-libsane.rules files 
(see [http://ubuntuforums.org/showthread.php?t=627471](http://ubuntuforums.org/showthread.php?t=627471) for more info)

+Attempted Solution:
1. Manually copy/pasted libsane-epkowa.so.1 to /usr/local/lib/sane/, this lead to a segmentation default error.

running "sudo gdb iscan"

"Program received signal SIGSEGV, Segmentation fault.
0x04b2544e in ?? () from /usr/local/lib/sane/libsane-epkowa.so.1"

2. Tried symbolic linking, this also lead to a segmentation default error

To create link:
"ln -s /usr/lib/sane/libsane-epkowa.so.1 /usr/local/lib/sane/libsane-epkowa.so.1"

running "sudo gdb iscan"

"Program received signal SIGSEGV, Segmentation fault.
0x024ad44e in ?? () from /usr/local/lib/sane/libsane-epkowa.so.1"

3. Tried editing /etc/ld.so.conf to include the files, did not make any difference.

include /usr/lib/sane/libsane-epkowa.so.1.0.15
include /usr/lib/sane/libsane-epkowa.so.1
include /usr/lib/sane/libsane-epkowa.la

-----------------------
Thank you!

---

