---
title: "Miro shuts down when trying to play a file"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by pedrotuga on 2009-05-12
After the upgrade to jaunty, miro shuts down each time I try to play a file.

I google a bit and a couple of people apparently fixed the problem by removing some old repository. I believe that is not my case since I don't have any third party repository besides skype.

Here's my sources.list if necessary:

[http://pastebin.ca/raw/1420767](http://pastebin.ca/raw/1420767)

Here's the error message I get when I run miro from the console.

```
The program 'miro.real' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 134 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```


Any tips?


**EDIT:**
Ok, turns out that is not only miro. I've tryed to open a file with VLC and got this error message:

```
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82

```

---

### Post by Jboxer on 2009-05-13
I have the exact same problem any workaround would be great

```
The program 'miro.real' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 127 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

EDIT:I forgot that i had an intel integrated graphics card i am doing the steps provided on the sticky [HOWTO: Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?t=1130582") maybe that will help you

---

### Post by pedrotuga on 2009-05-16
I may give that a try.
I mean, I have no idea what kind of graphics card this laptop has inside. How do I check that?

---

### Post by paulderol on 2009-07-28
type 

sudo lshw

into the terminal, and the graphics card should be listed. post that listing here, and it can be faced full on.

---

