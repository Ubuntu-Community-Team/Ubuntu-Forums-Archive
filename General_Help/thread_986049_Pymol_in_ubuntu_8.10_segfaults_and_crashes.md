---
title: "Pymol in ubuntu 8.10 segfaults and crashes"
date: 2008-11-18
forum: General Help
---

### Post by garg on 2008-11-18
Hi,

I need assistance troubleshooting this. I'm trying to get pymol [http://www.pymol.org](http://www.pymol.org) to run. It worked fine in 8.04 but whether I install it via apt-get or built it from source, it crashes in 8.10. 

When I run pymol in Ubuntu 8.10, I get a segmentation fault if I do
 the following:

 1. Go to Help > Pymol
 2. Go to Plugin > Apbs tools > and click on any button for example
 Choose Externally Generated PQR, or Run APBS or any other button
 Hit ESC anytime to toggle between text and graphics.

If I run it with strace and do Help > Pymol then I get the following:
> 
 OpenGL graphics engine:
  GL_VENDOR: NVIDIA Corporation
  GL_RENDERER: GeForce 7900 GS/PCI/SSE2
  GL_VERSION: 2.1.2 NVIDIA 177.80
 Adapting to GeForce hardware.
 Detected 2 CPU cores.  Enabled multithreaded rendering.
[{WIFSIGNALED(s) && WTERMSIG(s) == SIGSEGV}], 0, NULL) = 23630
--- SIGCHLD (Child exited) @ 0 (0) ---
write(2, "Segmentation fault\n", 19Segmentation fault
)    = 19
read(10, "", 8192)                      = 0
exit_group(139)                         = ?
Process 23629 detached



If I run it with gdb I get the following:


>  OpenGL graphics engine:
  GL_VENDOR: NVIDIA Corporation
  GL_RENDERER: GeForce 7900 GS/PCI/SSE2
  GL_VERSION: 2.1.2 NVIDIA 177.80
 [New Thread 0xb4ee0b90 (LWP 17068)]
 [New Thread 0xb46dfb90 (LWP 17069)]
 Adapting to GeForce hardware.
 Detected 2 CPU cores.  Enabled multithreaded rendering.
 [New Thread 0xb3c84b90 (LWP 17085)]
 [Thread 0xb3c84b90 (LWP 17085) exited]

 Program received signal SIGSEGV, Segmentation fault.
 [Switching to Thread 0xb46dfb90 (LWP 17069)]
 0x00000000 in ?? ()
 (gdb) quit



Bt full gives:


 The following is output from 'bt full'

