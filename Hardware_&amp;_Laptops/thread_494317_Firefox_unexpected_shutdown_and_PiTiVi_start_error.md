---
title: "Firefox unexpected shutdown and PiTiVi start error"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by aresgoddess on 2007-07-06
Recently, Firefox has been shutting down on me without any warning. This started about a week ago. When I ran it through the terminal I got this: ```
** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

GCJ PLUGIN: thread 0x8121d10: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x8121d10: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x8121d10: NP_GetValue
GCJ PLUGIN: thread 0x8121d10: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x8121d10: NP_GetValue return
GCJ PLUGIN: thread 0x8121d10: NP_GetValue
GCJ PLUGIN: thread 0x8121d10: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x8121d10: NP_GetValue return
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadShmSeg (invalid shared segment parameter)'.
  (Details: serial 30 error_code 165 request_code 143 minor_code 2)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

Not sure what to do about it. I've been reading other posts, but I can't seem to find the same error. Also, I've never been able to start the program PiTiVi. I also ran that through the terminal, and I got this: ```
The program 'pitivi' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 46 error_code 3 request_code 3 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Does anyone know what that means? both messages say to run the --sync command line, but I don't know what that is exactly.

---

