---
title: "DeSmuMe Won't Start"
date: 2008-11-11
forum: General Help
---

### Post by Airfoot on 2008-11-11
DeSmuMe won't start, when I try to run it in terminal i get this error:  dan@dan-laptop:~$ desmume
Nbr of joysticks: 0

The program 'desmume' received an X Window System error.
This probably reflects a bug in the program.
The error was 'GLXBadContext'.
  (Details: serial 305 error_code 154 request_code 143 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
dan@dan-laptop:~$

---

### Post by timbalisto on 2008-11-12
I have the same problem. I run Hardy Heron, fully updated. here is what I get from the terminal ```
tim@tim-desktop:~$ desmume
Nbr of joysticks: 1

Joystick 0 HID 6666:0667
Axes: 4
Buttons: 16
Trackballs: 0
Hats: 0

The program 'desmume' received an X Window System error.
This probably reflects a bug in the program.
The error was 'GLXBadContext'.
  (Details: serial 305 error_code 154 request_code 143 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```
any help would be appreciated.

---

### Post by timbalisto on 2008-11-15
Really? No one else has this problem besides us? What a bummer.:(

---

### Post by Airfoot on 2008-11-15
No kidding!

---

### Post by timbalisto on 2008-11-24
I found a solution! Try starting it with this
```
desmume --disable-3d

```
It works with about half the roms I have, but it's better than nothing.
I found the solution in another thread 
[http://ge.ubuntuforums.com/showthread.php?p=5683936](http://ge.ubuntuforums.com/showthread.php?p=5683936)

---

### Post by Airfoot on 2008-11-24
Thanks

---