>  Program received signal SIGSEGV, Segmentation fault.
 [Switching to Thread 0xb4722b90 (LWP 17866)]
 0x00000000 in ?? ()
 (gdb) bt full
 #0  0x00000000 in ?? ()
 No symbol table info available.
 #1  0xb5149385 in ?? () from /usr/lib/libBLT.2.4.so.8.4
 No symbol table info available.
 #2  0xb51495a0 in ?? () from /usr/lib/libBLT.2.4.so.8.4
 No symbol table info available.
 #3  0xb4f5d5ce in TclInvokeStringCommand ()
 from /usr/lib/libtcl8.4.so.0 No symbol table info available.
 #4  0xb4f5e94e in TclEvalObjvInternal () from /usr/lib/libtcl8.4.so.0
 No symbol table info available.
 #5  0xb4f5ec10 in Tcl_EvalObjv () from /usr/lib/libtcl8.4.so.0
 No symbol table info available.
 #6  0xb51eca1d in ?? ()
 from /usr/lib/python2.5/lib-dynload/_tkinter.so No symbol table info
 available. #7  0x080cea39 in PyEval_EvalFrameEx ()
 No symbol table info available.
 #8  0x080d0345 in PyEval_EvalCodeEx ()
 No symbol table info available.
 #9  0x080ce728 in PyEval_EvalFrameEx ()
 No symbol table info available.
 #10 0x080cfbf5 in PyEval_EvalFrameEx ()
 No symbol table info available.
 #11 0x080d0345 in PyEval_EvalCodeEx ()
 ---Type <return> to continue, or q <return> to quit---
 No symbol table info available.
 #12 0x080ce728 in PyEval_EvalFrameEx ()
 No symbol table info available.
 #13 0x080cfbf5 in PyEval_EvalFrameEx ()
 No symbol table info available.
 #14 0x080d0345 in PyEval_EvalCodeEx ()
 No symbol table info available.
 #15 0x08117891 in ?? ()
 No symbol table info available.
 #16 0x0805d867 in PyObject_Call ()
 No symbol table info available.
 #17 0x080c850c in PyEval_CallObjectWithKeywords ()
 No symbol table info available.
 #18 0x080c7ed4 in ?? ()
 No symbol table info available.
 #19 0x080cea39 in PyEval_EvalFrameEx ()
 No symbol table info available.
 #20 0x080d0345 in PyEval_EvalCodeEx ()
 No symbol table info available.
 #21 0x08117891 in ?? ()
 No symbol table info available.
 #22 0x0805d867 in PyObject_Call ()
 No symbol table info available.
 ---Type <return> to continue, or q <return> to quit---
 #23 0x08063a7a in ?? ()
 No symbol table info available.
 #24 0x0805d867 in PyObject_Call ()
 No symbol table info available.
 #25 0x080c850c in PyEval_CallObjectWithKeywords ()
 No symbol table info available.
 #26 0xb51ea097 in ?? ()
 from /usr/lib/python2.5/lib-dynload/_tkinter.so No symbol table info
 available. #27 0xb4f5d5ce in TclInvokeStringCommand ()
 from /usr/lib/libtcl8.4.so.0 No symbol table info available.
 #28 0xb4f5e94e in TclEvalObjvInternal () from /usr/lib/libtcl8.4.so.0
 No symbol table info available.
 #29 0xb4f8ad71 in ?? () from /usr/lib/libtcl8.4.so.0
 No symbol table info available.
 #30 0xb4f88db8 in TclCompEvalObj () from /usr/lib/libtcl8.4.so.0
 No symbol table info available.
 #31 0xb4f5fc24 in Tcl_EvalObjEx () from /usr/lib/libtcl8.4.so.0
 No symbol table info available.
 #32 0xb504eea0 in TkInvokeMenu () from /usr/lib/libtk8.4.so.0
 No symbol table info available.
 #33 0xb504ea76 in ?? () from /usr/lib/libtk8.4.so.0
 No symbol table info available.
 #34 0xb4f5e94e in TclEvalObjvInternal () from /usr/lib/libtcl8.4.so.0
 ---Type <return> to continue, or q <return> to quit---
 No symbol table info available.
 #35 0xb4f5ec10 in Tcl_EvalObjv () from /usr/lib/libtcl8.4.so.0
 No symbol table info available.
 #36 0xb4f5fd6b in Tcl_EvalObjEx () from /usr/lib/libtcl8.4.so.0
 No symbol table info available.
 #37 0xb4fc0af6 in Tcl_UplevelObjCmd () from /usr/lib/libtcl8.4.so.0
 No symbol table info available.
 #38 0xb4f5e94e in TclEvalObjvInternal () from /usr/lib/libtcl8.4.so.0
 No symbol table info available.
 #39 0xb4f8ad71 in ?? () from /usr/lib/libtcl8.4.so.0
 No symbol table info available.
 #40 0xb4f88db8 in TclCompEvalObj () from /usr/lib/libtcl8.4.so.0
 No symbol table info available.
 #41 0xb4fc107e in TclObjInterpProc () from /usr/lib/libtcl8.4.so.0
 No symbol table info available.
 #42 0xb4f5e94e in TclEvalObjvInternal () from /usr/lib/libtcl8.4.so.0
 No symbol table info available.
 #43 0xb4f5f812 in Tcl_EvalEx () from /usr/lib/libtcl8.4.so.0
 No symbol table info available.
 #44 0xb500e989 in Tk_BindEvent () from /usr/lib/libtk8.4.so.0
 No symbol table info available.
 #45 0xb50152c7 in TkBindEventProc () from /usr/lib/libtk8.4.so.0
 No symbol table info available.
 ---Type <return> to continue, or q <return> to quit---
 #46 0xb501ddc9 in Tk_HandleEvent () from /usr/lib/libtk8.4.so.0
 No symbol table info available.
 #47 0xb501e628 in ?? () from /usr/lib/libtk8.4.so.0
 No symbol table info available.
 #48 0xb4fb53eb in Tcl_ServiceEvent () from /usr/lib/libtcl8.4.so.0
 No symbol table info available.
 #49 0xb4fb5719 in Tcl_DoOneEvent () from /usr/lib/libtcl8.4.so.0
 No symbol table info available.
 #50 0xb51e7f01 in ?? ()
 from /usr/lib/python2.5/lib-dynload/_tkinter.so No symbol table info
 available. #51 0x080cea39 in PyEval_EvalFrameEx ()
 No symbol table info available.
 #52 0x080d0345 in PyEval_EvalCodeEx ()
 No symbol table info available.
 #53 0x080ce728 in PyEval_EvalFrameEx ()
 No symbol table info available.
 #54 0x080d0345 in PyEval_EvalCodeEx ()
 No symbol table info available.
 #55 0x080ce728 in PyEval_EvalFrameEx ()
 No symbol table info available.
 #56 0x080d0345 in PyEval_EvalCodeEx ()
 No symbol table info available.
 #57 0x0811797e in ?? ()
 ---Type <return> to continue, or q <return> to quit---
 No symbol table info available.
 #58 0x0805d867 in PyObject_Call ()
 No symbol table info available.
 #59 0x080cd502 in PyEval_EvalFrameEx ()
 No symbol table info available.
 #60 0x080cfbf5 in PyEval_EvalFrameEx ()
 No symbol table info available.
 #61 0x080cfbf5 in PyEval_EvalFrameEx ()
 No symbol table info available.
 #62 0x080d0345 in PyEval_EvalCodeEx ()
 No symbol table info available.
 #63 0x08117891 in ?? ()
 No symbol table info available.
 #64 0x0805d867 in PyObject_Call ()
 No symbol table info available.
 #65 0x08063a7a in ?? ()
 No symbol table info available.
 #66 0x0805d867 in PyObject_Call ()
 No symbol table info available.
 #67 0x080c850c in PyEval_CallObjectWithKeywords ()
 No symbol table info available.
 #68 0x080f9e68 in ?? ()
 No symbol table info available.
 ---Type <return> to continue, or q <return> to quit---
 #69 0xb7f5250f in start_thread ()
 from /lib/tls/i686/cmov/libpthread.so.0 No symbol table info
 available. #70 0xb7ea07ee in clone ()
 from /lib/tls/i686/cmov/libc.so.6 No symbol table info available.


I don't know why it is crashing. 
 I have tried version 0_99, 1, 1.1 and I also tried building from
 source ( svn co [https://pymol.svn.sourceforge.net/svnroot/pymol](https://pymol.svn.sourceforge.net/svnroot/pymol)
 pymol ) but I get the same exact problem.

 I have tried this with Ubuntu 8.10 with nvidia quadro fx3700. nvidia
 geforce 7900, an ATI card but they all give the same problem.

 However, we have other machines not running ubuntu 8.10 with python
 2.5.1 and pymol works perfectly on those.

 Is there anything else I can try and do you require any extra
 information?

Please help :confused:

---

### Post by garg on 2008-11-19
Still no luck here. Can any one provide me with some ideas on what to try next?

---

