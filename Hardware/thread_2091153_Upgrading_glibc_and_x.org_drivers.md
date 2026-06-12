---
title: "Upgrading glibc and x.org drivers?"
date: 2012-12-04
forum: Hardware
---

### Post by ivotkl on 2012-12-04
Ok. Main reason of this post is to upgrade glibc, but only because I need it to update x.org video drivers on both a desktop (Running Linux Mint Julia, 64 bits) and a laptop (Running ubuntu 10.04, 32 bits).-

I've searched glibc update on forums and there was nothing found. I'm currently interested in desktop, which is 64 bits. Regarding the laptop, I'm more concerned about [temperature issues](http://ubuntuforums.org/showthread.php?t=2090029) and [modifying fan speed](http://ubuntuforums.org/showthread.php?t=1999913).

**_Desktop specs:**_

OS:
```
Linux ivan-lnv 2.6.35-32-generic #67-Ubuntu SMP Mon Mar 5 19:39:49 UTC 2012 x86_64 GNU/Linux
```

glibc version:
```
GNU C Library (Ubuntu EGLIBC 2.12.1-0ubuntu10.4) stable release version 2.12.1, by Roland McGrath et al.
Copyright (C) 2010 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.
Compiled by GNU CC version 4.4.5.
Compiled on a Linux 2.6.35 system on 2012-03-06.
Available extensions:
	crypt add-on version 2.1 by Michael Glad and others
	GNU Libidn by Simon Josefsson
	Native POSIX Threads Library by Ulrich Drepper et al
	BIND-8.2.3-T5B
libc ABIs: UNIQUE IFUNC
For bug reporting instructions, please see:
<http://www.debian.org/Bugs/>
```

Onboard Graphic card:
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
```

OpenGL drivers installed:
```
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RS690 791E) 20090101  NO-TCL DRI2
OpenGL version string: 1.5 Mesa 7.9-devel
OpenGL extensions:

```

---

