---
title: "No package python-kde3 after upgrade, python segfault"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by nusch on 2009-10-30
I've some PyKDE3 app which I'm porting to Qt4, after upgrade to jaunty the app can't launch SEGFAULTing.
Here is backtrace:
```

Program received signal SIGSEGV, Segmentation fault.
strlen () at ../sysdeps/x86_64/strlen.S:31          
31      ../sysdeps/x86_64/strlen.S: No such file or directory.
        in ../sysdeps/x86_64/strlen.S
Current language:  auto
The current source language is "auto; currently asm".
(gdb) bt
#0  strlen () at ../sysdeps/x86_64/strlen.S:31
#1  0x0000000000461c41 in PyString_FromFormatV ()
#2  0x00000000004b062e in PyErr_Format ()
#3  0x00007ffff2326433 in ?? () from /usr/lib/pymodules/python2.6/sip.so
#4  0x00007ffff1f80bdf in initkdecore () from /usr/lib/python2.6/dist-packages/kdecore.so
#5  0x00000000004ba4bc in _PyImport_LoadDynamicModule ()
#6  0x00000000004b8a23 in ?? ()
#7  0x00000000004b8caf in ?? ()
#8  0x00000000004b924c in ?? ()
#9  0x00000000004b98b4 in PyImport_ImportModuleLevel ()
#10 0x000000000049c1cb in ?? ()
#11 0x000000000041d6e7 in PyObject_Call ()
#12 0x000000000049cd8f in ?? ()
#13 0x000000000049fc8e in PyEval_EvalFrameEx ()
#14 0x00000000004a40e0 in PyEval_EvalCodeEx ()
#15 0x00000000004a41b2 in PyEval_EvalCode ()
#16 0x00000000004c33a0 in PyRun_FileExFlags ()
#17 0x00000000004c3564 in PyRun_SimpleFileExFlags ()
#18 0x0000000000418ab7 in Py_Main ()
#19 0x00007ffff6fd0abd in __libc_start_main (main=<value optimized out>, argc=<value optimized out>, ubp_av=<value optimized out>, init=<value optimized out>,
    fini=<value optimized out>, rtld_fini=<value optimized out>, stack_end=0x7fffffffe238) at libc-start.c:220
#20 0x0000000000417ca9 in _start ()

```

The partialy parted app with pure Qt works ok.
Tried to:
```
apt-get --reinstall install python-kde3
```
but it gives me info that the package can't be downloaded. Is there any way to install it without breaking current kde4 system ? In 9.04 python-kde4 and python-kde3 coexistenced well.

---

