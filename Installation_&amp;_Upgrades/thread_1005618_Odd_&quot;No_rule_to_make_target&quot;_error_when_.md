---
title: "Odd &quot;No rule to make target&quot; error when compiling new 2.6.24 kernel"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by Nick- on 2008-12-08
Hello all. I'm still pretty new to the Ubuntu game, and currently have a machine running Ubuntu 8.04 with the 2.6.24 Server kernel. I'd like to get this guy running as clean and lean as possible, and still have everything enabled that I need.

Not being very familiar with Ubuntu or compiling kernels at all, I explicitly followed the great Kernel guide I found here ([http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)), and everything went perfectly until I get to the spot where I actually compilied the kernel. The command I enter, per the guide is: "make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers" .  I get a few informational messages, but then the whole thing seems to error out, throwing up a few of those lovely "No rule to make target" messages. 

If it helps, the complete output of the command I entered is below. I searched these forums and Google for quite a bit, so I hope this isn't something really obvious and simple that I missed! ;)

```

Warning: The file include/linux/version.h exists
The contained UTS_VERSION string:
                        ""
does not match expectations:
                        "2.6.24.3-custom"
I'll try and recover
exec debian/rules  DEBIAN_REVISION=2.6.24.3-custom-10.00.Custom  APPEND_TO_VERSION=-custom  INITRD=YES  kernel_image kernel_headers 
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 3: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator

====== making target CONFIG-common [new prereqs: testdir]======

====== making target CONFIG-common [new prereqs: stamp-conf]======
This is kernel package version 11.001.
====== making stamp-arch-conf because of  ======

====== making target CONFIG-arch [new prereqs: stamp-arch-conf]======
====== making target conf.vars [new prereqs: Makefile .config]======

Makefile:526: /usr/src/linux-headers-2.6.24-16-server/arch/xen/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.24-16-server/arch/xen/Makefile'.  Stop.
make: *** [conf.vars] Error 2

```


Thank you for any input you might have!



      - Nick

---

### Post by interim descriptor on 2008-12-22
I'm getting the same error, and I don't have a clue what's up.

Currently researching, will post again if I find a solution.

---

