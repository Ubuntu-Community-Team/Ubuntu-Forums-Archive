---
title: "Canon Pixma MP220 - sane fail error"
date: 2009-10-21
forum: Hardware
---

### Post by RebateFX on 2009-10-21
Hi

Using Ubuntu 9.10 (beta) and a Canon Pixma MP220 printer/scanner.

The printing works fine out of the box. Nothing to complain about there.

The scanning however.... ;)

Xsane was saying "operation was cancelled" when trying any scan or preview.

So I decided to look at the command line for any further detail...

```
jafar@callisto:~$ scanimage -L
device `pixma:04A91722_5006B8' is a CANON Canon PIXMA MP220 multi-function peripheral
jafar@callisto:~$ scanimage -T
scanimage: scanning image of size 640x877 pixels at 24 bits/pixel
scanimage: acquiring RGB frame, 8 bits/sample
scanimage: reading one scanline, 1920 bytes...	FAIL Error: Operation was cancelled
jafar@callisto:~$
```

Still the same. What does it mean? Is there any way to get any more detail about the error? Like WHY the operation was cancelled?

Scanimage -v shows....

```
jafar@callisto:~$ scanimage -v
scanimage: scanning image of size 640x877 pixels at 24 bits/pixel
scanimage: acquiring RGB frame
P6
# SANE data follows
640 877
255
scanimage: min/max graylevel value = 255/0
scanimage: sane_read: Operation was cancelled
```

Is there anything else I can post to the thread to help get me scanning with this?

---

### Post by Dark_Stang on 2009-10-21
Weeelll, acording to sane everything should be okay.
[http://www.sane-project.org/man/sane-pixma.5.html](http://www.sane-project.org/man/sane-pixma.5.html)

Make sure you have libsane-pixma installed.

Edit: So do we know that the scanner works okay? Has it worked on another machine?

---

