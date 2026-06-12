---
title: "Firefox 3.0.5 crashes when receiving &quot;Page cannot be loaded&quot;"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by cpradio on 2009-01-04
When using Firefox 3.0.5 for the past 3 days, it is consistently crashing when the url I am trying to open throws a "Page cannot be loaded" error.  I have tried purging firefox (and re-installing it) and creating a new profile.  All result in the same error being thrown.

Here is the information from running firefox in the console
```
FirebugService fbs.DBG_FBS_CREATION: false fbs.DBG_FBS_BP:false fbs.DBG_FBS_ERRORS:false fbs.DBG_FBS_STEP:false fbs.DBG_FBS_FUNCTION:false
*** e = [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: chrome://browser/content/utilityOverlay.js :: getShellService :: line 307"  data: no]
debugger.onModuleDeactivate Attempt to deactive context that is not active http://cpradio.org/
debugger.onModuleDeactivate Attempt to deactive context that is not active http://cpradio.org/
debugger.onModuleDeactivate Attempt to deactive context that is not active http://cpradio.org/
ERROR: ld.so: object '/usr/$LIB/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
QPixmap: Invalid pixmap parameters
The program 'firefox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 15307 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f636dcfd9fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x17) [0x7f636dcfdb77]
#2 /usr/lib/libX11.so.6 [0x7f63705f28c0]
#3 /usr/lib/libXrender.so.1(XRenderFreePicture+0x46) [0x7f63708b5a26]
#4 /usr/lib/libQtGui.so.4 [0x7f6365f7fcfb]
#5 /usr/lib/libQtGui.so.4 [0x7f6365f80680]
#6 /usr/lib/libQtGui.so.4(_ZN7QPixmap5derefEv+0x53) [0x7f6365f75fa3]
#7 /usr/lib/libQtGui.so.4(_ZN7QPixmapD1Ev+0x24) [0x7f6365f762e4]
#8 /usr/lib/libQtGui.so.4 [0x7f63660580bb]
#9 /usr/lib/libQtGui.so.4 [0x7f6366050819]
#10 /usr/lib/libQtGui.so.4 [0x7f6365f7fc58]
#11 /usr/lib/libQtGui.so.4 [0x7f6365f80680]
#12 /usr/lib/libQtGui.so.4(_ZN7QPixmap5derefEv+0x53) [0x7f6365f75fa3]
#13 /usr/lib/libQtGui.so.4(_ZN7QPixmapD2Ev+0x24) [0x7f6365f76334]
#14 /usr/lib/libQtGui.so.4 [0x7f6365f7b193]
#15 /usr/lib/libQtGui.so.4 [0x7f6365f7b79f]
#16 /usr/lib/libQtGui.so.4 [0x7f6365f7ae85]
#17 /lib/libc.so.6(exit+0x9d) [0x7f6374cb766d]
#18 /usr/lib/libgdk-x11-2.0.so.0 [0x7f636f943c81]
#19 /usr/lib/libX11.so.6(_XError+0xf4) [0x7f63705eb784]
```

Am I the only one experiencing this issue on a consistent basis?

---

### Post by cpradio on 2009-01-04
I also ran firefox -sync based on the above messages, and got the following:
```
cpradio:~$ firefox -sync
FirebugService fbs.DBG_FBS_CREATION: false fbs.DBG_FBS_BP:false fbs.DBG_FBS_ERRORS:false fbs.DBG_FBS_STEP:false fbs.DBG_FBS_FUNCTION:false
*** e = [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: chrome://browser/content/utilityOverlay.js :: getShellService :: line 307"  data: no]
debugger.onModuleDeactivate Attempt to deactive context that is not active http://cpradio.org/
debugger.onModuleDeactivate Attempt to deactive context that is not active http://cpradio.org/
ERROR: ld.so: object '/usr/$LIB/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
QPixmap: Invalid pixmap parameters
The program 'firefox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 12034 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f7802ecf9fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x17) [0x7f7802ecfb77]
#2 /usr/lib/libX11.so.6 [0x7f78057c48c0]
#3 /usr/lib/libXrender.so.1(XRenderFreePicture+0x46) [0x7f7805a87a26]
#4 /usr/lib/libQtGui.so.4 [0x7f77fb151cfb]
#5 /usr/lib/libQtGui.so.4 [0x7f77fb152680]
#6 /usr/lib/libQtGui.so.4(_ZN7QPixmap5derefEv+0x53) [0x7f77fb147fa3]
#7 /usr/lib/libQtGui.so.4(_ZN7QPixmapD1Ev+0x24) [0x7f77fb1482e4]
#8 /usr/lib/libQtGui.so.4 [0x7f77fb22a0bb]
#9 /usr/lib/libQtGui.so.4 [0x7f77fb222819]
#10 /usr/lib/libQtGui.so.4 [0x7f77fb151c58]
#11 /usr/lib/libQtGui.so.4 [0x7f77fb152680]
#12 /usr/lib/libQtGui.so.4(_ZN7QPixmap5derefEv+0x53) [0x7f77fb147fa3]
#13 /usr/lib/libQtGui.so.4(_ZN7QPixmapD2Ev+0x24) [0x7f77fb148334]
#14 /usr/lib/libQtGui.so.4 [0x7f77fb14d193]
#15 /usr/lib/libQtGui.so.4 [0x7f77fb14d79f]
#16 /usr/lib/libQtGui.so.4 [0x7f77fb14ce85]
#17 /lib/libc.so.6(exit+0x9d) [0x7f7809e8966d]
#18 /usr/lib/libgdk-x11-2.0.so.0 [0x7f7804b15c81]
#19 /usr/lib/libX11.so.6(_XError+0xf4) [0x7f78057bd784]
```

Didn't look to different to me...

---

### Post by cpradio on 2009-01-04
Okay, my bad on the previous post.  I ran firefox -sync instead of firefox --sync.  After running firefox --sync, everything seems to be operating fine.  I rand firefox --sync, typed in cpradio.org, got a "Page load error", closed Firefox.  Ran firefox without --sync, went to cpradio.org, got a "Page load error".

Firefox has since been running without any issues for 10 minutes now (best 10 minutes I have had all day since I can actually accomplish some surfing).

If the information leads to anything, cool; otherwise, I seem to be doing okay at the moment.

---

