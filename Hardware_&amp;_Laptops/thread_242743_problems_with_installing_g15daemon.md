---
title: "problems with installing g15daemon"
date: 2006-08-24
forum: Hardware &amp; Laptops
---

### Post by phroztbyt3 on 2006-08-24
So i downloaded g15daemon tarbal  and i followed the instructions to the teet.  I configured it, "make" it, "make install" it.. even "make check" it... then when i try to run it by typing "sudo g15daemon"

it comes up with this

[g15daemon: error while loading shared libraries: libg15.so.1: cannot open shared object file: No such file or directory]

I looked all over for the libg15.so.1  to no avail.. anyone know what i'm doing wrong.. greatly appreciated.

Thanks,

-Phrozt

---

### Post by phroztbyt3 on 2006-08-24
bump

---

### Post by phroztbyt3 on 2006-08-24
bump... sum1 answer me

---

### Post by AriusBlack on 2006-08-31
I too had this error and I found two work arounds:

**1.** Copy libg15.so.1 from /usr/local/lib to /lib

Or..

**2.** Add the following line to the /etc/ld.so.conf file
```
/usr/local/lib
```
Then run ldconfig

The second method will allow 3rd party libraries installed in /usr/local/lib to be found by linux. Both methods must be done as root (sudo).

Just as a further note I encountered a 2nd error after this one 

"Something went wrong. Couldnt get return value from daemon process"

I was using
```
sudo g15daemon
```
but it refused to work. Only after I ran it in a root terminal did I get anywhere (I have no idea what went wrong).

Hope this helps.

---

### Post by Elpram on 2006-09-14
I've tried both of your workarounds to no avail....

---

### Post by Elpram on 2006-09-14
Sorry about that, I made a simple typo, however now I'm getting the "Something went wrong. Couldnt get return value from daemon process" error as well...

---

### Post by Elpram on 2006-09-18
well modprobe uinput fixed it

Now I have no idea how to edit whats on the display.

---

