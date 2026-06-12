---
title: "GDK Error"
date: 2008-11-02
forum: General Help
---

### Post by Twexcom on 2008-11-02
I just installed a program using make install and this is the error I get when I try to run it: 

nicholas@nicholas-desktop:~/Desktop/zinf2$ zinf --sync

(<unknown>:32614): Gdk-WARNING **: Attempt to draw a drawable with depth 16 to a drawable with depth 32

(<unknown>:32614): Gdk-WARNING **: Attempt to draw a drawable with depth 16 to a drawable with depth 32

(<unknown>:32614): Gdk-WARNING **: Attempt to draw a drawable with depth 16 to a drawable with depth 32

(<unknown>:32614): Gdk-CRITICAL **: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
The program '<unknown>' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 2640 error_code 8 request_code 62 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Help?

---

### Post by Twexcom on 2008-11-04
When I type export XLIB_SKIP_ARGB_VISUALS=1 in the terminal just before running it, it works. Why?

---

