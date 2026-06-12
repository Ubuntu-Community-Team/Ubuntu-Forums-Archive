---
title: "Problem compiling Xe: &quot;cannot find -lasound&quot;"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by Doval on 2009-06-23
I'm trying to install [Xe](http://www.xe-emulator.com/), a multi system emulator, on Ubuntu 8.10 (32 bit.) I've unpacked the tar file into its own directory and navigated to that directory on the command line. However, when I use the "make" command, I get this error:
```
/usr/bin/ld: cannot find -lasound
collect2: ld returned 1 exit status
make: *** [xe] Error 1
```

I did a bit of googling around, and read that -lasound refers to the asound library. I searched for "libasound" on Synaptic, and it shows that I already have the libasound2 package (ALSA Library) installed. Is there some other package I'm missing? Is this error caused by something else entirely?

Thanks in advance.

---

### Post by Doval on 2009-06-24
Bump

---

### Post by Doval on 2009-06-24
Hope you don't mind, but my thread's fallen from page 1 to 5 overnight and still no answer, so...

Bumpity bump.

---

### Post by decoherence on 2009-06-24
> **Doval said:**
> Hope you don't mind, but my thread's fallen from page 1 to 5 overnight and still no answer, so...

Bumpity bump.

No worries!

For compiling things, you need the development headers. Install the package libasound2-dev and try it again. Repeat for any other dependencies it complains about.

---

### Post by Doval on 2009-06-25
Thanks a lot! That got me past that problem. However, now when I try to use "make install", it spits out this error:```
[: 37: ==: unexpected operator
Must be logged on as root.
```It spits that out every time, regardless of whether I sudo the "make install" command, and even if I log in as root via "sudo su". The terminal shows root@Blackbird, and the $ changed to #, and the "whoami" command returns root, yet it still throws that error...any ideas?

EDIT: Disregard I found the solution in this thread: [http://ubuntuforums.org/showthread.php?t=631680](http://ubuntuforums.org/showthread.php?t=631680) Changing the "#!/bin/sh" to "#/bin/bash" didn't work, but running the installer with "bash ./install.sh" did work.

Once again, thanks for the help.

---

