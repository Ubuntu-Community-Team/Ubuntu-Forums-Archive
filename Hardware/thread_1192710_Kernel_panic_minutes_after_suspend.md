---
title: "Kernel panic minutes after suspend"
date: 2009-06-20
forum: Hardware
---

### Post by jodiemaceachern on 2009-06-20
I was wondering if someone might have some input on this:

I tested this with The latest 64 bit ubuntu Jaunty, using a live USB.
I performed all the updates through the update app.

After resuming from a suspend, I will experience a kernel panic.
This can be reproduced every time by doing the following steps:
1. Suspend to Ram.
2. Press a key to wake it up.
3. On a console type "sudo apt-get install mc".
4. The package will download correctly, but as soon as it attempts to install it will cause a kernel panic. (CAPS LOCK blinking)

These steps are just a way to consistently reproduce the issue on my laptop, it will usually happen after surfing around on the Internet.

I reported the bug with the full information here, including a photo of the kernel panic:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/375257](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/375257)

I would even like to know a good work around so I can use it.

Thanks in advanced,
Jodie

---

### Post by jodiemaceachern on 2009-06-20
This is the information about my setup, it is on a TOSHIBA Satellite L300D.

Architecture: amd64
DistroRelease: Ubuntu 9.04
MachineType: TOSHIBA Satellite L300D
Package: linux-image-2.6.28-11-generic 2.6.28-11.42
ProcCmdLine: root=UUID=deda9e62-9a3a-40b3-8b8f-12647c36670c ro quiet splash
ProcEnviron:
 LANGUAGE=
 LANG=en_CA.UTF-8
 SHELL=/bin/bash
ProcVersionSignature: Ubuntu 2.6.28-11.42-generic
SourcePackage: linux

---

### Post by jodiemaceachern on 2009-06-23
Linux laptop 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:55:09 UTC 2009 x86_64 GNU/Linux

This update seems to have solved the issue.. I updated yesterday

---

