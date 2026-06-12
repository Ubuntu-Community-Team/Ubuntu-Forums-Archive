---
title: "See what ttyUSB devices are in use"
date: 2013-11-10
forum: Hardware
---

### Post by ajnozari on 2013-11-10
So I'm not sure if this has been asked or is even possible,

But is there a way to see what ttyUSB devices are being used by a program?

I'm working with usb miners (that use the /dev/ttyUSB*) but I can't figure out how to tell which ones are in use other than keep track manually.

Thanks for any help in advanced.

((As a note, they are on a cli))

---

### Post by sudodus on 2013-11-11
I'm not sure what you want. Please describe you problem or task, and it will be easier to help :-)

If you run a graphical desktop environment, you are usually using tty7. Terminal windows will be named pts/0, pts/1, etc. If you run a text screen, it is probably tty1, unless you have selected another one with a hotkey combination ***ctrl + alt + F2 ***...*** ctrl + alt + F6***.

Run ```
 who -a
``` for more details.

---

