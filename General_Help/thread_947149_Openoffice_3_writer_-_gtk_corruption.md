---
title: "Openoffice 3 writer - gtk corruption"
date: 2008-10-14
forum: General Help
---

### Post by jimmy the saint on 2008-10-14
I am running Hardy Heron 64bit and I just installed OOo3.  It seems nice, but writer corrupts the window borders.  I am running the stock human theme, and have tried it with a few others.  What happens is that if the Writer window loses focus then regains it, it turns pink or clear or just gets all colorful.  When the next window gains focus, it may or may not inherit this behavior.  This only happens half of the time.  Its hard to pin down.  Anyone else having this problem?  It only seems to affect Writer, not the others.

JTS

---

### Post by jimmy the saint on 2008-10-14
It is something to do with compiz.

---

### Post by JohnyN on 2008-10-18
Hello, I have the same problem on my machine.
[[img]http://www.divshare.com/img/thumb/5615115-104.png[/img]](http://www.divshare.com/download/5615115-104)
Ubuntu 8.04.1
I've installed Ubuntu from downloaded tar.gz archive at [http://www.openoffice.org/](http://www.openoffice.org/). Everything seems to be good, but GTK theme isn't applied. I've running Ubuntu 8.04.1 with standard Human Ubuntu theme and Compiz turned off.
Can anyone help, please?
Thanks

---

### Post by phoenix_snake on 2008-10-18
it has something to do with compiz and the nvidia driver if you move the cursor over the close and maximize buttons or something, you will notice if the window is inactive it doesn't happen and you know that blinking cursor for typing texts, if that isn't present it doesn't happen then either.

---

### Post by jimmy the saint on 2008-11-12
it seems odd that it only happens with one program.  I seem to remember a similar issue in fiesty with OO.  removing the oo gtk package (I forget the name) solved it then.  Too bad it doesn't work this time.

---

