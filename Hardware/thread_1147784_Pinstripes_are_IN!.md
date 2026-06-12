---
title: "Pinstripes are IN!"
date: 2009-05-03
forum: Hardware
---

### Post by jamesdcarroll on 2009-05-03
At least they are according to my system because now, for no reason that I can tell, my monitor is sporting thin pinstripes across it in kind of a jagged pattern. Even the boot up screen that normally displays a long list of errors from a failing hard drive in black and white text is being affected.  

Am I correct in my thinking that it's probably that its somewhat 'low level' (ie MOBO or vidcard) and not something maybe with the drivers? Card is an ATI Radeon 9700. 

One thing that I did find interesting is that when I tried to start f-spot it throws this:

```
(f-spot:22990): Gtk-CRITICAL **: gtk_window_resize: assertion `width > 0' failed
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 335 error_code 1 request_code 143 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

and then dies.  I don't know really what that means, though again, I would suspect that if there is something bad going on at a lower level it would affect system further up the food chain.

Thanks!!

---

