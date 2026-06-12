---
title: "nVIDIA overclock, Window Closes upon agreement."
date: 2010-11-03
forum: Hardware
---

### Post by zer010 on 2010-11-03
Ok, I have a nVIDIA GeForce FX 5200. I edited xorg.conf to enable Coolbits and that seems to have worked fine. I can open nvidia-settings and I can choose to enable overclocking. When I check the box to enable OC, a warning and an agreement pops up. I'm used to this from Windows so no problem there. However when I click "Yes" to the agreement, both the agreement and the settings windows close with no further action.  So I used the terminal to invoke nvidia-settings. I checked the box, clicked "Yes" and they closed again, but this time I got this feedback from the terminal: 
```
The program 'nvidia-settings' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 232 error_code 2 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```
Any ideas on what is happening and what I can do?

---

### Post by zer010 on 2010-11-05
Anyone else have this problem?

---

