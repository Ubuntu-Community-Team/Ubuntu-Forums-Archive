---
title: "How to disable automatic login on tty1 / tty6?"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by cleartistico on 2009-10-15
Hello,

i'm trying to disable the autologin on the ttys in ubuntu Hardy Heron on a Persistent Live USB installation.
For this reason i edited the /etc/event.d/ttyX files. I modified the line:

exec /bin/login -f ubuntu </dev/tty1> /dev/tty1 2>&1
to: 
exec /bin/login </dev/tty1> /dev/tty1 2>&1

but surprisingly after reboot the file gets back to its initial state: 

exec /bin/login -f ubuntu ...

(The file doesn't get overwritten, because if i put some comments they
are still there after reboot. ) Does anyone know how to disable this?
I tried to comment out the whole exec line, but then I don't get a login prompt
at all.  I'd also appreciate some other options for disabling the autologin!

Thanks for your response!

---

